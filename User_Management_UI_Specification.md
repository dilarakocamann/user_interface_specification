
# User Management Screen - UI Specification

## 1. Overview
This document specifies the requirements for the User Management screen. The screen allows administrators to manage users by viewing, adding, editing, and deleting user accounts.

## 2. Initial State
When the page is first loaded, it should display a table of existing users with the following columns:
- User ID
- First Name
- Last Name
- Email Address
- Role (e.g., Admin, User, Guest)
- Status (e.g., Active, Inactive)
- Actions (Edit, Delete)

### 2.1 Default View
- The table should be paginated with 10 users per page.
- Sorting by "User ID" in ascending order should be the default.
- A "Search" input field should be present above the table to filter users by name or email.
- "Add User" button should be prominently displayed for creating a new user.

## 3. Functional Requirements

### 3.1 User Table
- **Columns**: User ID, First Name, Last Name, Email Address, Role, Status, Actions (Edit, Delete)
- **Pagination**: The table should support pagination, showing 10 users per page. The developer should implement a backend API that supports pagination.
- **Sorting**: Users can sort columns in ascending or descending order by clicking the column header.
- **Filtering**: The "Search" field filters users based on First Name, Last Name, or Email Address. The table updates dynamically as the user types.
- **No Data State**: If no users match the search criteria, display a message: "No users found."

### 3.2 Add User
- **Add User Button**: Clicking the "Add User" button opens a modal form.
- **Modal Form Fields**: The form should include the following fields:
  - First Name (required)
  - Last Name (required)
  - Email Address (required, must be a valid email format)
  - Role (dropdown: Admin, User, Guest)
  - Status (dropdown: Active, Inactive)
- **Validation**: All required fields must be filled in before submitting. Show error messages below the fields if validation fails.
- **Submit Button**: When clicked, the user data should be sent to the server via a "Create User" API endpoint. Close the modal on success and refresh the user table.

### 3.3 Edit User
- **Edit Button**: The "Edit" action in the table opens a modal form with existing user data pre-filled.
- **Modal Form Behavior**: Similar to the "Add User" form, but allows updating the user data.
- **Validation**: The same validation rules apply as in the "Add User" form.
- **Submit Button**: When clicked, send the updated data to the server via an "Update User" API endpoint. Close the modal on success and refresh the user table.

### 3.4 Delete User
- **Delete Button**: Clicking the "Delete" action should open a confirmation dialog.
- **Confirmation Dialog**: Ask the user, "Are you sure you want to delete this user?" with "Confirm" and "Cancel" buttons.
- **Confirm Button**: Sends a request to the "Delete User" API endpoint. Refresh the table on success.
- **Cancel Button**: Closes the dialog without any action.

## 4. User Interface Components

### 4.1 Table
- **Type**: Paginated table with sortable columns.
- **Columns**: User ID, First Name, Last Name, Email Address, Role, Status, Actions.

### 4.2 Buttons
- **Add User**: Opens the "Add User" modal form.
- **Edit**: Opens the "Edit User" modal form for the selected user.
- **Delete**: Opens the confirmation dialog for user deletion.

### 4.3 Modals
- **Add User Modal**: Form to add new user details.
- **Edit User Modal**: Form to edit existing user details.

### 4.4 Confirmation Dialog
- **Delete Confirmation**: A dialog box confirming the deletion action.

## 5. Non-Functional Requirements
- **Responsiveness**: The user management screen should be responsive across various screen sizes, including desktop and mobile devices.
- **Performance**: Ensure that loading the user table is efficient, even with a large number of users.
- **Accessibility**: All UI components should be accessible via keyboard navigation and screen readers.

## 6. API Endpoints (for reference)
- **Get Users**: `GET /api/users?page={page}&size={size}`
- **Create User**: `POST /api/users`
- **Update User**: `PUT /api/users/{id}`
- **Delete User**: `DELETE /api/users/{id}`
