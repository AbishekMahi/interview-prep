# Form Builder Assignment - Bren

A dynamic, config-driven form builder built with Next.js (App Router), React Context, and TypeScript.

## Project Structure

```
├── app/
│   └── page.tsx
├── components/
│   ├── FormBuilder.tsx
│   ├── FormFiled.tsx
│   └── SubmittedData.tsx
├── context/
│   └── FormContext.tsx
└── types/
    └── form.ts
```

---

## `types/form.ts`

```ts
export type FormData = {
  name: string;
  email: string;
  dob: string;
  age: string;
  phone: string;
  gender: string;
  country: string;
  interest: string[];
  message: string;
  password: string;
  confirmPassword: string;
};

export type FormErrors = Partial<Record<keyof FormData, string>>;

export type FieldType = "string" | "number" | "email" | "url";

export type FieldConfig = {
  name: keyof FormData;
  label: string;
  type:
    | "text"
    | "number"
    | "tel"
    | "email"
    | "select"
    | "radio"
    | "textarea"
    | "date"
    | "checkbox"
    | "password";
  validationType: FieldType;
  required: boolean;
  readonly?: boolean;
  minLength?: number;
  maxLength?: number;
  min?: number;
  max?: number;
  options?: {
    label: string;
    value: string;
  }[];
};
```

---

## `context/FormContext.tsx`

```tsx
"use client";

import { createContext, useState, useContext } from "react";
import { FormData } from "@/types/form";

type FormContextType = {
  formData: FormData;
  setFormData: React.Dispatch<React.SetStateAction<FormData>>;
  resetForm: () => void;
};
// used when the form is first loaded or reset.
const defaultFormData: FormData = {
  name: "",
  email: "",
  dob: "",
  age: "",
  phone: "",
  gender: "",
  country: "",
  interest: [],
  message: "",
  password: "",
  confirmPassword: "",
};

// context can be undefined if the component is not inside FormProvider
const FormContext = createContext<FormContextType | undefined>(undefined);

export function FormProvider({ children }: { children: React.ReactNode }) {
  const [formData, setFormData] = useState<FormData>(defaultFormData);
  function resetForm() {
    setFormData(defaultFormData);
  }
  return (
    <FormContext.Provider value={{ formData, setFormData, resetForm }}>
      {children}
    </FormContext.Provider>
  );
}

// small helper soo that components dont need to call the useContext directly
export function useFormContext() {
  const context = useContext(FormContext);
  if (!context) {
    throw new Error("useFormContext must be used within a FormProvider");
  }
  return context;
}
```

---

## `components/FormFiled.tsx`

```tsx
"use client";
import { FormData } from "@/types/form";
import { useState } from "react";

type FormFieldProps = {
  name: keyof FormData;
  label: string;
  type:
    | "text"
    | "number"
    | "tel"
    | "email"
    | "select"
    | "radio"
    | "textarea"
    | "checkbox"
    | "date"
    | "password";
  value: string | string[];
  options?: {
    label: string;
    value: string;
  }[];
  error?: string;
  minLength?: number;
  maxLength?: number;
  min?: number;
  max?: number;
  onChange: (name: keyof FormData, value: string | string[]) => void;
};

export default function FormField({
  name,
  label,
  type,
  value,
  error,
  onChange,
  options = [],
  minLength,
  maxLength,
  min,
  max,
}: FormFieldProps) {
  const [showPassword, setShowPassword] = useState(false);

  return (
    <div className="space-y-1.5 mb-2">
      <label htmlFor={name} className="block text-sm font-medium text-gray-700">
        {label}
      </label>
      {type === "textarea" ? (
        <>
          <textarea
            id={name}
            name={name}
            value={value}
            minLength={minLength}
            maxLength={maxLength}
            className={`my-1 block w-full rounded-md p-2 border-2 border-gray-400 ${
              error ? "border-red-500" : "border-gray-800 "
            }`}
            onChange={(e) => onChange(name, e.target.value)}></textarea>
          <div className="mt-1 text-right text-xs text-gray-400">
            {value.length}/{maxLength}
          </div>
        </>
      ) : type === "select" ? (
        <select
          id={name}
          name={name}
          className={`my-1 block w-full rounded-md p-2 border-2 border-gray-400 ${
            error ? "border-red-500" : "border-gray-800 "
          }`}
          onChange={(e) => onChange(name, e.target.value)}>
          {options?.map((option) => (
            <option key={option.value} value={option.value}>
              {option.label}
            </option>
          ))}
        </select>
      ) : type === "radio" ? (
        <div className="gap-2 flex">
          {options?.map((option) => (
            <>
              <input
                type="radio"
                id={option.value}
                name={name}
                key={option.value}
                onChange={(e) => onChange(name, e.target.value)}
                value={option.value}
              />
              <label htmlFor={option.value}>{option.label}</label>
            </>
          ))}
        </div>
      ) : type === "checkbox" ? (
        <div className="gap-2 flex">
          {options?.map((option) => {
            const selected = Array.isArray(value) ? value : [];
            return (
              <>
                <input
                  type="checkbox"
                  id={option.value}
                  name={name}
                  checked={selected.includes(option.value)}
                  key={option.value}
                  onChange={(e) => {
                    const newValue = e.target.checked
                      ? selected.includes(option.value)
                        ? selected
                        : [...selected, option.value]
                      : selected.filter((item) => item !== option.value);
                    onChange(name, newValue);
                  }}
                  value={option.value}
                />
                <label htmlFor={option.value}>{option.label}</label>
              </>
            );
          })}
        </div>
      ) : (
        <div className="flex relative">
          <input
            id={name}
            name={name}
            type={type === "password" && showPassword ? "text" : type}
            value={value}
            minLength={minLength}
            maxLength={maxLength}
            min={min}
            max={max}
            onChange={(e) => onChange(name, e.target.value)}
            className={`my-1 block w-full rounded-md p-2 border-2 border-gray-400 ${
              error ? "border-red-500" : "border-gray-800 "
            }`}
          />
          {type === "password" && (
            <button
              className="absolute right-1 top-1/4 cursor-pointer"
              type="button"
              onClick={() => setShowPassword((prev) => !prev)}>
              {showPassword ? "Hide" : "Show"}
            </button>
          )}
        </div>
      )}
      {error && <p className="mt-1 mb-2 text-sm text-red-600">{error}</p>}
    </div>
  );
}
```

