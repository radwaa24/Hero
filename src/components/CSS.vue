<template>
    <div>


        <label for="message" class="block text-dark/40 dark:text-white/40 mb-1">Message</label>
        <textarea id="message"
            class="form-input py-2.5 bg-white dark:bg-white/5 px-4 w-full text-dark dark:text-white border border-dark/10 dark:border-white/10 rounded-md placeholder:opacity-50 focus:border-dark dark:focus:border-white/40 focus:ring-0 focus:shadow-none outline-none transition-colors"></textarea>

        <div class="form-checkbox">
            <input id="agree" type="checkbox" class="form-checkbox-input m-6">
            <label for="agree" class="form-checkbox-label">I agree to the terms and conditions</label>
        </div>

        <div class="form-radio">
            <input id="option1" type="radio" name="options" class="form-radio-input">
            <label for="option1" class="form-radio-label">Option 1</label>
            <input id="option2" type="radio" name="options" class="form-radio-input">
            <label for="option2" class="form-radio-label">Option 2</label>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MyForm',
}
</script>

<style scoped type="text/sass">
.form-control {
    label {
        @apply block text-dark/40 dark:text-white/40 mb-1;
    }

    .form-input,
    .form-select {
        @apply py-2.5 bg-white dark:bg-white/5 px-4 w-full text-dark dark:text-white border border-dark/10 dark:border-white/10 rounded-md placeholder:opacity-50 focus:border-dark dark:focus:border-white/40 focus:ring-0 focus:shadow-none outline-none transition-colors;

        &.has-error {
            @apply border-danger;
        }
    }

    select {
        background-position: right 0.5rem center;
    }

    .form-input {
        @apply py-3.5;
    }
}

.input-group {
    .form-control {
        @apply relative bg-white dark:bg-white/5 py-4 px-5 rounded-lg border border-dark/10;

        &.has-error {
            @apply border-danger;
        }

        label {
            @apply text-xs;
        }

        .form-input,
        .form-select {
            @apply w-full border-0 bg-transparent p-0 dark:text-white outline-none placeholder:opacity-50;
        }

        select {
            background-position: right 0 center;
        }
    }
}

.error {
    @apply text-danger text-sm first-letter:capitalize block;
}

/* Handle auto complete */
.dark {
    input:-webkit-autofill {
        -webkit-text-fill-color: #ffffff;
    }
}

input:-webkit-autofill {
    -webkit-background-clip: text;
    -webkit-text-fill-color: rgb(var(--dark));
    transition: background-color 5000s ease-in-out 0s;
}

/* Checkbox and Radio styling */
[type="checkbox"],
[type="radio"] {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    padding: 0;
    -webkit-print-color-adjust: exact;
    print-color-adjust: exact;
    display: inline-block;
    vertical-align: middle;
    background-origin: border-box;
    -webkit-user-select: none;
    -moz-user-select: none;
    user-select: none;
    flex-shrink: 0;
    height: 1rem;
    width: 1rem;
    --tw-shadow: 0 0 #0000;
}

