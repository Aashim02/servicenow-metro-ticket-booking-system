# 🚇 Metro Ticket Booking System — ServiceNow

A ServiceNow-based Metro Ticket Booking System built using Service Catalog, Catalog Client Scripts, UI Policies, custom station data, Flow Designer, automated fare calculation, payment selection, and QR ticket generation.

## 📌 Project Overview

The Metro Ticket Booking System provides a digital way for users to book metro tickets through the ServiceNow Service Catalog.

The solution allows a user to:

- Select a starting metro station
- Select a destination metro station
- Enter the number of passengers
- Select Single or Return journey
- Automatically calculate the applicable fare
- Select a payment method
- Select a travel date
- Submit the booking request
- Process the request through ServiceNow automation
- Generate a digital/QR ticket
- View the submitted request through the Order Status page

## 🎯 Objectives

The main objectives of this project are:

1. Build a user-friendly metro ticket booking service in ServiceNow.
2. Maintain metro station information using a dedicated custom table.
3. Automate fare calculation based on the booking information.
4. Reduce manual calculation and data-entry errors.
5. Provide conditional form behavior based on user selections.
6. Process the submitted request through ServiceNow automation.
7. Generate a digital ticket with QR information.
8. Demonstrate an end-to-end ServiceNow Service Catalog implementation.

## 🧩 Main ServiceNow Components

The project uses the following ServiceNow components:

### Service Catalog

A catalog item is used as the user-facing booking interface.

**Catalog Item:**

`Book metro tickets with automatic fare calculation and QR ticket generation`

### Catalog Variables

The booking form contains variables for information such as:

- Starting From
- Going to
- No. of Passengers
- Type of Journey
- Single Journey Fare
- Return Fare
- Mode of Payment
- Travel Date
- Total Fare

### Custom Table

A custom table named:

`Metro Station's Details`

is used to maintain metro station information and provide station reference data to the booking form.

### Client-side Automation

Catalog Client Scripts are used to perform dynamic form operations such as:

- Fare calculation
- Total fare calculation
- Field value updates
- Input validation
- Dynamic form behavior

### UI Policies

UI Policies are used to control the visibility, mandatory state, and behavior of fields based on user selections.

### Flow Designer

Flow Designer is used to automate backend processing after the catalog request is submitted.

### QR Ticket Generation

The project includes digital/QR ticket generation so that the booking can be represented as a digital ticket.

## 💰 Fare Calculation Logic

The system follows the required fare calculation behavior.

For the completed acceptance scenario:

- Number of passengers: **10**
- Single Journey Fare: **₹400**
- Return Fare: **₹400**

Therefore:

```text
Total Fare = Single Journey Fare + Return Fare
           = ₹400 + ₹400
           = ₹800
```

The important business requirement demonstrated by the project is that the configured fare values represent the booking scenario and the final total is calculated from the Single and Return fare components.

## 💳 Payment Options

The booking form provides multiple payment choices:

- Cash
- UPI
- Card
- Others

The form provides user feedback based on the selected payment method.

For example, when Card is selected, the form displays a payment-related informational message to the user.

## 🔄 Booking Workflow

The overall process is:

```text
User opens Catalog Item
        ↓
Select Starting Station
        ↓
Select Destination Station
        ↓
Enter Passenger Count
        ↓
Select Journey Type
        ↓
Fare is calculated
        ↓
Select Payment Method
        ↓
Select Travel Date
        ↓
Review Total Fare
        ↓
Submit / Order Now
        ↓
ServiceNow Request Created
        ↓
Flow Designer Processing
        ↓
Ticket / QR Information Generated
        ↓
Order Status Confirmation
```

## 🗃️ Station Data

Metro station information is maintained separately from the booking form.

The custom station table provides a centralized source for station information. This allows the booking form to use reference-based station selection rather than relying entirely on free-text input.

Typical station information can include:

- Station Name
- Station Code
- Station Status

## 🧪 Tested Scenario

The final tested scenario used:

| Field | Value |
|---|---|
| Starting From | Ashok Nagar |
| Going to | Chennai Central |
| No. of Passengers | 10 |
| Type of Journey | Return |
| Single Journey Fare | ₹400 |
| Return Fare | ₹400 |
| Total Fare | ₹800 |
| Mode of Payment | Card |
| Travel Date | 2026-09-25 |

### Expected Fare Result

```text
₹400 + ₹400 = ₹800
```

The booking was successfully submitted and the ServiceNow Order Status page displayed the submitted request.

## 📸 Screenshots

Recommended GitHub repository screenshots:

```text
screenshots/
├── catalog-form.png
├── fare-calculation.png
├── payment-selection.png
├── ticket-summary.png
├── order-status.png
└── qr-ticket.png
```

