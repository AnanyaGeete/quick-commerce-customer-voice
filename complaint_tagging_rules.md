> These tagging rules are reused from [Quick-Commerce NPS Benchmark from App Reviews](https://github.com/kaasyapv/Quick-Commerce-NPS-Benchmark-from-App-Reviews), Copyright (c) 2026 kaasyapv, released under the MIT License. Reused here so the complaint tags in this project can be compared with that study.

# Labelling rules

Every detractor review (1 to 3 stars, 4 or more words) gets exactly one label. The same rules
are used by the model taggers, by the hand labelling page and by the keyword baseline check.
Judge the text, not the star rating. Reviews are English, Hindi or Hinglish: judge by meaning.

## The ten labels

* late_delivery: order arrived late or took far longer than promised
* missing_or_wrong_items: items missing, wrong or short in the order, or marked delivered but never arrived
* quality_freshness: stale, expired, rotten, damaged or poor quality products
* fees_and_prices: delivery, handling or platform fees, high prices, and coupons, offers or free cash that won't apply
* refunds_returns: refund missing or slow, return or replacement refused
* customer_support: support and rider behaviour: bots, no human agent, unhelpful or rude support, rude riders
* app_payment_bugs: app and payment problems: crashes, OTP or login trouble, failed payments, money deducted, COD not offered, no cancel option
* out_of_stock: items unavailable or out of stock, or not serviceable in my area
* other: a complaint that fits none of the above
* no_complaint: no complaint, or too vague to name any problem (praise, or just 'worst app')

## Mixed reviews

Pick the complaint that most plausibly caused the low rating: the one stated first, or the one
given the most emphasis. Never pick two labels.

## Tie breaks

* Marked delivered but never arrived, or the order never came: missing_or_wrong_items.
* Damaged, broken, used or expired item received: quality_freshness. If the review is mainly
  about the refusal to refund, return or replace it, use refunds_returns.
* Money deducted but the order failed or was never placed: app_payment_bugs.
  A refund still pending for a returned or cancelled order: refunds_returns.
* A cancellation charge: fees_and_prices. Cannot cancel at all: app_payment_bugs.
* Free cash, cashback, coupons and offers that are missing or won't apply: fees_and_prices.
* Rude or abusive riders and delivery partners: customer_support.
* Area not served, "unserviceable", app not available where I live: out_of_stock.
* An order cancelled by the app or seller: other.
* A low star review that only praises, or only says "worst app", "bekar", "waste": no_complaint.
* other is only for a real complaint that fits none of the labels above.

## Output format

One line per review: `position|label`, using the position number from the chunk file and one
of the ten label names exactly as written above.
