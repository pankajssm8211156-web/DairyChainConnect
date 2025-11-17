# Dairy Supply Chain Platform - Design Guidelines

## Design Approach
**System-Based Approach**: Drawing from Linear's clean enterprise aesthetic combined with Material Design's robust component patterns. This platform requires excellent information hierarchy and data visualization capabilities for its multi-role dashboard system.

## Typography System

**Font Stack**: Inter (primary), system-ui fallback
- Headers: 600-700 weight, sizes: text-4xl (dashboard titles), text-2xl (section headers), text-xl (card headers)
- Body: 400-500 weight, text-base for primary content, text-sm for secondary info, text-xs for labels
- Data/Numbers: 600 weight, tabular-nums for alignment in tables and charts
- Line heights: leading-tight for headers, leading-relaxed for body content

## Layout System

**Spacing Primitives**: Use Tailwind units of 1, 2, 3, 4, 6, 8, 12, 16
- Component padding: p-4 to p-6 for cards, p-3 for compact elements
- Section spacing: space-y-6 for dashboard sections, space-y-4 for form groups
- Grid gaps: gap-4 for card grids, gap-6 for major sections

**Container Strategy**:
- Dashboard content: max-w-7xl with px-4 sm:px-6 lg:px-8
- Forms/Modals: max-w-md to max-w-2xl depending on complexity
- Full-width tables: w-full with horizontal scroll on mobile

## Core Layout Patterns

### Navigation Structure
**Sidebar + Top Bar Combination**:
- Left sidebar (w-64 hidden lg:block): Role-specific navigation, collapsed to icon-only on tablet
- Top bar: User profile, notifications, role switcher, mobile menu toggle
- Mobile: Bottom navigation for primary actions + hamburger for full menu

### Dashboard Layouts
**Grid-Based Information Architecture**:
- 3-column grid (lg:grid-cols-3) for metric cards on desktop
- 2-column (md:grid-cols-2) for tablet
- Single column stacked on mobile
- Mixed layouts: 2/3 main content + 1/3 sidebar for analytics + quick actions

### Role-Specific Dashboard Components

**Milkmen Dashboard**:
- Top metrics row: 4 stat cards (grid-cols-2 md:grid-cols-4) showing buying price, market rate, today's production, profit/loss
- Main content area: Production records table + chart visualization side-by-side (lg:grid-cols-2)
- Transport tracking map: Full-width card with embedded interactive map
- Bottom section: Recent transactions list

**Company Dashboard**:
- Executive summary: 6 KPI cards (grid-cols-2 md:grid-cols-3 lg:grid-cols-6)
- Financial charts: 2-column layout (lg:grid-cols-2) for profit trends + expense breakdown
- Logistics overview: Tabbed interface (delivery status, inventory, transport fleet)
- Staff management: Data table with search, filters, pagination
- Full-width financial report section with expandable details

**Customer Portal**:
- Hero-style product showcase: Featured products carousel with large images
- Product grid: 3-4 columns (grid-cols-2 md:grid-cols-3 lg:grid-cols-4) of product cards
- Order tracking: Timeline/stepper component showing production → packaging → transit → delivery
- Cart sidebar: Sticky positioned, slides in from right
- Order history: Card-based list with status badges

**Retailer Interface**:
- Inventory grid: Compact table with inline editing capabilities
- Order management: Kanban-style columns (pending, processing, completed)
- Stock alerts: Priority notification cards at top
- Analytics section: Chart + table combination for sales data

## Component Library

### Cards
- Standard card: rounded-lg border with subtle shadow, p-6 spacing
- Metric cards: Centered layout, large number (text-3xl font-bold), label below (text-sm), icon top-right
- Product cards: Image at top (aspect-video), content p-4, button at bottom
- Data cards: Compact p-4, dense information, hover state for interactivity

### Tables
- Zebra striping for readability
- Sticky header (thead position-sticky top-0)
- Responsive: Horizontal scroll on mobile with shadow indicators
- Row heights: py-3 for data rows, py-4 for header
- Cell padding: px-4 for text columns, px-2 for action columns

### Forms
- Stacked labels above inputs (not floating)
- Input groups: space-y-4 between fields, space-y-6 between sections
- Input sizing: h-10 for standard, h-12 for emphasized
- Multi-step registration: Progress stepper at top, one section visible at a time
- Validation: Inline error messages below fields, success states with checkmarks

### Navigation Elements
- Tab groups: Underlined active state, horizontal scroll on mobile
- Breadcrumbs: text-sm with separators, max 3 levels visible
- Pagination: Compact buttons with number display, prev/next prominent
- Filters: Collapsible panel on mobile, permanent sidebar on desktop

### Data Visualization
- Chart containers: aspect-video or aspect-square depending on chart type
- Chart legends: Positioned bottom or right, never overlapping data
- Tooltips: Floating cards on hover with detailed information
- Real-time updates: Subtle pulse animation on data changes

### Status & Feedback
- Status badges: Compact (px-2 py-1), rounded-full, uppercase text-xs
- Progress bars: h-2 rounded-full, animated transitions
- Loading states: Skeleton screens matching final content layout
- Empty states: Centered icon + heading + description + CTA
- Toast notifications: Fixed top-right, stack vertically, auto-dismiss

### Tracking Interface
- Map component: min-h-96, full-width container
- Timeline stepper: Vertical on mobile, horizontal on desktop
- Live status indicators: Pulsing dot animations
- Delivery route: Polyline overlay on map with markers

### Payment Components
- Checkout flow: Single column max-w-xl centered
- Payment form: Stripe Elements with consistent styling
- Order summary: Sticky sidebar on desktop, collapsible on mobile
- Transaction history: Expandable accordion with detailed receipts

## Responsive Breakpoints
- Mobile-first approach: base styles for mobile
- sm (640px): Compact tablets, 2-column grids
- md (768px): Tablets, show sidebar navigation
- lg (1024px): Desktop, full 3-column layouts, sidebar navigation
- xl (1280px): Large desktop, max-width containers

## Accessibility Standards
- Form inputs: Consistent h-10 height, clear focus states with ring offset
- Interactive elements: Minimum 44x44px touch targets on mobile
- Skip navigation: Hidden link for keyboard users
- ARIA labels: All icon-only buttons, dynamic content regions
- Keyboard navigation: Full tab order, escape to close modals
- Screen reader: Meaningful alt text, status announcements

## Images
**Product Images**: High-quality dairy product photography throughout customer portal - milk bottles, cheese, yogurt in clean studio lighting
**Dashboard Illustrations**: Simple line illustrations for empty states and onboarding
**Map Integration**: Embedded real-time maps for transport tracking (Leaflet/Mapbox)
**No Hero Image**: This is an application dashboard, not a marketing site - focus on functional UI

## Key Interaction Patterns
- Modal overlays: Centered, max-w-2xl, dark backdrop
- Slide-out panels: From right for details/filters, smooth transitions
- Inline editing: Click to edit in tables, save/cancel actions
- Drag and drop: For file uploads and order prioritization
- Infinite scroll: For long lists with "load more" fallback
- Auto-save: For forms with draft indicators
- Confirmation dialogs: For destructive actions