Add screenshots to the repository and reference them in this README using:

```markdown
![Catalog Form](screenshots/catalog-form.png)
```

## 📦 Update Set Installation

The project is packaged as a ServiceNow Update Set XML file.

### Requirements

- A ServiceNow instance
- System Administrator or appropriate administrative permissions
- The exported Update Set XML file

### Import Steps

1. Log in to the target ServiceNow instance.
2. Open the Application Navigator.
3. Search for **Retrieved Update Sets**.
4. Open:

   `System Update Sets → Retrieved Update Sets`

5. Use **Import Update Set from XML**.
6. Choose the exported `.xml` Update Set file.
7. Upload the XML.
8. Open the imported Update Set.
9. Click **Preview Update Set**.
10. Review any preview errors or conflicts.
11. If the preview is clean and the changes are expected, click **Commit Update Set**.
12. Verify the catalog item, scripts, UI policies, flows, tables, and related configuration.

ServiceNow's PDI backup guidance documents the same export/import workflow: complete the local Update Set, use **Export to XML**, then import it from **Retrieved Update Sets** and preview/commit it on the target instance.

## ⚠️ Important Deployment Note

An Update Set primarily transports ServiceNow configuration/customization. It should not be assumed to contain every type of application data.

If the project depends on station records stored in the custom station table, verify that those records are available in the target instance. If required, export/import the necessary data separately.

Also verify:

- Catalog Item availability
- Variable definitions
- Client Scripts
- UI Policies
- Script Includes, if used
- Flow Designer flow and subflows, if used
- Custom table configuration
- Reference data
- Roles/ACLs, if applicable
- Any notification configuration
- QR/ticket generation dependencies

## 🔐 Security Notes

Do not commit sensitive information to GitHub.

Never include:

- ServiceNow passwords
- API keys
- Access tokens
- OAuth secrets
- Personal credentials
- Private certificates
- Sensitive customer information
- Production credentials
- Unnecessary personal data

The repository should contain the project implementation and documentation, not environment secrets.

## 📁 Suggested Repository Structure

```text
metro-ticket-booking-servicenow/
│
├── README.md
│
├── update-set/
│   └── metro-ticket-booking-update-set.xml
│
├── screenshots/
│   ├── catalog-form.png
│   ├── fare-calculation.png
│   ├── payment-selection.png
│   ├── ticket-summary.png
│   ├── order-status.png
│   └── qr-ticket.png
│
├── documentation/
│   └── Metro_Ticket_Booking_System_Final_Report.pdf
│
└── LICENSE
```

## 🚀 Deployment Flow

```text
Development PDI
      ↓
Complete Update Set
      ↓
Export Update Set to XML
      ↓
Download XML
      ↓
Add XML to GitHub
      ↓
Clone / Download Repository
      ↓
Import XML into Target ServiceNow Instance
      ↓
Preview Update Set
      ↓
Resolve / Review Conflicts
      ↓
Commit Update Set
      ↓
Test Application
```

## 📝 Project Highlights

- ServiceNow Service Catalog implementation
- Custom metro station data model
- Reference-based station selection
- Dynamic fare calculation
- Single and Return journey support
- Passenger-based booking input
- Multiple payment options
- Conditional user-interface behavior
- Flow Designer automation
- Digital ticket generation
- QR-based ticket concept
- Order submission and confirmation
- End-to-end functional testing

## 📊 Final Result

The project successfully demonstrates the required metro ticket booking scenario.

For the tested Return journey with 10 passengers:

```text
Single Journey Fare = ₹400
Return Fare         = ₹400
---------------------------
Total Fare          = ₹800
```

The request was successfully submitted through the ServiceNow catalog and the resulting order/request could be viewed from the Order Status page.

## 🔮 Future Enhancements

Possible future enhancements include:

- Real-time route-based fare calculation
- Distance-based fare calculation
- Dedicated route/fare master tables
- Passenger-category pricing
- Child/senior-citizen fares
- Ticket cancellation
- Refund processing
- QR code scanning and verification
- Automated email/SMS ticket delivery
- Payment gateway integration
- Admin dashboard
- Booking history
- Travel analytics
- Station availability information
- Real-time metro service status

## 👨‍💻 Project

**Project:** Metro Ticket Booking System  
**Platform:** ServiceNow  
**Application Area:** Service Catalog / ITSM Platform Development  
**Environment:** ServiceNow Personal Developer Instance (PDI)

---

## 📚 References

- ServiceNow Personal Developer Instance backup and Update Set export/import guidance
- ServiceNow Update Set functionality and platform documentation

> This repository is intended for learning, demonstration, portfolio, and ServiceNow development purposes.