/* Checkbox styles */
[type="checkbox"] {
    border-radius: 6px;
    background: var(--White, #FFF);
}

[type="checkbox"]:focus,
[type="radio"]:focus {
    border-radius: 6px;
    border: var(--0, 1px) solid var(--Primary-primary-200, #EAAAB7);
    background: var(--White, #FFF);
    box-shadow: 0px 0px 0px 4px #FAEDEF;
}

[type="checkbox"]:hover,
[type="radio"]:hover {
    border-radius: 6px;
    border: var(--0, 1px) solid var(--Primary-primary-600, #BE405A);
    background: var(--Primary-primary-50, #FAEDEF);
}

[type="checkbox"]:checked,
[type="radio"]:checked {
    background-size: 100% 100%;
    background-position: 50%;
    background-repeat: no-repeat;
    border-radius: 6px;
    border: 1px solid var(--Primary-primary-600, #BE405A);
    background: var(--Primary-primary-50, #FAEDEF);
}

[type="checkbox"]:checked {
    background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%23fff' viewBox='0 0 16 16'%3E%3Cpath d='M12.207 4.793a1 1 0 0 1 0 1.414l-5 5a1 1 0 0 1-1.414 0l-2-2a1 1 0 0 1 1.414-1.414L6.5 9.086l4.293-4.293a1 1 0 0 1 1.414 0z'/%3E%3C/svg%3E");
}

[type="radio"]:checked {
    background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%23fff' viewBox='0 0 16 16'%3E%3Cpath d='M12.207 4.793a1 1 0 0 1 0 1.414l-5 5a1 1 0 0 1-1.414 0l-2-2a1 1 0 0 1 1.414-1.414L6.5 9.086l4.293-4.293a1 1 0 0 1 1.414 0z'/%3E%3C/svg%3E");
}

[type="checkbox"]:indeterminate {
    background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 16 16'%3E%3Cpath stroke='%23fff' stroke-linecap='round' stroke-linejoin='round' stroke-width='2' d='M4 8h8'/%3E%3C/svg%3E");
    background-size: 100% 100%;
    background-position: 50%;
    background-repeat: no-repeat;
    border-radius: 6px;
    border: var(--0, 1px) solid var(--Primary-primary-600, #BE405A);
    background: var(--Primary-primary-50, #FAEDEF);
}

[type="checkbox"]:indeterminate:focus {
    border-radius: 6px;
    border: var(--0, 1px) solid var(--Primary-primary-600, #BE405A);
    background: var(--Primary-primary-50, #FAEDEF);
    box-shadow: 0px 0px 0px 4px #FAEDEF;
}

[type="checkbox"]:indeterminate:hover {
    border-radius: 6px;
    border: var(--0, 1px) solid var(--Primary-primary-600, #BE405A);
    background: var(--Primary-primary-50, #FAEDEF);
}

/* Form checkbox and radio */
.form-checkbox,
.form-radio {
    margin-right: 0.375rem;
    height: 1.25rem;
    width: 1.25rem;
    cursor: pointer;
    border-radius: 0.25rem;
    border-width: 1px;

    &.is-white {
        border: var(--0, 1px) solid var(--Neutral-neutral-400, #A2A19E);
        background-color: white;
    }

    --tw-text-opacity: 1;
    --tw-shadow: 0 0 #0000 !important;
    box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000),
    var(--tw-ring-shadow, 0 0 #0000),
    var(--tw-shadow) !important;
    outline: 2px solid #0000 !important;
    outline-offset: 2px !important;
    --tw-ring-offset-shadow: var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color) !important;
    --tw-ring-shadow: var(--tw-ring-inset) 0 0 0 calc(var(--tw-ring-offset-width)) var(--tw-ring-color) !important;
    box-shadow: var(--tw-ring-offset-shadow),
    var(--tw-ring-shadow),
    var(--tw-shadow, 0 0 #0000) !important;
    --tw-ring-offset-width: 0px !important;
}

[type="radio"] {
    border-radius: 100%;
}

.form-checkbox:checked,
.form-radio:checked {
    background-size: 90% 90%;
}

.form-checkbox:focus,
.form-radio:focus {
    border-color: #1c1c1c1a;

    &.is-white {
        border-color: white;
    }
}

.form-checkbox:disabled,
.form-radio:disabled {
    cursor: not-allowed;
    background-color: #1c1c1c66;
}

/* Dark mode checkbox and radio */
.dark .form-checkbox,
.dark .form-checkbox:focus,
.dark .form-radio,
.dark .form-radio:focus {
    border-color: #ffffff1a;
}

.dark .form-checkbox:disabled,
.dark .form-radio:disabled {
    background-color: #fff6;
}

/* Form checkbox outline styles */
.form-checkbox.outline-primary:checked {
    --tw-border-opacity: 1;
    border-color: rgb(var(--primary) / var(--tw-border-opacity));
    background-color: initial;
    background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%23d14664' viewBox='0 0 16 16'%3E%3Cpath d='M12.207 4.793a1 1 0 0 1 0 1.414l-5 5a1 1 0 0 1-1.414 0l-2-2a1 1 0 0 1 1.414-1.414L6.5 9.086l4.293-4.293a1 1 0 0 1 1.414 0z'/%3E%3C/svg%3E");
}

.form-checkbox.outline-secondary:checked {
    --tw-border-opacity: 1;
    border-color: rgb(var(--muted) / var(--tw-border-opacity));
    background-color: initial;
    background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%2393a3b0' viewBox='0 0 16 16'%3E%3Cpath d='M12.207 4.793a1 1 0 0 1 0 1.414l-5 5a1 1 0 0 1-1.414 0l-2-2a1 1 0 0 1 1.414-1.414L6.5 9.086l4.293-4.293a1 1 0 0 1 1.414 0z'/%3E%3C/svg%3E");
}

.form-checkbox.outline-success:checked {
    --tw-border-opacity: 1;
    border-color: rgb(var(--success) / var(--tw-border-opacity));
    background-color: initial;
    background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%2300c853' viewBox='0 0 16 16'%3E%3Cpath d='M12.207 4.793a1 1 0 0 1 0 1.414l-5 5a1 1 0 0 1-1.414 0l-2-2a1 1 0 0 1 1.414-1.414L6.5 9.086l4.293-4.293a1 1 0 0 1 1.414 0z'/%3E%3C/svg%3E");
}

.form-checkbox.outline-danger:checked {
    --tw-border-opacity: 1;
    border-color: rgb(var(--danger) / var(--tw-border-opacity));
    background-color: initial;
    background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%23de0000' viewBox='0 0 16 16'%3E%3Cpath d='M12.207 4.793a1 1 0 0 1 0 1.414l-5 5a1 1 0 0 1-1.414 0l-2-2a1 1 0 0 1 1.414-1.414L6.5 9.086l4.293-4.293a1 1 0 0 1 1.414 0z'/%3E%3C/svg%3E");
}

.form-checkbox.outline-warning:checked {
    --tw-border-opacity: 1;
    border-color: rgb(var(--warning) / var(--tw-border-opacity));
    background-color: initial;
    background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%23ffcc00' viewBox='0 0 16 16'%3E%3Cpath d='M12.207 4.793a1 1 0 0 1 0 1.414l-5 5a1 1 0 0 1-1.414 0l-2-2a1 1 0 0 1 1.414-1.414L6.5 9.086l4.293-4.293a1 1 0 0 1 1.414 0z'/%3E%3C/svg%3E");
}

.form-checkbox.outline-info:checked {
    --tw-border-opacity: 1;
    border-color: rgb(var(--info) / var(--tw-border-opacity));
    background-color: initial;
    background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%23006fde' viewBox='0 0 16 16'%3E%3Cpath d='M12.207 4.793a1 1 0 0 1 0 1.414l-5 5a1 1 0 0 1-1.414 0l-2-2a1 1 0 0 1 1.414-1.414L6.5 9.086l4.293-4.293a1 1 0 0 1 1.414 0z'/%3E%3C/svg%3E");
}

.form-checkbox.outline-dark:checked {
    --tw-border-opacity: 1;
    border-color: rgb(var(--dark) / var(--tw-border-opacity));
    background-color: initial;
    background-image: url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='%231c1c1c' viewBox='0 0 16 16'%3E%3Cpath d='M12.207 4.793a1 1 0 0 1 0 1.414l-5 5a1 1 0 0 1-1.414 0l-2-2a1 1 0 0 1 1.414-1.414L6.5 9.086l4.293-4.293a1 1 0 0 1 1.414 0z'/%3E%3C/svg%3E");
}

.form-checkbox.is-white {
    &[class*="outline-"] {
        &:checked {
            @apply bg-white border-white;
        }
    }
}

/* Form radio outline styles */
.form-radio {
    &[class*="outline-"] {
        --tw-border-opacity: 1;
        background: none !important;
    }

    &.outline {
        &-primary:checked {
            @apply border-primary;
        }

        &-secondary:checked {
            @apply border-muted;
        }

        &-success:checked {
            @apply border-success;
        }

        &-danger:checked {
            @apply border-danger;
        }

        &-warning:checked {
            @apply border-warning;
        }

        &-info:checked {
            @apply border-info;
        }

        &-dark:checked {
            @apply border-dark;
        }
    }
}

/* Select dropdown styles */
select {
    appearance: none;
    background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 20 20'%3e%3cpath stroke='%236b7280' stroke-linecap='round' stroke-linejoin='round' stroke-width='1.5' d='M6 8l4 4 4-4'/%3e%3c/svg%3e");
    background-position: right 0 center;
    background-repeat: no-repeat;
    background-size: 1.5em 1.5em;
    padding-right: 2.5rem;
    -webkit-print-color-adjust: exact;
    print-color-adjust: exact;
}

/* Toggle button */
.toggle-button {
    input {
        &:checked {
            ~.band {
                --tw-bg-opacity: 1;
                @apply bg-primary;
            }

            ~.dot {
                --tw-translate-x: 100%;
                transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
                --tw-bg-opacity: 1;
                background-color: rgb(255 255 255 / var(--tw-bg-opacity));
            }
        }
    }
}

/* Outline toggle button styles */
.toggle-button.outline input:checked {
    ~.band {
        --tw-border-opacity: 1;
        @apply border-color: rgb(106 105 245 / var(--tw-border-opacity));
        background-color: initial;
    }

    ~.dot {
        --tw-translate-x: 100%;
        transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
        --tw-bg-opacity: 1;
        @apply bg-primary;
    }
}
</style>
