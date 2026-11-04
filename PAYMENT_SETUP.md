# Trendora — real payment setup guide

**Important:** the included checkout is a demonstration only. It does not take payments, create server-side orders, reserve stock, send email, or arrange delivery. Do not publish it as a live checkout. The sample UPI/card/COD choices are labels only; no credentials or payment details are collected.

## Suggested payment route for an India-based merchant

Start by comparing **Razorpay** and **Cashfree Payments**. Both advertise domestic UPI (including UPI apps such as Google Pay and PhonePe), cards and other payment methods. International card/cross-border features require separate eligibility, onboarding and activation; availability varies by merchant, business category, country and compliance review. Check current terms and fees directly before choosing.

- Razorpay: https://razorpay.com/payment-gateway/ and https://razorpay.com/international-payment-gateway-india/
- Cashfree: https://www.cashfree.com/ and https://www.cashfree.com/international-payment-gateway/
- Cashfree international overview: https://www.cashfree.com/accept-international-payments/

### 1. Prepare the business before applying

Create and verify the merchant/business account using the legal business name and bank account that will receive settlements. The provider may request identity/business proofs, PAN, bank proof, business registration/GST details where applicable, website ownership and additional documents. Requirements depend on the legal structure and provider review. Do not invent a business address, tax number, policy or company identity.

Before requesting live activation, publish accurate versions of these pages/details on your real domain:

- About the business and legal seller name
- Contact details and customer support method
- Product descriptions, prices, stock and shipping coverage
- Shipping, delivery, returns, refunds and cancellation policies
- Privacy policy and terms of sale
- Any required grievance/contact information

Have a qualified Indian accountant or legal adviser review GST, consumer-protection, invoicing, export and cross-border obligations for your actual business model.

### 2. Domestic UPI, Google Pay, PhonePe and cards

1. Apply for a payment gateway account with Razorpay or Cashfree.
2. Complete KYC/business verification and link the settlement bank account.
3. In the provider dashboard, enable the domestic payment methods approved for your account: UPI, debit/credit cards and any other methods you want to offer.
4. Google Pay and PhonePe are generally presented to customers as UPI apps/payment choices through the gateway's UPI flow, not as separate merchant bank accounts that you hard-code into a checkout.
5. Use the provider's sandbox/test mode first. Test successful, failed, cancelled and pending payments, refunds, duplicate callbacks and mobile UPI intent flows.
6. Switch to live credentials only after approval and end-to-end testing.

### 3. International cards and worldwide customers

1. Ask the chosen provider to enable its international/export payment facility for your Indian merchant account. It is not automatically active just because domestic card payments work.
2. Confirm supported buyer countries, currencies, card networks, settlement currency, fees, chargeback rules, refund process and required export/compliance documents.
3. Configure the allowed countries and currencies only after provider approval. Do not promise worldwide shipping until you have verified courier coverage, customs, duties, delivery times and restricted-product rules.
4. Show the buyer the actual currency charged and disclose shipping, duties/taxes and refund conditions before payment.
5. Reconcile settlements and maintain required remittance/export records with your accountant.

### 4. How the real integration must be built

The current Trendora files are static HTML/CSS/JavaScript. A production payment flow needs a trusted server/backend (or a supported commerce platform/plugin):

1. Browser sends the cart to your backend.
2. Backend rechecks product prices, availability, shipping and taxes from a trusted catalogue/database.
3. Backend creates a payment order/session using the gateway's secret key. **Never put secret keys in browser JavaScript or commit them to GitHub.**
4. Browser opens the provider's hosted checkout/SDK using the returned public/order details.
5. Backend verifies the payment signature and/or webhook using the provider's documented method before marking an order paid.
6. Backend stores the order and payment status, sends confirmation, updates inventory and supports refunds/reconciliation.

Use the gateway's official current developer documentation and SDK. Keep secret keys in server-side environment variables, verify webhook signatures, use HTTPS, validate all incoming data, and make webhook/order processing idempotent. Never trust a success redirect alone as proof of payment.

Useful starting points:
- Razorpay docs: https://razorpay.com/docs/
- Cashfree docs: https://www.cashfree.com/docs/

## Google Pay and PhonePe distinction

For an Indian website, the normal UPI integration through an approved payment gateway lets customers choose a supported UPI app such as Google Pay or PhonePe. Availability depends on the gateway's current UPI product, app/device and transaction rules. Do not place a personal UPI ID or QR on a commercial checkout as a substitute for verified order/payment reconciliation unless your bank/provider explicitly supports that business collection method.

## Go-live checklist

- [ ] Replace demo product catalogue with genuine products, prices, stock and product photography you have rights to use.
- [ ] Add real legal seller details and customer-support contacts.
- [ ] Publish reviewed shipping, return/refund, cancellation, privacy and terms pages.
- [ ] Configure tax/GST, invoices and shipping rules for your business.
- [ ] Complete gateway KYC and receive written/live dashboard activation for each payment method.
- [ ] Build backend order creation, payment verification, signed webhooks, inventory and refunds.
- [ ] Test in sandbox, then make a small controlled live transaction and refund it.
- [ ] Remove demo checkout labels and do not go live until the complete order/payment flow is verified.

Provider features, eligibility and fees change. Confirm them in the merchant dashboard and current provider documentation on the day you integrate.
