# Customize Default Form Validation
To Customize the default form validation, you can use the `onInvalid` and `onInput` event handlers to set custom validation messages and clear them respectively.

## Example
```tsx
'use client';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import React, { FC, useId } from 'react';

type FormFieldProps = React.HTMLAttributes<HTMLInputElement> & {
  label: string;
  error?: string;
};

const FormField: FC<FormFieldProps> = ({ label, error, ...props }) => {
  const id = useId();

  const onInvalid = (e: React.InvalidEvent<HTMLInputElement>) => {
    if (error) e.target.setCustomValidity(error);
  };

  const onInput = (e: React.FormEvent<HTMLInputElement>) => {
    e.currentTarget.setCustomValidity('');
  };

  return (
    <div className="flex w-full flex-col gap-1">
      <Label htmlFor={id} className="text-lg font-semibold">
        {label}
      </Label>
      <Input
        className="border-primary bg-transparent"
        onInvalid={onInvalid}
        onInput={onInput}
        id={id}
        {...props}
      />
    </div>
  );
};

export default FormField;
```
# Resources
- [`checkValidity()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLSelectElement/checkValidity): Returns true if an input element contains valid data.
- [`reportValidity()`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLSelectElement/reportValidity): Returns true if an input element contains valid data.
- [`ValidityState`](https://developer.mozilla.org/en-US/docs/Web/API/ValidityState): The ValidityState interface represents the validity states that an element can be in, with respect to constraint validation.