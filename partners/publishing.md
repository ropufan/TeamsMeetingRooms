# Publishing a Consulting Service in Partner Center

To begin, you will navigate to the [Partner Center](https://partner.microsoft.com/en-us/dashboard/home), specifically the [Commercial Marketplace](https://partner.microsoft.com/en-us/dashboard/commercial-marketplace/overview) section. Within this module of Partner Center, you gain access to essential features for creating and managing your offerings intended for publication on the Microsoft Commercial Marketplace. There are [multiple types of offerings](https://learn.microsoft.com/en-us/partner-center/marketplace/determine-your-listing-type) that you can publish on the Microsoft Commercial Marketplace, and each has its settings.

`Consulting Services` themselves are of 5 types:

- **Assessment**: An evaluation of a customer's environment to determine the applicability of a solution and to estimate the cost and timeline of its implementation.
- **Briefing**: An introduction to a solution or a service using frameworks, demos, and customer examples.
- **Implementation**: A complete installation that results in a fully working solution.
- **Proof of concept**: A limited-scope implementation to determine whether a solution meets the customer's requirements.
- **Workshop**: An interactive engagement conducted on the customer's premises. It can involve training, briefings, assessments, or demos built on the customer's data or environment.

> **Warning**
> Each published offering will need to belong to one of these categories, and the category should be included in the name of the offering, as in the example below.

For the purpose of this guide, we will focus on the following assumptions:

- we want to publish a `Consulting Services`
- the service is an `Assessment`
- the technology is `Teams Meeting Rooms`
- the service takes us `1 day` to deliver

## Creating a new offer

You should create a new offer by clicking on the `+ New offer` button and selecting `Consulting Services`. A panel will show from the right side, and you will need to complete the two fields that will be displayed. Over here, the `Offer ID` and `Offer Alias` defined in the form will be used internally in Partner Center and will not be visible to customers.

![Partner Center - Commercial Marketplace](./../images/publishing/step1_pc.png "Creating a new offer")

```markdown
# Example values from above screenshot

Offer ID: `tmr_1day_assessment`
Offer Alias: `Teams Meeting Rooms: 1-day Assessment`
```

## Offer Setup

The first thing that you will need to configure when creating a `+ New Offer` is to configure where the leads that come from the respective offering will go.  
For this, you have [multiple options of destinations](https://learn.microsoft.com/en-us/partner-center/marketplace/create-consulting-service-offer#configure-lead-management), but for the purpose of this guide, we will focus on the [`HTTPS Endpoint`](https://learn.microsoft.com/en-us/partner-center/marketplace/partner-center-portal/commercial-marketplace-lead-management-instructions-https) destination.

![Partner Center - Commercial Marketplace](./../images/publishing/step2_crm.png "Select CRM destination")

> **Warning**
> If you do not have an HTTPS endpoint, please see [this section](./azure_webook.md) on how to easily create one using Azure.

After you select the `HTTPS Endpoint` and insert the URL of your endpoint, you will need to `Validate` the endpoint.  
If the validation is successful, go ahead and hit `Connect` on the form and then `Save Draft` on the initial offering, to save the changes.

![Partner Center - Commercial Marketplace](./../images/publishing/step3_crm.png "Select CRM destination")

## Proprieties

## Offer listing

## Pricing and availability

## Co-sell with Microsoft

## Publishing

## Post Publishing

### Extra resources

- [Consulting Services documentation](https://learn.microsoft.com/en-us/partner-center/marketplace/plan-consulting-service-offer)
