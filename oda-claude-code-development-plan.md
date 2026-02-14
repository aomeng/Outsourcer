# Outsourcing Decision Advisor
## Claude Code Development Plan - Browser-Based Frontend

**Development Approach:** AI-Assisted Rapid Prototyping with Claude Code  
**Timeline:** 4-6 weeks to functional prototype  
**Target:** Modern web browsers (Chrome, Firefox, Safari, Edge)

---

## Table of Contents

1. [Development Philosophy](#philosophy)
2. [Sprint 0: Setup & Architecture (3-5 days)](#sprint-0)
3. [Sprint 1: Core Assessment Flow (1 week)](#sprint-1)
4. [Sprint 2: Analysis Engine (1 week)](#sprint-2)
5. [Sprint 3: Results & Visualization (1 week)](#sprint-3)
6. [Sprint 4: Advanced Features (1 week)](#sprint-4)
7. [Sprint 5: Polish & Deploy (3-5 days)](#sprint-5)
8. [Tech Stack](#tech-stack)
9. [Project Structure](#project-structure)
10. [Claude Code Workflow](#claude-workflow)
11. [Testing Strategy](#testing)
12. [Deployment Options](#deployment)

---

## Development Philosophy {#philosophy}

### Why Claude Code?

**Ideal for this project because:**
- ✅ Complex business logic (algorithms) - Claude excels at translating requirements to code
- ✅ Multiple interconnected components - Claude can maintain context
- ✅ Data transformations and calculations - Claude handles math well
- ✅ Rapid iteration on UI/UX - Quick component generation
- ✅ Comprehensive documentation - Claude generates docs alongside code

### Core Principles

1. **Iterative Development**: Build working features incrementally
2. **Client-Side First**: Start with browser-only, add backend later if needed
3. **Component-Driven**: Small, testable, reusable components
4. **Progressive Enhancement**: Core functionality first, bells and whistles later
5. **Rapid Prototyping**: Get to usable product quickly, refine continuously

### Development Model

```
Week 1: Working basic flow (input → calculate → show results)
Week 2: Complete algorithms and risk assessment
Week 3: Beautiful visualizations and UX polish
Week 4: Advanced features (scenarios, exports, benchmarks)
Week 5: Testing, refinement, deployment
Week 6: Buffer for unexpected issues
```

---

## Sprint 0: Setup & Architecture (3-5 days) {#sprint-0}

### Goal
Get development environment ready and make architectural decisions.

### Tasks

#### Day 1: Project Initialization

**Claude Code Prompts:**

```bash
# Initialize project
"Create a modern React + TypeScript + Vite project for an outsourcing 
decision advisor app. Include Tailwind CSS, React Router, and Recharts 
for visualizations. Set up ESLint and Prettier."

# Project structure
"Create a well-organized folder structure for a React app with:
- Pages for multi-step assessment and results
- Components for forms, charts, and UI elements
- Services for calculation logic
- Types for TypeScript interfaces
- Utils for helper functions"
```

**Expected Output:**
```
outsourcing-advisor/
├── src/
│   ├── pages/
│   │   ├── Home.tsx
│   │   ├── Assessment.tsx
│   │   └── Results.tsx
│   ├── components/
│   │   ├── forms/
│   │   ├── charts/
│   │   └── ui/
│   ├── services/
│   │   ├── calculators/
│   │   └── storage/
│   ├── types/
│   ├── utils/
│   └── App.tsx
├── public/
├── package.json
├── tsconfig.json
├── tailwind.config.js
└── vite.config.ts
```

#### Day 2: Data Models & Types

**Claude Code Prompt:**

```typescript
"Create TypeScript interfaces for the Outsourcing Decision Advisor based 
on this Deloitte methodology. I need types for:

1. AssessmentData - all input data from user
2. FinancialMetrics - costs, savings, ROI data
3. RiskFactors - 5 risk categories with scores
4. ReadinessFactors - 6 readiness components
5. StrategicFactors - core competency questions
6. AnalysisResults - calculated outputs
7. Recommendation - final recommendation with tier and conditions

Make them comprehensive with JSDoc comments."
```

**Expected Output:** Complete TypeScript type definitions

#### Day 3: Local Storage Service

**Claude Code Prompt:**

```typescript
"Create a browser localStorage service for persisting assessment data.
Include:
- Save/load assessment drafts
- List all saved assessments
- Delete assessments
- Export/import functionality (JSON)
- TypeScript typed with error handling
- Automatic save every 30 seconds"
```

#### Day 4: Design System & UI Components

**Claude Code Prompt:**

```typescript
"Create a design system for the Outsourcing Decision Advisor with:

1. Color palette for professional business app
2. Typography scale
3. Spacing system
4. Reusable components:
   - Button (primary, secondary, danger)
   - Input (text, number, currency)
   - Slider with labels
   - Card
   - ProgressBar
   - Badge (for recommendation tiers)
   - Modal
   
Use Tailwind CSS. Make components accessible (ARIA labels, keyboard nav)."
```

#### Day 5: Routing & Layout

**Claude Code Prompt:**

```typescript
"Set up React Router with these routes:
- / - Homepage with overview and 'Start Assessment' CTA
- /assessment - Multi-step assessment wizard
- /results/:id - Results display page
- /saved - List of saved assessments

Create a layout component with:
- Header with navigation
- Footer with links
- Responsive sidebar for larger screens
- Mobile-friendly hamburger menu"
```

### Deliverables

- [ ] Project initialized and running locally
- [ ] TypeScript types defined
- [ ] Storage service implemented
- [ ] Design system components ready
- [ ] Routing configured
- [ ] Clean, documented codebase

### Success Criteria

✅ `npm run dev` starts the app  
✅ Can navigate between routes  
✅ Design system components render correctly  
✅ TypeScript compiles without errors  
✅ Can save/load data to localStorage  

---

## Sprint 1: Core Assessment Flow (1 week) {#sprint-1}

### Goal
Build the multi-step assessment wizard where users input their data.

### Architecture Decision: Form State Management

**Option A: React Hook Form** (Recommended for Claude Code)
- Performant, less re-renders
- Built-in validation
- Easy integration with TypeScript
- Good for complex forms

**Option B: Simple useState**
- More straightforward for AI generation
- Easier to debug
- Full control

**Recommendation:** Start with useState, migrate to React Hook Form if performance issues arise.

### Day 1-2: Assessment Wizard Structure

**Claude Code Prompt:**

```typescript
"Create a multi-step assessment wizard component with 6 steps:

Step 1: Function Details
- Function name (text input)
- Function category (dropdown: IT, HR, Finance, Customer Service, etc.)
- Current headcount (number)
- Department/business unit (text)

Step 2: Financial Metrics
- Current annual cost (currency input with formatting)
- Cost per transaction (currency)
- Estimated outsourcing cost (currency)
- Transition cost (currency)
- Budget constraints (currency, optional)
- Expected volume change % (number, -50 to +100)

Step 3: Performance Metrics
- Error rate % (0-100)
- Customer satisfaction (1-10 slider with descriptions)
- SLA achievement % (0-100)
- Processing time (number input for hours)
- Utilization rate % (optional)
- Productivity score (1-10, optional)

Step 4: Risk Assessment
- Business criticality (1-10 slider with descriptions:
  1-3: Low - minimal impact if interrupted
  4-6: Medium - significant but manageable
  7-8: High - major impact on operations
  9-10: Critical - business-critical function)
- Data sensitivity (1-10 slider)
- Regulatory complexity (1-10 slider)
- Change management capacity (1-10 slider)

Step 5: Readiness Evaluation
- Process documentation % (0-100)
- Process standardization % (0-100)
- Stakeholder alignment (1-10 slider)
- Internal expertise level (1-10)
- Vendor market maturity (1-10)

Step 6: Strategic Factors
- Is this a core competency? (Yes/No)
- Requires proprietary knowledge? (Yes/No)
- Customer-facing function? (Yes/No)
- Drives competitive advantage? (Yes/No)
- Can be standardized? (Yes/No)
- Innovation score (1-10 slider)

Features needed:
- Progress indicator showing current step
- Back/Next navigation
- Form validation with helpful error messages
- Auto-save to localStorage every 30 seconds
- 'Save as Draft' button
- Input helpers (tooltips, example values)
- Responsive design (mobile-friendly)

Use TypeScript, Tailwind CSS, and the design system components."
```

### Day 3: Form Components

**Claude Code Prompt:**

```typescript
"Create specialized form input components:

1. CurrencyInput
   - Formats as user types ($1,234,567)
   - Accepts only numbers
   - Shows validation errors
   - Optional helper text

2. PercentageInput
   - Shows % symbol
   - Validates 0-100 range
   - Helpful error messages

3. SliderWithLabels
   - Shows current value
   - Descriptive labels for low/medium/high
   - Visual feedback
   - Keyboard accessible

4. YesNoToggle
   - Toggle switch with labels
   - Clear visual state
   - Accessible

Each component should:
- Be TypeScript typed
- Have proper ARIA labels
- Show validation states
- Be mobile-friendly
- Include helpful tooltips"
```

### Day 4-5: Validation & UX Polish

**Claude Code Prompt:**

```typescript
"Add comprehensive validation to the assessment wizard:

Required fields:
- Function name
- Function category  
- Current annual cost
- Estimated outsourcing cost

Validation rules:
- All currency values must be > 0
- Percentages must be 0-100
- Slider values must be 1-10
- Error rate must be valid percentage
- Can't proceed to next step with validation errors

UX enhancements:
- Show which steps are complete (green checkmark)
- Disable 'Next' if current step invalid
- Clear error messages near each field
- 'Save Draft' works from any step
- Warning if user tries to leave with unsaved changes
- Progress percentage (e.g., '67% complete')
- Estimated time remaining
- Helpful placeholder text and examples"
```

### Weekend: Testing & Refinement

**Manual Testing Checklist:**
- [ ] Can complete all 6 steps
- [ ] Validation works correctly
- [ ] Auto-save works
- [ ] Can navigate back and forth
- [ ] Mobile experience is good
- [ ] Tooltips are helpful
- [ ] No TypeScript errors
- [ ] No console errors

### Deliverables

- [ ] Complete 6-step wizard
- [ ] All input components working
- [ ] Validation implemented
- [ ] Auto-save functional
- [ ] Mobile responsive
- [ ] Accessible (keyboard navigation, ARIA)

### Success Criteria

✅ User can input all required data  
✅ Form validates correctly  
✅ Data persists to localStorage  
✅ Mobile experience is smooth  
✅ No major bugs or errors  

---

## Sprint 2: Analysis Engine (1 week) {#sprint-2}

### Goal
Build the calculation logic that analyzes input data and generates recommendations.

### Day 1: Cost-Benefit Calculator

**Claude Code Prompt:**

```typescript
"Create a cost-benefit analysis calculator with these functions:

calculateCostBenefit(params: {
  currentAnnualCost: number;
  outsourceAnnualCost: number;
  transitionCost: number;
  contractYears: number;
  volumeChangePercent: number;
  efficiencyGainPercent: number;
}): CostBenefitResult

Return:
{
  totalSavings: number;
  savingsPercentage: number;
  breakEvenMonths: number;
  roiPercentage: number;
  fiveYearTCOCurrent: number;
  fiveYearTCOOutsourced: number;
  npv: number; // with 8% discount rate
  paybackPeriodMonths: number;
  yearByYearBreakdown: Array<{
    year: number;
    currentCost: number;
    outsourceCost: number;
    annualSavings: number;
    cumulativeSavings: number;
  }>;
}

Include:
- Detailed JSDoc comments explaining formulas
- Proper handling of edge cases (negative savings, never breaks even)
- TypeScript types
- Unit tests (Jest) for common scenarios
- Sensitivity analysis function for best/likely/worst cases"
```

### Day 2: Risk Assessment Calculator

**Claude Code Prompt:**

```typescript
"Create a risk assessment calculator:

calculateRiskScore(params: {
  businessCriticality: number; // 1-10
  dataSensitivity: number; // 1-10
  regulatoryComplexity: number; // 1-10
  vendorMaturity: number; // 1-10 (higher = better)
  processStability: number; // 1-10 (higher = better)
}): RiskAssessmentResult

Weights:
- Business criticality: 30%
- Data sensitivity: 25%
- Regulatory complexity: 20%
- Vendor maturity: 15% (inverse - low maturity = high risk)
- Process stability: 10% (inverse)

Return:
{
  overallScore: number; // 0-100
  riskLevel: 'low' | 'medium' | 'high' | 'critical';
  components: Array<{
    name: string;
    score: number;
    weight: number;
    severity: string;
    description: string;
  }>;
  keyRisks: string[]; // Array of risk descriptions
  mitigationRecommendations: string[]; // Top 5-7 mitigation actions
}

Risk levels:
- 0-25: Low
- 26-50: Medium  
- 51-75: High
- 76-100: Critical

Generate specific mitigation recommendations based on which 
components score high. Include TypeScript types and unit tests."
```

### Day 3: Readiness Assessment Calculator

**Claude Code Prompt:**

```typescript
"Create a readiness assessment calculator:

calculateReadiness(params: {
  processDocumentationPercent: number; // 0-100
  processStandardizationPercent: number; // 0-100
  stakeholderAlignment: number; // 1-10
  changeCapacity: number; // 1-10
  vendorMarketMaturity: number; // 1-10
  budgetApproved: boolean;
  executiveSponsorship: boolean;
}): ReadinessResult

Weights:
- Process maturity (avg of doc + standardization): 25%
- Documentation completeness: 15%
- Stakeholder alignment: 20%
- Change management capacity: 15%
- Vendor market availability: 15%
- Financial preparedness: 10%

Return:
{
  overallScore: number; // 0-100
  readinessLevel: 'ready' | 'mostly-ready' | 'needs-preparation' | 'not-ready';
  components: Array<{
    name: string;
    score: number;
    weight: number;
    status: 'ready' | 'needs-improvement' | 'not-ready';
    gapAnalysis: string;
  }>;
  gaps: string[]; // Array of gap descriptions
  preparationTimelineWeeks: number; // Estimated time to get ready
  nextSteps: string[]; // Specific preparation actions
}

Readiness levels:
- 80-100: Ready to proceed
- 70-79: Mostly ready - minor gaps
- 50-69: Needs significant preparation
- 0-49: Not ready - substantial work required

Include detailed gap analysis for each component and specific 
recommendations. Add TypeScript types and unit tests."
```

### Day 4: Strategic Fit Calculator

**Claude Code Prompt:**

```typescript
"Create a strategic fit calculator:

calculateStrategicFit(params: {
  isCoreCompetency: boolean;
  requiresProprietaryKnowledge: boolean;
  isCustomerFacing: boolean;
  drivesCompetitiveAdvantage: boolean;
  standardizationPossible: boolean;
  innovationScore: number; // 1-10
}): StrategicFitResult

Scoring (lower = better candidate for outsourcing):
- Core competency: +30 points
- Proprietary knowledge: +25 points
- Competitive advantage: +25 points
- Customer facing: +10 points
- Innovation requirement: +0 to +10 points
- Standardization possible: -15 points

Return:
{
  overallScore: number; // 0-100
  recommendation: string;
  analysis: string;
  coreCompetencyImpact: number;
  competitiveAdvantageImpact: number;
  standardizationPotential: number;
  detailedAssessment: {
    strategicImportance: 'low' | 'moderate' | 'high' | 'critical';
    outsourcingViability: 'good-candidate' | 'consider-carefully' | 'high-risk' | 'not-recommended';
    rationale: string;
  };
}

Strategic importance levels:
- 0-25: Low - good candidate for outsourcing
- 26-50: Moderate - consider carefully
- 51-75: High - outsource with caution
- 76-100: Critical - not recommended

Include detailed rationale and TypeScript types."
```

### Day 5: Recommendation Engine

**Claude Code Prompt:**

```typescript
"Create the final recommendation engine that combines all analyses:

generateRecommendation(params: {
  costBenefit: CostBenefitResult;
  riskAssessment: RiskAssessmentResult;
  readiness: ReadinessResult;
  strategicFit: StrategicFitResult;
  marketMaturityScore: number; // 1-10
}): FinalRecommendation

Component weights for overall score:
- Cost savings potential: 30%
- Risk (inverted): 25%
- Readiness: 20%
- Strategic fit (inverted): 15%
- Market maturity: 10%

Return:
{
  overallScore: number; // 0-100
  tier: 'STRONG_RECOMMEND' | 'RECOMMEND_WITH_CONDITIONS' | 
        'NEUTRAL' | 'NOT_RECOMMENDED' | 'STRONGLY_DISCOURAGE';
  confidence: 'high' | 'medium' | 'low';
  executiveSummary: string; // 2-3 paragraph summary
  keyFactors: {
    costSavings: number;
    risk: number;
    readiness: number;
    strategic: number;
    market: number;
  };
  strengths: string[]; // Top 3-5 strengths
  concerns: string[]; // Top 3-5 concerns
  conditions: string[]; // Required conditions (if applicable)
  nextSteps: string[]; // Recommended next actions (5-7 items)
  timeline: string; // Estimated timeline if proceeding
  criticalSuccessFactors: string[]; // Top 5 CSFs
}

Recommendation tiers:
- 80-100: STRONG_RECOMMEND
  • >20% savings, <50 risk, >80 readiness, non-core
- 60-79: RECOMMEND_WITH_CONDITIONS  
  • 10-20% savings, 50-70 risk, 70-79 readiness
- 40-59: NEUTRAL
  • Marginal business case, mixed signals
- 20-39: NOT_RECOMMENDED
  • <10% savings, >70 risk, <70 readiness
- 0-19: STRONGLY_DISCOURAGE
  • Critical function, severe risks, regulatory issues

Override rules:
- If strategic score ≥76: STRONGLY_DISCOURAGE
- If risk ≥76 AND readiness <50: STRONGLY_DISCOURAGE
- If risk ≥60: Add conditions or downgrade to RECOMMEND_WITH_CONDITIONS

Calculate confidence based on score variance across components.
Include comprehensive TypeScript types and unit tests."
```

### Weekend: Integration & Testing

**Claude Code Prompt:**

```typescript
"Create an integration test that:
1. Takes sample assessment data
2. Runs all calculators in sequence
3. Generates final recommendation
4. Validates the output

Test scenarios:
- Strong recommend case (high savings, low risk)
- Strongly discourage case (core competency)
- Conditional recommend (moderate savings, some risks)
- Edge cases (zero savings, extreme values)

Also create a test data generator for randomized testing."
```

### Deliverables

- [ ] All 5 calculators implemented
- [ ] Recommendation engine complete
- [ ] Unit tests for each calculator
- [ ] Integration tests
- [ ] TypeScript types documented
- [ ] Algorithm documentation with examples

### Success Criteria

✅ All calculations produce correct results  
✅ Edge cases handled properly  
✅ Tests pass (>90% coverage)  
✅ Performance is good (<100ms for full analysis)  
✅ Code is well-documented  

---

## Sprint 3: Results & Visualization (1 week) {#sprint-3}

### Goal
Build the results page with beautiful visualizations and comprehensive output.

### Day 1: Results Page Layout

**Claude Code Prompt:**

```typescript
"Create a results display page with these sections:

1. Recommendation Header
   - Large recommendation badge (color-coded by tier)
   - Overall score as circular progress indicator
   - Confidence level indicator
   - Executive summary (2-3 paragraphs)

2. Key Metrics Grid (4 cards)
   - Cost Savings % with 5-year total
   - Risk Score with level indicator
   - Readiness Score with level
   - Timeline estimate

3. Tabbed Content Area
   Tab 1: Financial Analysis
   Tab 2: Risk Assessment
   Tab 3: Readiness Evaluation
   Tab 4: Strategic Analysis
   Tab 5: Next Steps

4. Actions Bar
   - Download PDF Report
   - Export to Excel
   - Save Assessment
   - Start New Assessment
   - Edit Assessment

Use the design system components and make it responsive.
Mobile: Stack vertically
Tablet: 2-column grid
Desktop: Full layout with sidebar

Add proper TypeScript types for all props."
```

### Day 2: Financial Visualizations

**Claude Code Prompt:**

```typescript
"Create financial analysis charts using Recharts:

1. CostComparisonChart
   - Bar chart comparing current vs outsourced costs
   - Year-by-year breakdown (5 years)
   - Show cumulative savings
   - Animated on load
   - Responsive
   - Tooltips with formatted currency

2. BreakEvenTimeline
   - Line chart showing cumulative savings over time
   - Mark break-even point clearly
   - Reference line at $0
   - Monthly granularity for first 2 years
   - Tooltips with month and cumulative value

3. SavingsWaterfallChart
   - Waterfall chart showing:
     * Current costs (starting point)
     * Outsource costs (reduction)
     * Transition costs (increase)
     * Efficiency gains (reduction)
     * Final savings (result)
   - Color-coded (red for costs, green for savings)

4. ROI Gauge
   - Semi-circle gauge showing ROI percentage
   - Color-coded ranges:
     * 0-50%: Yellow
     * 50-100%: Light green
     * 100-200%: Green
     * 200%+: Dark green
   - Show payback period below gauge

All charts should:
- Be responsive (adapt to screen size)
- Have proper TypeScript types
- Include loading states
- Handle edge cases (negative savings, etc.)
- Use company brand colors from design system
- Be accessible (ARIA labels)"
```

### Day 3: Risk & Readiness Visualizations

**Claude Code Prompt:**

```typescript
"Create risk and readiness visualization components:

1. RiskRadarChart
   - Radar/spider chart with 5 axes (risk components)
   - Shows score for each component (0-100)
   - Filled area with opacity
   - Color-coded by severity
   - Tooltips on hover
   - Responsive

2. RiskHeatmap
   - Table showing risk components
   - Color-coded cells (green/yellow/orange/red)
   - Includes component name, score, weight, severity
   - Click to see mitigation recommendations
   - Mobile: Show as cards instead of table

3. ReadinessProgressBars
   - Stacked/grouped horizontal bars for 6 readiness components
   - Each bar shows score 0-100
   - Color-coded by status (ready/needs-improvement/not-ready)
   - Show weight percentage
   - Gap analysis on hover/click

4. ReadinessGauge
   - Overall readiness score as circular gauge
   - Show preparation timeline estimate
   - List top 3 gaps below gauge
   - Color-coded ranges:
     * 0-49: Red (not ready)
     * 50-69: Orange (needs prep)
     * 70-79: Yellow (mostly ready)
     * 80-100: Green (ready)

All visualizations should use Recharts or custom SVG, be fully 
responsive, and include proper TypeScript typing."
```

### Day 4: Interactive Features

**Claude Code Prompt:**

```typescript
"Add interactive features to the results page:

1. Scenario Comparison Widget
   - Quick toggle between Best/Likely/Worst case
   - Instantly updates all charts and numbers
   - Shows variance between scenarios
   - Highlight which scenario is currently displayed

2. Assumption Editor
   - Modal that lets user adjust key assumptions:
     * Outsource cost (± 20%)
     * Efficiency gains (0-30%)
     * Transition cost (± 30%)
     * Contract length (3-7 years)
   - Live recalculation as they adjust sliders
   - 'Reset to Original' button
   - 'Apply Changes' saves new scenario

3. Detail Panels (Expandable)
   - Click any metric to see detailed breakdown
   - Formulas shown with actual numbers plugged in
   - Sources/assumptions listed
   - Can expand/collapse sections
   - Smooth animations

4. Print-Friendly View
   - Toggle to print-optimized layout
   - Removes interactive elements
   - Optimizes charts for printing
   - Fits content to pages properly
   - Shows all expanded details

Implement with proper state management and TypeScript types."
```

### Day 5: Results Refinement & Mobile

**Claude Code Prompt:**

```typescript
"Optimize the results page for mobile:

1. Mobile Layout
   - Single column layout
   - Cards stack vertically
   - Tabs become accordion on mobile
   - Charts resize appropriately
   - Touch-friendly interactions (larger tap targets)

2. Performance Optimizations
   - Lazy load charts (only render when visible)
   - Memoize expensive calculations
   - Virtualize long lists
   - Optimize re-renders

3. UX Enhancements
   - Smooth scroll to sections
   - 'Back to top' button
   - Sticky recommendation header on scroll
   - Loading skeletons while calculating
   - Empty states if data missing
   - Error boundaries for chart failures

4. Accessibility
   - All charts have text alternatives
   - Keyboard navigation works
   - Focus management
   - ARIA labels comprehensive
   - Color contrast meets WCAG AA

Test on various screen sizes and devices."
```

### Weekend: Polish & Testing

**Manual Testing:**
- [ ] All charts render correctly
- [ ] Responsive on mobile/tablet/desktop
- [ ] Interactions work (hover, click, expand)
- [ ] Numbers match calculator outputs
- [ ] Loading states smooth
- [ ] No layout shifts
- [ ] Performance is good

### Deliverables

- [ ] Complete results page
- [ ] All visualizations implemented
- [ ] Interactive features working
- [ ] Mobile-optimized
- [ ] Accessible
- [ ] Performance-optimized

### Success Criteria

✅ Results display all analysis outputs  
✅ Charts are clear and informative  
✅ Mobile experience is excellent  
✅ Page loads in <2 seconds  
✅ Interactions are smooth  
✅ Accessible to screen readers  

---

## Sprint 4: Advanced Features (1 week) {#sprint-4}

### Goal
Add scenario modeling, export functionality, and helpful tools.

### Day 1-2: Export Functionality

**Claude Code Prompt:**

```typescript
"Create export functionality:

1. PDF Report Generator
   Use jsPDF and jspdf-autotable to generate a professional PDF report:
   
   - Cover page with:
     * Company name/logo placeholder
     * Assessment date
     * Function name
     * Recommendation tier (large, color-coded)
   
   - Executive Summary page
     * Overall score
     * Key metrics table
     * Recommendation summary
   
   - Financial Analysis (2-3 pages)
     * Cost comparison table
     * Charts as images
     * ROI breakdown
   
   - Risk Assessment (1-2 pages)
     * Risk components table
     * Heat map
     * Mitigation recommendations
   
   - Next Steps (1 page)
     * Prioritized action list
     * Timeline
     * Critical success factors
   
   Features:
   - Professional styling
   - Page numbers
   - Table of contents
   - Proper page breaks
   - Header/footer on each page
   - File named: ODA-Report-{FunctionName}-{Date}.pdf

2. Excel Export
   Use SheetJS (xlsx) to create multi-sheet workbook:
   
   Sheet 1: Summary
   - Key metrics
   - Recommendation
   
   Sheet 2: Financial Analysis
   - Year-by-year breakdown
   - Savings calculation
   
   Sheet 3: Risk Assessment
   - Component scores
   - Mitigation actions
   
   Sheet 4: Input Data
   - All user inputs for reference
   
   Features:
   - Formatted cells (currency, percentages)
   - Colored headers
   - Formulas for calculations
   - File named: ODA-Data-{FunctionName}-{Date}.xlsx

3. JSON Export/Import
   - Export full assessment as JSON
   - Import JSON to restore assessment
   - Validation on import
   - Error handling

Implement all with TypeScript types and error handling."
```

### Day 3: Scenario Modeling

**Claude Code Prompt:**

```typescript
"Create a scenario modeling feature:

1. ScenarioBuilder Component
   - Create up to 5 scenarios
   - Each scenario can modify:
     * Outsource cost (±30%)
     * Transition cost (±30%)
     * Efficiency gains (0-30%)
     * Contract length (3-7 years)
     * Volume change (±50%)
   
   - Preset scenarios:
     * Best Case (outsource -10%, efficiency +15%, transition -10%)
     * Most Likely (as entered)
     * Worst Case (outsource +10%, efficiency +5%, transition +20%)
     * Conservative (pessimistic assumptions)
     * Aggressive (optimistic assumptions)

2. ScenarioComparison Component
   - Side-by-side comparison table
   - Shows for each scenario:
     * Total 5-year savings
     * Break-even point
     * ROI
     * Overall score
     * Recommendation tier
   
   - Highlight best/worst scenarios
   - Sortable by metric
   - Export comparison to Excel

3. SensitivityAnalysis
   - Chart showing how recommendation changes as one variable varies
   - Select variable to test (outsource cost, efficiency, etc.)
   - Show range where recommendation flips
   - Identify 'tipping points'
   - Visual indicator of sensitivity

4. MonteCarloSimulation (Optional Advanced Feature)
   - Run 1000 simulations with random variations
   - Show distribution of outcomes
   - Probability of achieving certain savings
   - Confidence intervals

All components should:
- Recalculate in real-time
- Show loading states during calculation
- Be mobile-responsive
- Include TypeScript types
- Handle edge cases"
```

### Day 4: Benchmarking Data

**Claude Code Prompt:**

```typescript
"Create a benchmarking system with sample industry data:

1. BenchmarkData
   Create a static JSON file with benchmark data for common functions:
   
   Categories:
   - IT Infrastructure
   - HR/Payroll
   - Customer Service
   - Finance/Accounting
   - Procurement
   
   For each category, include:
   - Typical cost per transaction
   - Average error rate
   - Common SLA targets
   - Typical savings range (min-max %)
   - Market maturity score (1-10)
   - Number of established vendors
   - Common contract length
   
   Industries:
   - Financial Services
   - Healthcare
   - Retail
   - Manufacturing
   - Technology
   - (Generic/Cross-industry)

2. BenchmarkComparison Component
   - Show user's metrics vs industry benchmarks
   - Visual indicators (better/worse/average)
   - Variance percentages
   - Color-coded (green if better, red if worse)
   - Tooltips with explanations

3. BenchmarkInsights
   - Automatically generated insights:
     * "Your cost per transaction is 15% higher than industry average"
     * "Your error rate is significantly better than typical"
     * "This function category has high market maturity"
   
   - Recommendations based on benchmarks:
     * "Strong vendor market suggests good outsourcing opportunity"
     * "Your above-average costs indicate potential for savings"

Implement with TypeScript types and make extensible for adding 
more benchmark data later."
```

### Day 5: Helper Tools & UX Enhancements

**Claude Code Prompt:**

```typescript
"Add helpful tools and UX improvements:

1. Assessment Helper Wizard
   - Modal that guides user through data collection
   - Explains where to find each metric
   - Example values
   - Links to resources
   - 'I don't know this' option that uses industry averages

2. Quick Estimate Mode
   - Simplified 1-page form with just essential inputs
   - Runs quick analysis
   - Good for initial screening
   - Option to 'Expand to Full Assessment'

3. Glossary/Help System
   - Tooltip explanations for all terms
   - Expandable help sections
   - Video tutorials (placeholder for now)
   - FAQ section
   - Context-sensitive help

4. Comparison Tool
   - Load and compare multiple saved assessments
   - Side-by-side view
   - Identify which functions are best candidates
   - Portfolio-level view of all assessments

5. Sharing Features
   - Generate shareable link (readonly view)
   - Email report directly
   - Copy summary to clipboard
   - Social sharing (LinkedIn, etc.)

6. Keyboard Shortcuts
   - S: Save draft
   - E: Export
   - N: Next step
   - B: Back
   - ?: Show keyboard shortcuts

7. Progress Tracking
   - Show completion percentage
   - Estimate time remaining
   - Visual progress bar
   - 'You're 75% done!' encouragement

Implement with accessibility in mind and TypeScript types."
```

### Deliverables

- [ ] PDF and Excel export working
- [ ] JSON export/import functional
- [ ] Scenario modeling implemented
- [ ] Benchmark comparisons available
- [ ] Helper tools complete
- [ ] Keyboard shortcuts working

### Success Criteria

✅ Can export professional PDF report  
✅ Excel export includes all data  
✅ Scenarios calculate correctly  
✅ Benchmarks display properly  
✅ Helper tools are useful  
✅ All features work on mobile  

---

## Sprint 5: Polish & Deploy (3-5 days) {#sprint-5}

### Goal
Final polish, testing, optimization, and deployment.

### Day 1: Performance Optimization

**Claude Code Prompt:**

```typescript
"Optimize application performance:

1. Code Splitting
   - Lazy load routes
   - Lazy load heavy components (charts)
   - Dynamic imports for rarely-used features

2. Bundle Optimization
   - Analyze bundle size
   - Remove unused dependencies
   - Tree-shake unnecessary code
   - Minimize and compress

3. Caching Strategy
   - Cache calculation results
   - Memoize expensive functions
   - Cache benchmark data
   - Service worker for offline capability (optional)

4. Rendering Optimization
   - Use React.memo for expensive components
   - Optimize re-renders
   - Virtualize long lists
   - Debounce inputs

5. Asset Optimization
   - Compress images
   - Use WebP format
   - Lazy load images
   - Optimize SVGs

Run Lighthouse audit and achieve score >90 for performance."
```

### Day 2: Final Testing & Bug Fixes

**Testing Checklist:**

```markdown
Functionality:
- [ ] All calculators work correctly
- [ ] All forms validate properly
- [ ] Storage works (save/load)
- [ ] Export features work
- [ ] Scenario modeling works
- [ ] Charts render correctly
- [ ] Navigation works
- [ ] No console errors

Browser Compatibility:
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)
- [ ] Mobile Safari (iOS)
- [ ] Chrome Mobile (Android)

Responsive Design:
- [ ] Mobile (320px-480px)
- [ ] Tablet (481px-768px)
- [ ] Desktop (769px-1024px)
- [ ] Large Desktop (1025px+)

Accessibility:
- [ ] Keyboard navigation works
- [ ] Screen reader compatible
- [ ] Color contrast adequate
- [ ] ARIA labels present
- [ ] Focus indicators visible

Performance:
- [ ] Page load <3s
- [ ] Interactions smooth
- [ ] No jank or layout shifts
- [ ] Lighthouse score >90

Data Integrity:
- [ ] Calculations accurate
- [ ] Data persists correctly
- [ ] No data loss on refresh
- [ ] Export data complete
```

### Day 3: Documentation & Deployment

**Claude Code Prompt:**

```markdown
"Create comprehensive documentation:

1. README.md
   - Project overview
   - Features list
   - Technology stack
   - Getting started guide
   - Build instructions
   - Deployment instructions

2. USER_GUIDE.md
   - How to use the application
   - Step-by-step walkthrough
   - Tips and best practices
   - FAQ
   - Troubleshooting

3. DEVELOPER_GUIDE.md
   - Project structure
   - Component architecture
   - State management
   - Calculation algorithms
   - Adding new features
   - Testing guidelines

4. DEPLOYMENT.md
   - Deployment options
   - Configuration
   - Environment variables
   - Production optimizations

5. CODE_DOCUMENTATION
   - JSDoc comments on all functions
   - Type definitions documented
   - Complex algorithms explained
   - Examples provided

Make all documentation clear, comprehensive, and well-organized."
```

**Deployment Options:**

```yaml
Option 1: Vercel (Recommended)
  Pros:
    - Zero config for Vite/React
    - Automatic deployments from Git
    - Free tier generous
    - CDN included
    - HTTPS automatic
    - Custom domains easy
  
  Setup:
    1. Create Vercel account
    2. Import GitHub repo
    3. Deploy (automatic)
  
  Cost: Free for personal projects

Option 2: Netlify
  Similar to Vercel:
    - Easy deployment
    - Free tier
    - Form handling
    - Serverless functions
  
  Setup:
    1. Create Netlify account
    2. Connect GitHub
    3. Configure build settings
    4. Deploy
  
  Cost: Free for personal

Option 3: GitHub Pages
  Pros:
    - Completely free
    - Simple setup
    - Git-based deployment
  
  Cons:
    - No serverless functions
    - Static only
  
  Setup:
    1. Build project
    2. Push to gh-pages branch
    3. Enable in Settings
  
  Cost: Free

Option 4: AWS S3 + CloudFront
  Pros:
    - Very cheap
    - Highly scalable
    - Full control
  
  Cons:
    - More complex setup
    - Manual configuration
  
  Cost: ~$1-5/month

Recommendation: Start with Vercel, migrate to AWS if scaling needed.
```

### Day 4-5: Launch Preparation

**Pre-Launch Checklist:**

```markdown
Technical:
- [ ] All tests passing
- [ ] Performance optimized
- [ ] Security headers configured
- [ ] Analytics configured (Google Analytics/Plausible)
- [ ] Error tracking configured (Sentry)
- [ ] Monitoring configured
- [ ] Backups enabled
- [ ] SSL/HTTPS enabled
- [ ] Custom domain configured
- [ ] Favicon and meta tags set

Content:
- [ ] Privacy policy
- [ ] Terms of service
- [ ] About page
- [ ] Contact information
- [ ] Help documentation
- [ ] Example assessments

Marketing:
- [ ] Landing page copy
- [ ] Screenshots/demos
- [ ] Video walkthrough (optional)
- [ ] Social media images
- [ ] Launch announcement draft

Support:
- [ ] Feedback mechanism
- [ ] Bug report form
- [ ] Feature request process
- [ ] Email support configured
```

### Deliverables

- [ ] Application fully optimized
- [ ] All bugs fixed
- [ ] Documentation complete
- [ ] Deployed to production
- [ ] Monitoring configured
- [ ] Launch-ready

### Success Criteria

✅ Application deployed and accessible  
✅ No critical bugs  
✅ Performance score >90  
✅ Documentation comprehensive  
✅ Analytics tracking  
✅ Ready for users  

---

## Tech Stack {#tech-stack}

### Core Technologies

```yaml
Frontend Framework:
  Primary: React 18.2+
  Reason: Component-based, large ecosystem, Claude Code optimized
  Alternative: Vanilla JS + Web Components (simpler, no build step)

Language:
  Primary: TypeScript 5.0+
  Reason: Type safety, better IDE support, catches bugs early
  Alternative: JavaScript (faster prototyping)

Build Tool:
  Primary: Vite 5.0+
  Reason: Fast HMR, optimized builds, simple config
  Alternative: Create React App, Parcel

Styling:
  Primary: Tailwind CSS 3.4+
  Reason: Utility-first, rapid styling, consistent design
  Additions: Custom CSS for complex animations

Routing:
  Primary: React Router 6+
  Reason: Industry standard, declarative routing

State Management:
  Primary: React Context + Hooks
  Reason: Built-in, no extra dependencies, sufficient for this app
  Alternative: Zustand (if state gets complex)

Forms:
  Primary: React Hook Form (optional)
  Reason: Performant, less re-renders, easy validation
  Alternative: Controlled components with useState

Validation:
  Primary: Zod
  Reason: TypeScript-first, runtime validation
  Alternative: Yup, custom validators

Charts/Visualization:
  Primary: Recharts 2.10+
  Reason: React-based, composable, good docs
  Alternative: Chart.js, D3.js (more complex)

Storage:
  Primary: Browser localStorage
  Reason: Simple, persistent, no backend needed
  Optional: IndexedDB (for larger data)

PDF Generation:
  Primary: jsPDF + jspdf-autotable
  Reason: Client-side, no backend needed
  Alternative: react-pdf, pdfmake

Excel Export:
  Primary: SheetJS (xlsx)
  Reason: Full Excel support, client-side

Date Handling:
  Primary: date-fns
  Reason: Lightweight, tree-shakeable
  Alternative: Day.js, Luxon

Utilities:
  - lodash-es (only specific functions, tree-shaken)
  - clsx (conditional classes)
  - react-icons (icon library)

Testing:
  - Vitest (unit tests)
  - React Testing Library (component tests)
  - Playwright (e2e tests, optional)

Code Quality:
  - ESLint (linting)
  - Prettier (formatting)
  - TypeScript strict mode

Analytics (Optional):
  - Plausible (privacy-friendly)
  - Posthog (open source)
  - Google Analytics

Error Tracking (Optional):
  - Sentry (free tier)
  - LogRocket

Deployment:
  - Vercel (recommended)
  - Netlify
  - GitHub Pages
```

### Why No Backend Initially?

**Client-Side Only Advantages:**
1. ✅ Faster development (no API to build)
2. ✅ No hosting costs (static hosting free)
3. ✅ Better privacy (data stays in browser)
4. ✅ Works offline
5. ✅ Simpler deployment
6. ✅ Easier to understand and maintain

**When to Add Backend:**
- Multi-user collaboration needed
- Cloud storage/sync required
- Real-time benchmark updates needed
- User authentication required
- Analytics on user behavior needed
- API integrations needed

**Easy Backend Addition Later:**
- Firebase (easiest)
- Supabase (open source)
- PocketBase (minimal)
- Custom FastAPI backend

---

## Project Structure {#project-structure}

```
outsourcing-advisor/
├── public/
│   ├── favicon.ico
│   ├── logo.svg
│   └── sample-data/
│       └── benchmarks.json
│
├── src/
│   ├── components/
│   │   ├── ui/                    # Design system components
│   │   │   ├── Button.tsx
│   │   │   ├── Input.tsx
│   │   │   ├── Card.tsx
│   │   │   ├── Badge.tsx
│   │   │   ├── Modal.tsx
│   │   │   ├── ProgressBar.tsx
│   │   │   └── Tooltip.tsx
│   │   │
│   │   ├── forms/                 # Form components
│   │   │   ├── CurrencyInput.tsx
│   │   │   ├── PercentageInput.tsx
│   │   │   ├── SliderWithLabels.tsx
│   │   │   ├── YesNoToggle.tsx
│   │   │   └── FormStep.tsx
│   │   │
│   │   ├── charts/                # Visualization components
│   │   │   ├── CostComparisonChart.tsx
│   │   │   ├── BreakEvenTimeline.tsx
│   │   │   ├── RiskRadarChart.tsx
│   │   │   ├── ReadinessGauge.tsx
│   │   │   ├── ROIGauge.tsx
│   │   │   └── SensitivityChart.tsx
│   │   │
│   │   ├── assessment/            # Assessment-specific components
│   │   │   ├── AssessmentWizard.tsx
│   │   │   ├── StepFunction.tsx
│   │   │   ├── StepFinancial.tsx
│   │   │   ├── StepPerformance.tsx
│   │   │   ├── StepRisk.tsx
│   │   │   ├── StepReadiness.tsx
│   │   │   ├── StepStrategic.tsx
│   │   │   └── StepReview.tsx
│   │   │
│   │   ├── results/               # Results display components
│   │   │   ├── RecommendationHeader.tsx
│   │   │   ├── KeyMetricsGrid.tsx
│   │   │   ├── FinancialAnalysis.tsx
│   │   │   ├── RiskAssessment.tsx
│   │   │   ├── ReadinessEvaluation.tsx
│   │   │   ├── StrategicAnalysis.tsx
│   │   │   ├── NextSteps.tsx
│   │   │   └── ActionBar.tsx
│   │   │
│   │   ├── scenarios/             # Scenario modeling components
│   │   │   ├── ScenarioBuilder.tsx
│   │   │   ├── ScenarioComparison.tsx
│   │   │   └── SensitivityAnalysis.tsx
│   │   │
│   │   └── layout/                # Layout components
│   │       ├── Header.tsx
│   │       ├── Footer.tsx
│   │       ├── Navigation.tsx
│   │       └── MobileMenu.tsx
│   │
│   ├── pages/
│   │   ├── Home.tsx               # Landing page
│   │   ├── Assessment.tsx         # Assessment wizard page
│   │   ├── Results.tsx            # Results display page
│   │   ├── SavedAssessments.tsx   # List of saved assessments
│   │   ├── About.tsx              # About page
│   │   └── Help.tsx               # Help/documentation page
│   │
│   ├── services/
│   │   ├── calculators/
│   │   │   ├── costBenefit.ts     # Cost-benefit calculator
│   │   │   ├── riskAssessment.ts  # Risk assessment calculator
│   │   │   ├── readiness.ts       # Readiness calculator
│   │   │   ├── strategicFit.ts    # Strategic fit calculator
│   │   │   └── recommendation.ts  # Final recommendation engine
│   │   │
│   │   ├── storage/
│   │   │   ├── localStorage.ts    # localStorage wrapper
│   │   │   └── exporters.ts       # PDF/Excel export functions
│   │   │
│   │   └── benchmarks/
│   │       └── benchmarkData.ts   # Benchmark data service
│   │
│   ├── types/
│   │   ├── assessment.ts          # Assessment data types
│   │   ├── results.ts             # Analysis results types
│   │   ├── scenarios.ts           # Scenario types
│   │   └── benchmarks.ts          # Benchmark types
│   │
│   ├── utils/
│   │   ├── formatters.ts          # Currency, percentage formatters
│   │   ├── validators.ts          # Input validation functions
│   │   ├── calculations.ts        # Helper calculation functions
│   │   └── constants.ts           # App constants
│   │
│   ├── hooks/
│   │   ├── useLocalStorage.ts     # localStorage hook
│   │   ├── useAssessment.ts       # Assessment state hook
│   │   ├── useAnalysis.ts         # Analysis results hook
│   │   └── useScenarios.ts        # Scenarios hook
│   │
│   ├── styles/
│   │   ├── globals.css            # Global styles
│   │   └── tailwind.css           # Tailwind directives
│   │
│   ├── App.tsx                    # Main app component
│   ├── main.tsx                   # Entry point
│   └── vite-env.d.ts              # Vite type definitions
│
├── tests/
│   ├── unit/
│   │   ├── calculators.test.ts
│   │   ├── storage.test.ts
│   │   └── utils.test.ts
│   │
│   ├── integration/
│   │   ├── assessment-flow.test.tsx
│   │   └── results-display.test.tsx
│   │
│   └── e2e/
│       └── complete-workflow.spec.ts
│
├── .env.example                   # Environment variables template
├── .eslintrc.json                 # ESLint config
├── .prettierrc                    # Prettier config
├── index.html                     # HTML entry point
├── package.json
├── tsconfig.json                  # TypeScript config
├── tailwind.config.js             # Tailwind config
├── vite.config.ts                 # Vite config
├── vitest.config.ts               # Vitest config
├── README.md
├── USER_GUIDE.md
└── DEVELOPER_GUIDE.md
```

---

## Claude Code Workflow {#claude-workflow}

### Optimal Claude Code Usage Patterns

#### 1. Start with Types First

**Best Practice:**
```typescript
// STEP 1: Define types with Claude
"Create comprehensive TypeScript types for our assessment data model.
Include JSDoc comments explaining each field."

// STEP 2: Use types to guide implementation
"Now create the cost-benefit calculator that takes CostBenefitInput
and returns CostBenefitResult."
```

**Why:** Types provide guardrails for Claude and catch errors early.

#### 2. Build Components Iteratively

**Iterative Approach:**
```typescript
// ITERATION 1: Basic structure
"Create a basic CurrencyInput component with just value and onChange"

// ITERATION 2: Add features
"Add formatting as user types, validation, and error messages"

// ITERATION 3: Polish
"Add keyboard shortcuts, accessibility, and loading states"
```

**Why:** Easier to review and test incrementally.

#### 3. Request Tests Alongside Code

**Good Prompt:**
```typescript
"Create the risk assessment calculator with:
1. The main function
2. TypeScript types
3. JSDoc documentation
4. Unit tests for common scenarios
5. Unit tests for edge cases"
```

**Why:** Claude writes better tests when asked upfront.

#### 4. Use Concrete Examples

**Vague (Less Effective):**
```
"Create a slider component"
```

**Specific (More Effective):**
```typescript
"Create a slider component for risk assessment (1-10 scale) that:
- Shows current value prominently
- Has descriptive labels (1-3: Low Risk, 4-6: Medium, 7-8: High, 9-10: Critical)
- Updates in real-time as user drags
- Works on mobile (larger touch targets)
- Shows tooltip on hover with description
- Is keyboard accessible (arrow keys)
Example: When value is 7, show 'High Risk - Significant operational impact'"
```

**Why:** Specific examples prevent ambiguity and reduce iterations.

#### 5. Ask for Multiple Options

**Good Prompt:**
```typescript
"Give me 3 different approaches for state management:
1. Using React Context
2. Using Zustand
3. Using plain useState

For each, show:
- Pros/cons for this specific use case
- Code example
- Complexity level
- Recommendation"
```

**Why:** Claude can evaluate trade-offs and help you decide.

#### 6. Request Explanations

**Good Prompt:**
```typescript
"Create the ROI calculation function. Include:
1. The code
2. Step-by-step explanation of the formula
3. Example calculation with actual numbers
4. Edge cases and how they're handled"
```

**Why:** You'll understand and maintain the code better.

### Common Claude Code Patterns for This Project

#### Pattern 1: Component + Types + Tests

```typescript
// Request everything together
"Create a ReadinessGauge component that:
- Shows 0-100 score as circular gauge
- Color-coded (red/yellow/green based on score)
- Displays readiness level text below
- Responsive and accessible

Include:
- TypeScript component with proper typing
- Props interface
- Unit tests (RTL)
- Storybook story (optional)"
```

#### Pattern 2: Service Layer Development

```typescript
// Step-by-step service creation
"Create a storage service for assessments:

STEP 1: Interface definition
- Define the methods we need
- Type all inputs/outputs

STEP 2: Implementation
- Use localStorage
- Handle errors gracefully
- Add logging

STEP 3: Tests
- Test save/load/delete
- Test error cases
- Test with mock localStorage"
```

#### Pattern 3: Feature with Multiple Sub-Components

```typescript
// Break down complex features
"I want to build the scenario modeling feature. Let's start with:

Phase 1: Data structure
- Create Scenario type
- Create ScenarioInput type
- Create ScenarioResult type

Phase 2: Logic
- Scenario calculator function
- Comparison function

Phase 3: UI Components
- ScenarioBuilder (form to create scenarios)
- ScenarioComparison (table showing results)
- ScenarioChart (visualization)

Let's do Phase 1 first."
```

### Debugging with Claude Code

#### When You Get Stuck

**Effective Debug Prompts:**

```typescript
// Share the error
"I'm getting this error: [paste error]
Here's the relevant code: [paste code]
What's wrong and how do I fix it?"

// Ask for explanation
"This code works but I don't understand how. Can you explain
line by line what's happening and why?"

// Request refactoring
"This code is messy. Can you refactor it to be:
- More readable
- Better typed
- More performant
- Better tested"
```

### Code Review with Claude

```typescript
// Ask Claude to review
"Review this component for:
1. TypeScript best practices
2. React best practices
3. Accessibility issues
4. Performance concerns
5. Missing error handling
6. Unclear naming

[paste code]

Be specific about what to improve."
```

### Documentation with Claude

```typescript
// Generate docs
"Create comprehensive documentation for this module:
- Overview of what it does
- API reference for all functions
- Usage examples
- Edge cases to be aware of
- Related modules

[paste code]"
```

---

## Testing Strategy {#testing}

### Testing Philosophy

**Test Pyramid:**
```
         /\
        /E2E\          ← 5% (critical user flows)
       /------\
      / Integ \       ← 15% (component integration)
     /----------\
    /   Unit     \    ← 80% (logic, functions, utils)
   /--------------\
```

### Unit Testing

**What to Test:**
- ✅ All calculator functions
- ✅ Utility functions
- ✅ Validators
- ✅ Formatters
- ✅ Complex algorithms

**What Not to Test:**
- ❌ Third-party libraries
- ❌ Simple getters/setters
- ❌ Trivial logic

**Example Test with Claude Code:**

```typescript
// Claude Prompt:
"Write comprehensive unit tests for the cost-benefit calculator.
Test scenarios:
1. Normal case with positive savings
2. Negative savings (outsourcing more expensive)
3. Zero transition cost
4. Very long contract (10+ years)
5. Extreme values
6. Zero/null inputs (error handling)

Use Vitest and aim for 100% coverage of this function."

// Claude will generate something like:
import { describe, it, expect } from 'vitest';
import { calculateCostBenefit } from './costBenefit';

describe('calculateCostBenefit', () => {
  it('calculates positive savings correctly', () => {
    const result = calculateCostBenefit({
      currentAnnualCost: 1000000,
      outsourceAnnualCost: 700000,
      transitionCost: 100000,
      contractYears: 5,
      volumeChangePercent: 0,
      efficiencyGainPercent: 0
    });
    
    expect(result.totalSavings).toBe(1400000);
    expect(result.savingsPercentage).toBe(28);
    expect(result.breakEvenMonths).toBeLessThan(12);
  });
  
  // ... more tests
});
```

### Component Testing

**What to Test:**
- ✅ Renders correctly
- ✅ Props work as expected
- ✅ User interactions (click, type, etc.)
- ✅ Conditional rendering
- ✅ Error states

**Example with Claude Code:**

```typescript
// Claude Prompt:
"Write React Testing Library tests for the CurrencyInput component.
Test:
1. Renders with initial value
2. Formats currency as user types
3. Shows validation error when invalid
4. Calls onChange with correct value
5. Handles edge cases (very large numbers)
6. Works with keyboard input
7. Is accessible (ARIA labels)"

// Claude generates comprehensive tests
```

### Integration Testing

**What to Test:**
- ✅ Multi-step flows
- ✅ Data flow between components
- ✅ State management
- ✅ LocalStorage integration

**Example:**

```typescript
// Claude Prompt:
"Write integration tests for the complete assessment flow:
1. User fills out all 6 steps
2. Data saves to localStorage
3. User can navigate back/forward
4. Validation prevents progression
5. Final submission works
6. Results page loads with correct data"
```

### E2E Testing (Optional for MVP)

**If Time Permits:**

```typescript
// Claude Prompt:
"Write Playwright E2E test for happy path:
1. Visit homepage
2. Click 'Start Assessment'
3. Complete all steps with valid data
4. Submit assessment
5. Verify results page shows correct recommendation
6. Export PDF successfully
7. Save assessment
8. Load saved assessment and verify data persists"
```

### Test Coverage Goals

```yaml
Target Coverage:
  Overall: 80%+
  Calculator Functions: 100%
  Components: 70%+
  Utils: 90%+
  
Critical Paths:
  - Assessment submission: 100%
  - Calculation accuracy: 100%
  - Data persistence: 100%
  - Export functionality: 90%+
```

### Testing Commands

```json
{
  "scripts": {
    "test": "vitest",
    "test:ui": "vitest --ui",
    "test:coverage": "vitest --coverage",
    "test:watch": "vitest --watch",
    "test:e2e": "playwright test",
    "test:e2e:ui": "playwright test --ui"
  }
}
```

---

## Deployment Options {#deployment}

### Option 1: Vercel (Recommended)

**Why Vercel:**
- ⚡ Zero-config for Vite
- 🔄 Automatic deployments from Git
- 🌍 Global CDN
- 🔒 Automatic HTTPS
- 💰 Generous free tier
- 📊 Built-in analytics
- 🎯 Custom domains easy

**Deployment Steps:**

```bash
# 1. Build your project
npm run build

# 2. Install Vercel CLI
npm i -g vercel

# 3. Deploy
vercel

# Or connect GitHub repo via Vercel dashboard
# Automatic deployments on every push to main
```

**Vercel Configuration:**

```json
// vercel.json (optional, auto-detected for Vite)
{
  "buildCommand": "npm run build",
  "outputDirectory": "dist",
  "devCommand": "npm run dev",
  "framework": "vite"
}
```

**Environment Variables:**
```bash
# Set in Vercel dashboard
VITE_APP_NAME=Outsourcing Decision Advisor
VITE_ANALYTICS_ID=your-analytics-id
```

**Custom Domain:**
1. Buy domain (Namecheap, Google Domains)
2. Add to Vercel project
3. Update DNS records (automatic instructions)
4. SSL auto-configured

**Cost:** Free for personal projects

---

### Option 2: Netlify

**Why Netlify:**
- Similar to Vercel
- Great DX
- Form handling built-in
- Serverless functions
- Split testing

**Deployment Steps:**

```bash
# 1. Build project
npm run build

# 2. Install Netlify CLI
npm i -g netlify-cli

# 3. Deploy
netlify deploy --prod

# Or drag-and-drop dist/ folder to Netlify dashboard
```

**netlify.toml:**

```toml
[build]
  command = "npm run build"
  publish = "dist"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

**Cost:** Free for personal projects

---

### Option 3: GitHub Pages

**Why GitHub Pages:**
- Completely free
- Simple
- No extra account needed

**Deployment Steps:**

```bash
# 1. Install gh-pages
npm i -D gh-pages

# 2. Add to package.json
{
  "scripts": {
    "deploy": "npm run build && gh-pages -d dist"
  }
}

# 3. Deploy
npm run deploy
```

**Update vite.config.ts:**

```typescript
export default defineConfig({
  base: '/outsourcing-advisor/', // Your repo name
  plugins: [react()],
})
```

**Enable in GitHub:**
1. Go to repo Settings
2. Pages section
3. Source: gh-pages branch
4. Save

**Cost:** Free

---

### Option 4: Self-Hosted (Advanced)

**Simple Server:**

```bash
# Install serve globally
npm i -g serve

# Build and serve
npm run build
serve -s dist -p 3000
```

**With Docker:**

```dockerfile
# Dockerfile
FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

```bash
# Build and run
docker build -t oda-app .
docker run -p 80:80 oda-app
```

**Cost:** Server hosting ($5-20/month)

---

### Deployment Checklist

```markdown
Pre-Deployment:
- [ ] All tests passing
- [ ] No console errors
- [ ] Build succeeds locally
- [ ] Environment variables set
- [ ] Analytics configured
- [ ] Error tracking configured
- [ ] Performance optimized
- [ ] Security headers configured

Post-Deployment:
- [ ] Site accessible
- [ ] All pages load
- [ ] Forms work
- [ ] LocalStorage works
- [ ] Export functions work
- [ ] Mobile responsive
- [ ] SSL/HTTPS working
- [ ] Custom domain (if applicable)
- [ ] Analytics tracking
- [ ] No broken links

Monitoring:
- [ ] Set up uptime monitoring
- [ ] Configure error alerts
- [ ] Check performance metrics
- [ ] Monitor user analytics
```

---

## Key Metrics & Success Criteria

### Application Metrics

```yaml
Performance:
  Page Load Time: <2 seconds
  Time to Interactive: <3 seconds
  First Contentful Paint: <1 second
  Lighthouse Score: >90
  
Functionality:
  Calculation Accuracy: 100%
  Form Completion Rate: >80%
  Data Persistence: 100%
  Export Success Rate: >95%
  
User Experience:
  Mobile Usability: Excellent
  Accessibility Score (WAVE): 0 errors
  Browser Compatibility: 100% (modern browsers)
  Error Rate: <1%
  
Code Quality:
  TypeScript Coverage: 100%
  Test Coverage: >80%
  ESLint Warnings: 0
  Build Success Rate: 100%
```

### Development Velocity Metrics

```yaml
Sprint Velocity:
  Sprint 0: 5 days
  Sprint 1: 7 days
  Sprint 2: 7 days
  Sprint 3: 7 days
  Sprint 4: 7 days
  Sprint 5: 5 days
  Total: 38 days (~6 weeks)

Lines of Code (Estimated):
  Components: ~3,000 LOC
  Services/Logic: ~2,000 LOC
  Types: ~500 LOC
  Tests: ~2,500 LOC
  Total: ~8,000 LOC
  
  (Claude Code can generate ~500-1000 LOC/day with good prompts)
```

---

## Conclusion

This plan optimizes for:
- ✅ **Rapid development** with Claude Code
- ✅ **Modern, maintainable** codebase
- ✅ **Browser-first** architecture
- ✅ **Iterative delivery** of working features
- ✅ **Production-ready** outcome

### Key Advantages of This Approach

1. **Fast Time-to-Value:** Working prototype in 2 weeks
2. **Low Cost:** No backend hosting, free deployment
3. **Easy Maintenance:** Simple architecture, well-documented
4. **Scalable:** Easy to add backend later if needed
5. **AI-Optimized:** Designed for Claude Code strengths

### Next Steps to Start

1. ✅ **Day 1:** Initialize project with Claude Code
2. ✅ **Day 2:** Set up types and design system
3. ✅ **Week 1:** Build assessment flow
4. ✅ **Week 2:** Implement calculators
5. ✅ **Week 3:** Create visualizations
6. ✅ **Week 4:** Add advanced features
7. ✅ **Week 5:** Test and deploy

### Support & Resources

**Claude Code Prompting Tips:**
- Be specific about requirements
- Request tests alongside code
- Ask for multiple options
- Iterate incrementally
- Request explanations

**Recommended Learning:**
- React docs: react.dev
- TypeScript handbook: typescriptlang.org
- Tailwind docs: tailwindcss.com
- Vite guide: vitejs.dev

---

**Ready to start building?**

Begin with:
```bash
npm create vite@latest outsourcing-advisor -- --template react-ts
cd outsourcing-advisor
npm install
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

Then share this plan with Claude Code and start with Sprint 0!

---

**Document Version:** 1.0  
**Last Updated:** February 15, 2026  
**Optimized For:** Claude Code Development  
**Estimated Timeline:** 4-6 weeks  
**Difficulty:** Intermediate  
**Prerequisites:** Basic React knowledge, TypeScript familiarity
"""

with open('oda-claude-code-development-plan.md', 'w', encoding='utf-8') as f:
    f.write(content)

print("✅ Development plan created successfully!")
print(f"📄 File size: {len(content):,} characters")
print(f"📍 Location: /mnt/user-data/outputs/oda-claude-code-development-plan.md")
