# InvoiceMe

## Description
InvoiceMe is a simple, all-in-one platform that connects contractors with clients, even through vendors in subcontractor relationships. It allows contractors to create invoices, track payments, and manage their business all in one place.

## Entity Types
- Client: A person or company that hires a contractor or vendor to perform a service.
- Vendor: An intermediary business entity that hires a subcontractor to provide service to a client.
- Contractor: A person or company that provides a service to a client or vendor.
- Invoice: A document that outlines the services provided by a contractor or vendor to a client or vendor, including the cost of the services and payment terms.
- Timesheet: A document that outlines the hours worked by a contractor or vendor on a project for a client or vendor.

## Features
- Clients can create a profile and view invoices and timesheets from contractors and vendors
- Clients can approve timesheets and invoices for payment or dispute them with a comment
- Clients can create new project codes
- Contractors can create a profile and submit invoices and timesheets to clients and vendors
- Contractors can view the status of their invoices and timesheets
- Contractors can view the status of their payments
- Vendors can create a profile for their business and submit invoices and timesheets to clients
- Vendors, clients and contractors can view their payment history

## Additional Details
- The full lifecycle of the work-to-payment process is tracked in the system
- Two main relationships occur: Direct contractor to client and contractor to vendor to client.
- Clients can have multiple vendors and contractors
- Vendors can have multiple contractors
- Contractors can have multiple clients and vendors
- Invoices and timesheets can be disputed by clients and vendors
- Invoices and timesheets can be approved by clients and vendors
- Invoices and timesheets can be paid by clients and vendors
- Invoices and timesheets can be rejected by clients and vendors
- Invoices and timesheets can be edited by contractors and vendors
- Invoices and timesheets can be deleted by contractors and vendors
- Invoices and timesheets can be viewed by clients, contractors, and vendors
- Invoices and timesheets can be searched by clients, contractors, and vendors
- Invoices and timesheets can be filtered by clients, contractors, and vendors
- Invoices and timesheets can be sorted by clients, contractors, and vendors
- Invoices and timesheets can be exported by clients, contractors, and vendors

## Implementation Workflow

### Time Recording
- Implement a timesheet entry system where contractors can:
  - Select client/vendor and associated project
  - Record hours with date, project code, description, and hourly rate
  - Save timesheet entries as draft or submit for approval
  - Attach supporting documents if needed
- Allow bulk time entry and timesheet templates for recurring work

### Approval Process
- Implement multi-level approval workflow:
  - Timesheet submitted by contractor → vendor approval (if applicable) → client approval
  - Email/in-app notifications for pending approvals
  - Approval dashboard for clients/vendors showing submitted timesheets
  - Option to partially approve, reject with comments, or request clarification
  - Automatic reminders for pending approvals after configurable time period

### Invoice Generation
- Automated invoice generation based on approved timesheets:
  - For contractor to vendor: System generates invoice when vendor approves time
  - For vendor to client: System generates invoice including contractor costs plus vendor markup
  - For contractor to client (direct): System generates invoice when client approves time
- Support for scheduled invoice generation (weekly, bi-weekly, monthly)
- Customizable invoice templates with branding options
- PDF generation and email delivery

### Payment Processing
- Implement payment tracking system:
  - Manual payment recording with reference numbers and dates
  - Optional integration with payment processors (Stripe, PayPal, etc.)
  - Support for partial payments and payment terms
- For vendor intermediaries:
  - Track incoming client payments
  - Link client payments to contractor invoices
  - Manage payment disbursement to contractors
  - Configure automatic or manual payment forwarding

### Reporting
- Implement dashboard views for:
  - Unpaid/overdue invoices
  - Time recorded vs time approved
  - Payment history and aging reports
  - Profit margins for vendors
- Export options for accounting systems (CSV, QuickBooks, etc.)

### Technical Implementation Suggestions
- Database: Supabase PostgreSQL for relational data with proper constraints
- Authentication: Supabase Auth for user management and role-based access control
- Backend: Node.js/Express or similar framework with RESTful API
- Frontend: Next.js + Shadcn + Tailwind CSS for responsive UI
- PDF Generation: Use library like PDFKit or jsPDF
- Notifications: Email service + in-app notification system
