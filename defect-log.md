# Defect Log

The following are candidate findings from Rakesh's manual exploration. Verify
each item and complete the environment and reproduction details before
submitting it as a confirmed defect.

## DEF-001 — Category filter may have no accessible name

- **Area:** Buyer catalogue
- **Severity:** Low (provisional)
- **Status:** Needs accessibility verification
- **Environment:** Browser and OS details not provided
- **Account role:** Buyer

### Steps to reproduce

To be completed with the exact steps and assistive technology used to verify
the issue.

### Expected result

The category filter has a programmatic name that identifies its purpose to
assistive technology.

### Actual result

In the catalogue DOM shared for review, the category `<select>` has no
associated `<label>`, `aria-label`, or `title` attribute. Verify its computed
accessible name before confirming the issue.

### Evidence

The pasted catalogue DOM is preliminary evidence. Add a screenshot or
accessibility-tree/screen-reader capture after manual verification.

---

## DEF-002 — Past delivery date can be selected

- **Area:** Buyer checkout
- **Severity:** Low (provisional)
- **Status:** Observed in UI; server-side behavior not verified
- **Environment:** Chrome on Windows (from the supplied screenshot); date shown
  as 2026-11-03, while the computer date shown is 2026-11-17
- **Account role:** Buyer

### Steps to reproduce

1. Open checkout.
2. Select 2026-11-03 as the delivery date.

### Expected result

The delivery date picker permits only today through the next 7 days.

### Actual result

The checkout date field displays the past date 2026-11-03. The screenshot does
not establish whether the application accepts an order with that date.

### Impact

Buyers can select an invalid date and may reach an error later in checkout.

### Evidence

- [Past date displayed on checkout](./evidence/checkout-past-date-selected.png)

---

## DEF-003 — Delivery slot selection reported as unavailable

- **Area:** Buyer checkout
- **Severity:** Unassigned pending verification
- **Status:** Needs retest
- **Environment:** Chrome on Windows (from the supplied screenshots)
- **Account role:** Buyer

### Steps to reproduce

Rakesh reported that he could not select a delivery slot. Record the exact date,
time, slot, and actions used when reproducing this.

### Expected result

For an eligible delivery date, available slots can be selected. Same-day slot
availability is subject to the 10:00 cut-off and other booking rules.

### Actual result

The supplied screenshots show no selected radio option and an “Invalid delivery
slot” message after submission. They do not establish that an eligible slot
could not be selected. The computer clock shown is after 10:00 on 2026-11-17,
when same-day delivery is no longer available. Another screenshot shows the
date field changed to 2026-11-21 while the URL still contains
`date=2026-11-17`; confirm whether “Show slots” was pressed after changing the
date.

### Evidence

- [Initial checkout slot options](./evidence/checkout-initial-slots.png)
- [Invalid delivery slot message](./evidence/checkout-invalid-slot-message.png)
- [Future date before slot refresh](./evidence/checkout-future-date-before-refresh.png)

---

Do not count DEF-001 or DEF-003 as confirmed until their verification notes and
evidence are completed.
