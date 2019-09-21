# FRANCE
France Multi Location V!
openapi: 3.0.0
info:
  version: '0.0.1'
  title: 'ORDS generated API for pcs_api'
servers:
  - url: https://agkqslkkaj91pge-dbeurprod.adb.eu-frankfurt-1.oraclecloudapps.com/ords/spartan/api
security:
  - bearerAuth: [] 
paths: 
  /route/:
    get:
      tags: 
        - Route
      responses:
        200:
          description: A list of all the Routes
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Route'
        400:
          $ref: '#/components/responses/UnauthorizedError'
    post:
      tags: 
        - Route
      requestBody:
        $ref: '#/components/requestBodies/PAYLOAD4'
      responses:
        200:
          description: output of the endpoint Route
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Route'
        400:
          $ref: '#/components/responses/UnauthorizedError'
  /route/schedule/{date}:
    get:
      tags: 
        - Route Schedule
      responses:
        200:
          description: A list of all PET details by Date & RoutCode Wise
          content:
            application/json:
              schema:
                type: object
                properties: {}
        400:
          $ref: '#/components/responses/UnauthorizedError'
      parameters:
        - name: date
          in: path
          required: true
          description: A list of Route details by Date & RoutCode Wise. Date format should be (YYYY-MM-DD)
          schema:
            type: string
  /route/schedule/pending:
    get:
      tags: 
        - Route Schedule
      responses:
        200:
          description: A list of all the Pending Pickup & Delivery pet details.
          content:
            application/json:
              schema:
                type: object
                properties: {}
        400:
          $ref: '#/components/responses/UnauthorizedError'
components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT
      description: Bearer Token supplied by the /AUTH call
  parameters:
    schedule_id:
        in: path
        name: schedule_id
        required: true
        schema:
          type: string
          maximum: 10
        description: The ID of the pet
  responses:
    UnauthorizedError:
      description: Access token is missing or invalid
  requestBodies:
    PAYLOAD4:
      content:
        application/json:
          schema:
            $ref: "#/components/schemas/Route"
      required: true
  schemas:
    Route:
      properties: 
              ROUTE_CODE: 
                type: "string"
              DESCRIPTION: 
                type: "string"
              SPEC_COMMENTS: 
                type: "string"
              CREATE_DTTM: 
                type: "string"
              CREATE_USER: 
                type: "string"
              UPDATE_DTTM: 
                type: "string"
              UPDATE_USER: 
                type: "string"
              DEFAULT_FLAG: 
                type: "string"
              SAP_CODE: 
                type: "string"
              UNASSIGNED_FLAG: 
                type: "string"
