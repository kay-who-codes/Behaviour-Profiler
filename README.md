# How to Make Changes to Behaviour Checklist

This guide walks you through updating the **Body Language** section of a web application by removing one behaviour and adding two others.

- **Remove**: `Excessive Hand Gestures`
- **Add**: `Self-Hugging`, `Palm Exposure`

---

## Step 1: Update HTML

### 1.1 Remove “Excessive Hand Gestures”

In `index.html`:

1. Locate the **Body Language** section (starts around **line 494**).
2. Inside the `<div class="checkbox-group" style="margin-top: 20px;">` (around **line 528**), find and remove the following block:

```html
<div class="checkbox-item">
    <input type="checkbox" id="handGestures">
    <label for="handGestures">Excessive Hand Gestures</label>
</div>
```

### 1.2 Add “Self-Hugging” and “Palm Exposure”

In the same `<div class="checkbox-group" style="margin-top: 20px;">`, add the following:

```html
<div class="checkbox-item">
    <input type="checkbox" id="selfHugging">
    <label for="selfHugging">Self-Hugging</label>
</div>
<div class="checkbox-item">
    <input type="checkbox" id="palmExposure">
    <label for="palmExposure">Palm Exposure</label>
</div>
```

---

## Step 2: Update JavaScript

The JavaScript handles data collection, storage, and report generation.

### 2.1 Update `collectFormData`

- Found around **line 707** inside a `<script>` tag.
- Code block (already dynamic):

```js
const checkboxes = form.querySelectorAll('input[type="checkbox"]');
checkboxes.forEach(checkbox => {
    formData[checkbox.id] = checkbox.checked;
});
```

✅ No changes required — new checkboxes will be included automatically.

---

### 2.2 Update `generatePDFContent`

- Found starting at **line 816**.
- Modify the `sections` object (around **line 821**):

**Original:**

```js
'Body Language': [
  'posture', 'postureNotes', 'armPosition', 'armPositionNotes',
  'footTapping', 'legBouncing', 'handGestures', 'selfTouching',
  'objectManipulation', 'barrierCreation', 'bodyLanguageNotes'
],
```

**Updated:**

```js
'Body Language': [
  'posture', 'postureNotes', 'armPosition', 'armPositionNotes',
  'footTapping', 'legBouncing', 'selfHugging', 'palmExposure',
  'selfTouching', 'objectManipulation', 'barrierCreation',
  'bodyLanguageNotes'
],
```

---

### 2.3 Update `parseCSV` and `exportToCSV`

- If your app supports CSV import/export:
  - ✅ No changes are needed — the functions handle all checkbox IDs dynamically.

---

## Step 3: Test the Changes

Open the app in a browser and confirm the following:

- [ ] “Excessive Hand Gestures” is no longer present.
- [ ] “Self-Hugging” and “Palm Exposure” appear as new checkbox options.
- [ ] Form saving, loading, exporting, and importing all work with the new behaviours.

---

**Tip**: Version control your changes and test across browsers for full compatibility.
