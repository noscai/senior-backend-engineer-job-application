### Task Description for Software Engineer Applicant

#### Overview
You will be tasked with setting up a local instance of MedusaJS with a PostgreSQL database and developing a custom plugin named `medusa-plugin-anamnesis` for a digital anamnesis form system for ClinicOS. This system will enable the creation and management of anamnesis forms, sections, and questions, which will be displayed to patients on the frontend and store their responses in the backend.

#### Part 1: Setting Up MedusaJS Locally
1. **Install MedusaJS Backend**
   - Follow the official MedusaJS documentation to install MedusaJS locally with a PostgreSQL database.
   - Documentation: [MedusaJS Installation](https://docs.medusajs.com/development/backend/install)

#### Part 2: Develop `medusa-plugin-anamnesis`
2. **Create the Plugin**
   - Follow the MedusaJS plugin creation guide to scaffold a new plugin named `medusa-plugin-anamnesis`.
   - Documentation: [Creating Plugins in MedusaJS](https://docs.medusajs.com/development/plugins/create)

3. **Plugin Requirements**
   - The plugin should allow for the creation of digital anamnesis forms.
   - An anamnesis form will have multiple sections (`anamnesis_sections`), and each section will have multiple questions (`anamnesis_questions`).

4. **Data Models and Relationships**
   - **AnamnesisForm**
     - `id`
     - `title`
     - `description`
     - `created_at`
     - `updated_at`
   - **AnamnesisSection**
     - `id`
     - `form_id` (foreign key to AnamnesisForm)
     - `title`
     - `description`
     - `order` (integer to maintain section order)
     - `created_at`
     - `updated_at`
   - **AnamnesisQuestion**
     - `id`
     - `section_id` (foreign key to AnamnesisSection)
     - `question_text`
     - `question_type` (enum: short_answer, long_answer, date, date_time, time, multiple_choice, select)
     - `options` (JSONB, used for multiple_choice and select types)
     - `created_at`
     - `updated_at`

5. **Handling Responses**
   - Create a model to store patient responses with the following fields:
     - **AnamnesisResponse**
       - `id`
       - `customer_id`
       - `order_id`
       - `form_id` (foreign key to AnamnesisForm)
       - `responses` (JSONB: [{question_id, answer}, ...])
       - `created_at`
       - `updated_at`

6. **API Endpoints**
   - Create both `/admin` and `/store` endpoints for managing and retrieving forms.
     - `/admin` Endpoints:
       - Create a new anamnesis form
       - Add sections to a form
       - Add questions to a section
       - Retrieve a form template for management
     - `/store` Endpoints:
       - Retrieve a form template for patient use
       - Submit patient responses

#### Part 3: Internationalization (Extra Task)
7. **Internationalization**
   - Implement internationalization support for anamnesis forms, sections, and questions.
   - Design your tables/models to include a `language_code` field for each text field or create separate tables to manage translations.
   - Ensure the frontend can request forms in the desired language.

#### Submission
- Provide a GitHub repository link with your MedusaJS project and `medusa-plugin-anamnesis` plugin.
- Include a README.md with instructions on how to set up and run your project, and how to test the plugin functionality.
- Document your design decisions, especially for the data models and internationalization approach.

### Evaluation Criteria
- Correctness: The plugin works as intended, with proper CRUD operations for forms, sections, and questions.
- Code Quality: Clean, readable, and maintainable code.
- Design: Efficient and scalable data model design.
- API Endpoints: Proper implementation of both `/admin` and `/store` endpoints.
- Extra Task: Implementation of internationalization support.
- Documentation: Clear instructions and well-documented code.

Good luck, and we look forward to reviewing your submission!
