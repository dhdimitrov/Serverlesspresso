# Serverlesspresso Workshop

A serverless coffee ordering application demonstrating event-driven architecture patterns using AWS services.

## Overview

Serverlesspresso is a complete serverless application that simulates a coffee shop ordering system with real-time updates, order processing workflows, and multi-channel event distribution.

## Architecture

The application uses an event-driven architecture with the following key components:

- **EventBridge** - Central event bus for application events
- **AppSync Events API** - Real-time GraphQL subscriptions
- **Step Functions** - Order processing workflow orchestration
- **Lambda Functions** - Event publishers and business logic
- **Cognito** - User authentication and management
- **DynamoDB** - Data persistence (in separate stacks)

## CloudFormation Template

The `workshop-self-service.yaml` template creates the core infrastructure:

### Resources Created:
- **ServerlesspressoEventBus** - Custom EventBridge event bus
- **AppSyncEventsApi** - Real-time messaging API
- **EventApiNameSpace** - AppSync channel namespace
- **PublisherFunctionUser/Config/Admin** - Lambda event publishers
- **UserPool & UserPoolClient** - Cognito authentication
- **SSM Parameters** - Configuration storage for cross-stack references

### Event Flow:
1. Events → EventBridge → Lambda Publishers → AppSync Channels
2. Real-time updates distributed to user, admin, and config channels
3. Role-based event filtering for different user types

## OrderProcessorWorkflow Step Function

The Step Functions workflow orchestrates the complete order processing pipeline:

- **Order Validation** - Validates order details and inventory
- **Payment Processing** - Handles payment authorization
- **Order Fulfillment** - Manages order preparation states
- **Notification Dispatch** - Sends real-time updates to customers
- **Error Handling** - Manages failures and retries

The workflow ensures reliable order processing with proper error handling and state management.

## Resources

- **📊 Presentation with Video Examples**: [Google Slides](https://docs.google.com/presentation/d/1qb1ofxJz_yd7UmhHos3cPPkjZHvlIgAn/edit?slide=id.g36cde9e505e_0_19#slide=id.g36cde9e505e_0_19)
- **🎯 Official Workshop**: [AWS Workshop Studio](https://catalog.workshops.aws/serverlesspresso/en-US)

## Key Learning Outcomes

- Event-driven serverless architecture patterns
- Real-time messaging with AppSync Events
- Step Functions workflow orchestration
- Multi-stack CloudFormation deployments
- Serverless authentication with Cognito
- Cross-service communication via EventBridge
