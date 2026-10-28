# TestForge AI

TestForge AI is a lightweight web application for drafting and managing software test cases. It provides a simple place for QA engineers, developers, and product teams to turn a feature name into a starting set of test scenarios, then review and maintain those cases in a browser.

## Project Overview

Writing test cases manually from feature requirements can be repetitive and time-consuming. TestForge AI helps speed up that first step by generating a small set of common scenarios and expected results, including valid input, missing fields, invalid formats, service availability, and mobile layout.

The application is intended as a simple test-case drafting tool and workshop project. Its current generator uses predefined templates in the browser; it does not send the user story to an AI model or external API. Generated cases are starting points and should be adapted to the feature’s actual requirements.

## Key Features

- **Generate test cases:** Enter a feature name and user story to create five template-based test cases. Both fields are required; the current templates use the feature name to compose the scenarios and expected results.
- **Create and read cases:** Add cases manually and review them in a table with a generated test ID, scenario, expected result, and status.
- **Update cases:** Edit a case’s scenario, expected result, and status, or change its status directly in the table.
- **Delete cases:** Remove a single case or clear the complete list.
- **Filter by status:** Use the All, Passed, and Pending tabs to filter the table. Each tab displays a live count. Individual cases can also have a Failed status, although there is no Failed filter tab or counter.
- **Validate and escape input:** Required fields are checked, and displayed scenario and expected-result text is HTML-escaped.
- **Responsive interface:** The table can scroll horizontally on narrow screens.

## Technology Stack

- **HTML:** A single `index.html` file contains the interface and application code.
- **Tailwind CSS:** Styling is loaded from the Tailwind CSS CDN.
- **Pure JavaScript:** Application state, template-based generation, CRUD operations, filtering, and rendering are implemented with browser JavaScript without a framework.

## How It Works

### Application flow

1. The user enters a feature name and user story.
2. JavaScript checks that both fields are present.
3. The generator applies five predefined templates to the feature name and adds the resulting cases to an in-memory array with Pending status.
4. The table is rendered from that array. Status filters and counters are recalculated whenever the data changes.
5. Users can add, edit, update the status of, or delete cases through the interface.

The user story is currently required as input but is not used to customize the predefined scenarios. The application does not persist data: cases are lost when the page is refreshed or closed.

### Three-layer prompt architecture

The project was developed with an AI-assisted, three-layer prompt structure:

1. **Role and context:** Set the AI’s role and established the project context: a browser-based test-case generator using HTML, Tailwind CSS via CDN, and plain JavaScript.
2. **Task and requirements:** Defined the input form, generation flow, test-case table, CRUD operations, statuses, and status-filter tabs with counters.
3. **Constraints and output:** Specified a responsive, straightforward implementation in a single `index.html` file without a frontend framework.

These prompt layers describe the AI-assisted development process; they are not runtime components of the application. Test-case generation in the current app is template-based and does not require an AI service.

## Running the Application

1. Clone or download the project.
2. Open `index.html` in a modern web browser.

No build step or package installation is required. An internet connection is needed to load Tailwind CSS from its CDN.

## Future Enhancements

- Integrate an AI or LLM API to generate scenarios from the full user story and acceptance criteria.
- Persist test cases across page reloads, for example with browser storage or a backend service.
- Export test cases to CSV, Excel-compatible formats, or PDF.
- Add project and feature organization so cases can be managed across multiple projects.
- Add a Failed status filter and counter, and support additional statuses or workflow customization.
- Integrate with project and issue-management tools such as Jira or GitHub Issues.
- Generate starter automated test scripts for tools such as Playwright or Cypress.
