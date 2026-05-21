# Payments Processing

Payments Processing handles the money side of an Arcadia Editions order.
Its business role is to authorize the charge, manage retries and failures,
capture the funds once the order can move forward, and void the payment when the
commercial flow must be compensated.

It gives the rest of the platform trustworthy payment outcomes without owning the
order, stock, or shipping domains.
