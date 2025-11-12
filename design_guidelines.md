# Student Attendance Management System - Design Guidelines

## Design Approach
**System-Based Approach**: Material Design principles adapted for educational productivity tools
**Justification**: This is a utility-focused, information-dense application where efficiency and clarity are paramount. Teachers need quick access to student data, fast attendance marking, and clear report visualization.

## Typography System
- **Primary Font**: Inter or Roboto via Google Fonts CDN
- **Heading Hierarchy**: 
  - Page titles: text-3xl font-bold
  - Section headers: text-xl font-semibold
  - Card titles: text-lg font-medium
  - Labels: text-sm font-medium uppercase tracking-wide
- **Body Text**: text-base for primary content, text-sm for secondary information
- **Data Display**: Tabular numerics use tabular-nums class for alignment

## Layout & Spacing System
**Tailwind Units**: Standardize on 2, 4, 6, 8, 12, 16 for consistency
- Component padding: p-4 to p-6
- Section spacing: space-y-6 to space-y-8
- Card gaps: gap-4 to gap-6
- Page margins: px-4 md:px-6 lg:px-8

**Grid System**: 
- Dashboard: 12-column grid (grid-cols-12) for flexible layouts
- Reports: 2-3 column layouts for metric cards
- Student lists: Single column with card-based rows

## Core Components

### Navigation
- **Top Bar**: Fixed header with app logo, current class context, teacher profile dropdown
- **Sidebar**: Collapsible navigation (Dashboard, Mark Attendance, Reports, Students, Alerts, Settings)
- Icons from Heroicons via CDN
- Active state indicated with subtle background treatment

### Dashboard Layout
- **Stats Cards Row**: 4-column grid (grid-cols-1 md:grid-cols-2 lg:grid-cols-4) displaying: Today's Classes, Total Students, Average Attendance %, Pending Alerts
- **Quick Actions Panel**: Large buttons for "Mark Attendance" and "View Today's Summary"
- **Recent Activity Feed**: List of recent attendance entries and alerts

### Attendance Marking Interface
- **Class Selector**: Dropdown at top to choose class/period
- **Student List Table**: 
  - Columns: Photo thumbnail, Student Name, Roll Number, Status toggle
  - Status: Radio buttons or pill toggles (Present/Absent/Late)
  - Bulk actions: "Mark All Present" button
- **Action Bar**: Sticky bottom bar with Save and Cancel buttons
- **Barcode Scanner**: Floating action button (bottom-right) to activate scanner overlay

### Data Tables
- Striped rows for readability (even rows with subtle background)
- Sortable column headers with arrow indicators
- Pagination controls at bottom (10/25/50 entries per page)
- Search/filter bar above table
- Responsive: Stack to cards on mobile viewports

### Report Generation
- **Filter Panel**: Card with date range picker, class selector, student filter
- **Report Display**: 
  - Summary metrics in 3-column card grid
  - Attendance trend (placeholder for chart: <!-- CHART: Line graph showing attendance % over time -->)
  - Detailed breakdown table
- **Export Options**: Buttons for PDF/CSV download

### Alert System
- **Configuration Panel**: Form with threshold slider (percentage), notification method checkboxes
- **Alert History**: Timeline-style list with student name, attendance %, date sent, status
- **Alert Badge**: Notification counter on sidebar navigation item

### Forms & Inputs
- Consistent input styling: rounded corners (rounded-lg), clear labels above inputs
- Required fields marked with asterisk
- Validation messages below inputs
- Primary action buttons: Full padding (px-6 py-3), prominent placement
- Secondary actions: Ghost button style

### Cards & Containers
- Standard card: rounded-lg with shadow-sm, p-6 padding
- Elevation for interactive cards: hover:shadow-md transition
- Headers within cards: pb-4 border-b with title + optional action button

### Modal Overlays
- Confirmation dialogs: Centered, max-w-md, with clear action buttons
- Detail views: Slide-in panel from right (max-w-2xl)
- Backdrop: Semi-transparent overlay with blur effect

## Responsive Breakpoints
- Mobile-first approach
- Sidebar collapses to hamburger menu below md breakpoint
- Multi-column grids stack to single column on mobile
- Tables convert to stacked cards with key info visible

## Accessibility
- All interactive elements keyboard navigable
- Focus indicators on all inputs and buttons
- Aria labels for icon-only buttons
- Sufficient contrast ratios throughout
- Form inputs with associated labels (not placeholders alone)

## Animations
**Minimal & Purposeful Only**:
- Page transitions: None (instant navigation for speed)
- Dropdown menus: Simple fade-in (transition-opacity duration-150)
- Modal entry: Scale from 95% to 100% (transition-transform duration-200)
- Loading states: Subtle pulse on skeleton screens

## Images
**No hero image** - This is a dashboard application focused on functionality
**Profile thumbnails**: Small circular avatars (w-8 h-8 to w-10 h-10) for student photos in lists
**Empty states**: Simple illustrations or icons when no data exists

This system prioritizes teacher efficiency, data clarity, and quick task completion over visual flourishes.