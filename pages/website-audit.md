---
layout: page
title: Website audit
permalink: /website-audit
section: proposal
intro_paragraph:
---

<!-- Load Stripe.js on your website. -->
<script src="https://js.stripe.com/v3"></script>

<button style="background-color:#6772E5;color:#FFF;padding:8px 12px;border:0;border-radius:4px;font-size:1em" id="checkout-button-plan_D3r3AlJjiRTPbQ" role="link">
  Checkout
</button>

<div id="error-message"></div>

<script>
(function() {
  var stripe = Stripe('pk_live_P2Ijeq1xX4rYnJukcMW2dGjW');

  var checkoutButton = document.getElementById('checkout-button-plan_D3r3AlJjiRTPbQ');
  checkoutButton.addEventListener('click', function () {
    // When the customer clicks on the button, redirect
    // them to Checkout.
    stripe.redirectToCheckout({
      items: [{plan: 'plan_D3r3AlJjiRTPbQ', quantity: 1}],

      // Do not rely on the redirect to the successUrl for fulfilling
      // purchases, customers may not always reach the success_url after
      // a successful payment.
      // Instead use one of the strategies described in
      // https://stripe.com/docs/payments/checkout/fulfillment
      successUrl: 'https://leadingwebstudio.com/success',
      cancelUrl: 'https://leadingwebstudio.com/canceled',
    })
    .then(function (result) {
      if (result.error) {
        // If `redirectToCheckout` fails due to a browser or network
        // error, display the localized error message to your customer.
        var displayError = document.getElementById('error-message');
        displayError.textContent = result.error.message;
      }
    });
  });
})();
</script>