---

## `components/FormBuilder.tsx`

```tsx
// here is where we build the form builder component, which will allow users to create and customize form fields.
"use client";

import { useState } from "react";
import FormField from "./FormFiled";
import SubmittedData from "@/components/SubmittedData";
import { useFormContext } from "@/context/FormContext";
import { FormData, FormErrors, FieldConfig } from "@/types/form";

const fields: FieldConfig[] = [
  {
    name: "name",
    label: "Name",
    type: "text",
    validationType: "string",
    required: true,
    minLength: 2,
    maxLength: 50,
  },
  {
    name: "email",
    label: "Emaill",
    type: "email",
    validationType: "email",
    required: true,
    minLength: 5,
    maxLength: 100,
  },
  {
    name: "dob",
    label: "Date of Birth",
    type: "date",
    validationType: "string",
    required: true,
  },
  {
    name: "age",
    label: "Age",
    type: "number",
    validationType: "number",
    required: true,
    // minLength: 1,
    // maxLength: 3,
    min: 18,
    max: 120,
  },
  {
    name: "phone",
    label: "Phone Number",
    type: "tel",
    validationType: "string",
    required: true,
    minLength: 10,
    maxLength: 15,
  },
  {
    name: "gender",
    label: "Gender",
    type: "radio",
    options: [
      { label: "Male", value: "male" },
      {
        label: "Female",
        value: "female",
      },
    ],
    validationType: "string",
    required: true,
  },
  {
    name: "country",
    label: "Country",
    type: "select",
    options: [
      { label: "Select Country", value: "" },
      { label: "India", value: "India" },
      { label: "UK", value: "UK" },
      { label: "USA", value: "USA" },
    ],
    validationType: "string",
    required: true,
  },
  {
    name: "interest",
    label: "Interest",
    type: "checkbox",
    options: [
      { label: "Reading", value: "Reading" },
      { label: "Coding", value: "Coding" },
      { label: "Running", value: "Running" },
      { label: "Music", value: "Music" },
    ],
    validationType: "string",
    required: true,
  },
  {
    name: "message",
    label: "Message",
    type: "textarea",
    validationType: "string",
    required: true,
    minLength: 10,
    maxLength: 500,
  },
  {
    name: "password",
    label: "Password",
    type: "password",
    validationType: "string",
    required: true,
    minLength: 6,
    maxLength: 20,
  },
  {
    name: "confirmPassword",
    label: "Confirm Password",
    type: "password",
    validationType: "string",
    required: true,
    minLength: 6,
    maxLength: 20,
  },
];

export default function FormBuilder() {
  const { formData, setFormData, resetForm } = useFormContext();
  const [errors, setErrors] = useState<FormErrors>({});
  const [submittedData, setSubmittedData] = useState<FormData | null>(null);

  function handleChange(name: keyof FormData, value: string | string[]) {
    setFormData((prev) => ({
      ...prev,
      [name]: value,
    }));

    setErrors((prev) => ({
      ...prev,
      [name]: undefined,
    }));
  }

  // form validation function
  function validateField(
    value: string | string[],
    fieldConfig: FieldConfig,
  ): string | undefined {
    if (Array.isArray(value)) {
      if (fieldConfig.required && value.length === 0) {
        return `${fieldConfig.label} is required`;
      }
      return undefined;
    }

    const trimmedValue = value.trim();

    // check if the field is required and if the value is empty
    if (fieldConfig.required && !trimmedValue) {
      return `${fieldConfig.label} is required.`;
    }

    // for optional fields only validate if the field has a value
    if (!trimmedValue) {
      return undefined;
    }

    // for minimum length validation
    if (
      fieldConfig.minLength !== undefined &&
      trimmedValue.length < fieldConfig.minLength
    ) {
      return `${fieldConfig.label} must be at least ${fieldConfig.minLength} characters.`;
    }

    // for maximum length validation
    if (
      fieldConfig.maxLength !== undefined &&
      trimmedValue.length > fieldConfig.maxLength
    ) {
      return `${fieldConfig.label} must be at most ${fieldConfig.maxLength} characters.`;
    }

    // for number validation
    if (
      fieldConfig.validationType === "number" &&
      isNaN(Number(trimmedValue))
    ) {
      return `${fieldConfig.label} must be a valid number.`;
    }

    // form min age value validation
    if (fieldConfig.validationType === "number") {
      const numValue = Number(value);
      if (numValue && isNaN(Number(trimmedValue))) {
        return "age must be a number";
      }
      if (fieldConfig.min !== undefined && numValue < fieldConfig.min) {
        return `${fieldConfig.label} age must be at least ${fieldConfig.min}`;
      }
      if (fieldConfig.max !== undefined && numValue > fieldConfig.max) {
        return `${fieldConfig.label} age must be at most ${fieldConfig.max}`;
      }
    }

    // for email validation
    if (
      fieldConfig.validationType === "email" &&
      !/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i.test(trimmedValue)
    ) {
      return `${fieldConfig.label} must be a valid email address.`;
    }

    // // password match validation
    // if (
    //   "confirmPassword" in formData &&
    //   formData.confirmPassword !== undefined
    // ) {
    //   if (formData.password !== formData.confirmPassword) {
    //     return "Passwords do not match";
    //   }
    // }
    return undefined;
  }

  // handle form submission
  function handleSubmit(e: React.FormEvent<HTMLFormElement>) {
    e.preventDefault();

    // create errors object, start with no errors
    const newErrors: FormErrors = {};

    // validate every field
    fields.forEach((field) => {
      const error = validateField(formData[field.name], field);
      if (error) {
        newErrors[field.name] = error;
      }
    });
    // crorr field password validation
    if ("confirmPassword" in formData) {
      if (
        formData.password !== undefined &&
        formData.confirmPassword !== undefined &&
        formData.password !== formData.confirmPassword
      ) {
        newErrors.confirmPassword = "Passwords do not match";
      }
    }

    setErrors(newErrors);

    if (Object.keys(newErrors).length > 0) {
      // if there are error, we don't submit the form
      return;
    }

    // if noo errors, submit the form
    setSubmittedData({ ...formData });
  }

  // handle form reset
  function handleReset() {
    resetForm();
    setErrors({});
    // setSubmittedData(null);
  }
  return (
    <div className="mx-auto w-full p-6">
      <div className="grid gap-8 md:grid-cols-2">
        <form onSubmit={handleSubmit} onReset={handleReset}>
          {fields.map((field) => (
            <FormField
              key={field.name}
              name={field.name}
              label={field.label}
              type={field.type}
              options={field.options}
              value={formData[field.name]}
              onChange={handleChange}
              error={errors[field.name]}
              minLength={field.minLength}
              maxLength={field.maxLength}
              min={field.min}
              max={field.max}
            />
          ))}

          <div className="flex gap-3 mt-3">
            <button
              type="submit"
              className="rounded-md bg-black px-4 py-2 text-white hover:bg-gray-800 cursor-pointer">
              Submit
            </button>

            <button
              type="button"
              onClick={handleReset}
              className="rounded-md border px-4 py-2 hover:bg-gray-50 cursor-pointer">
              Reset
            </button>
          </div>
        </form>

        <SubmittedData data={submittedData} />
      </div>
    </div>
  );
}
```

---

## `components/SubmittedData.tsx`

```tsx
// to display the submitted data
import { FormData } from "@/types/form";

export default function SubmittedData({ data }: { data: FormData | null }) {
  if (!data) {
    return <p>No data submitted yet.</p>;
  }

  return (
    <div>
      <h2 className="text-xl font-bold mb-4">Submitted Data</h2>
      <ul>
        {Object.entries(data).map(([key, value]) => (
          <li key={key}>
            <strong className="font-semibold capitalize">{key}:</strong>
            {"  "}
            {Array.isArray(value) ? value.join(", ") : String(value)}
          </li>
        ))}
      </ul>
    </div>
  );
}
```

---

## `app/page.tsx`

```tsx
import FormBuilder from "@/components/FormBuilder";
import { FormProvider } from "@/context/FormContext";

export default function Home() {
  return (
    <FormProvider>
      <main className="flex min-h-screen flex-col items-center justify-between p-24">
        <h1 className="text-3xl font-bold mb-4">
          Form Builder Assignment - Bren
        </h1>
        <FormBuilder />
      </main>
    </FormProvider>
  );
}
```
