<h1 align="center">eCommerce Sales Funnel Analysis</h1>
<table align="center">
  <tr>
    <td width="1440">
      <h2 align="center">Project Background</h2>
      <body>
        This project performs a full-funnel sales analysis of a simulated eCommerce platform using <strong>BigQuery SQL</strong>. The dataset contains <strong>9,381 user event records</strong> spanning the entire customer journey — from initial page view through add-to-cart, checkout, payment, and final purchase — across multiple traffic acquisition channels. <br>
        <br>
        All events are dated from <strong>January 2025 onward</strong> and tracked across <strong>5,000 unique visitors</strong>. The platform generated <strong>$87,975 in total revenue</strong> from <strong>826 completed orders</strong> during the analysis period. <br>
        <br>
        The analysis is structured around four SQL queries that answer the following questions:
      </body>
      <h3>Northstar Metrics</h3>
      <h4>
        <ul>
          <li>Funnel conversion rates — How many users drop off at each stage from page view to purchase?</li>
          <li>Traffic source performance — Which acquisition channels drive the most purchases and the highest conversion rates?</li>
          <li>Time to conversion — How long does it take a user to move from first view to completed purchase?</li>
          <li>Revenue funnel — What is the platform's average order value, revenue per buyer, and revenue per visitor?</li>
        </ul>
      </h4>
    </td>
  </tr>
</table>

<table align="center">
  <tr>
    <div width="920">
      <h1 align="center">Executive Summary</h1>
      <h3 align="center">Sales Funnel Overview (2025)</h3>
      <td width="1440" valign="top">
        <ol>
          <li>
            <strong>Funnel Performance — Largest Drop at the Top:</strong>
            <ul>
              <li>The steepest drop in the funnel occurs at the very first step: only <strong>31% of page viewers</strong> go on to add an item to their cart (5,000 viewers → 1,553 ATC users).</li>
              <li>Once a user adds to cart, retention improves significantly — <strong>71%</strong> proceed to checkout start, <strong>82%</strong> advance from checkout to payment, and <strong>92%</strong> complete the purchase after entering payment info.</li>
              <li>The <strong>overall end-to-end conversion rate is 17%</strong> (826 purchases from 5,000 visitors), which is strong for eCommerce and indicates that the bottom of the funnel is well-optimized.</li>
            </ul>
          </li>
          <li>
            <strong>Revenue Snapshot:</strong>
            <ul>
              <li><strong>Total revenue: $87,975</strong> across 826 orders.</li>
              <li><strong>Average order value (AOV): $106.51</strong></li>
              <li><strong>Revenue per visitor: $17.60</strong> — a key metric reflecting how efficiently site traffic is monetized.</li>
              <li>Revenue per buyer and orders per buyer are both 1:1, indicating no repeat purchases were captured in this dataset window.</li>
            </ul>
          </li>
        </ol>
      </td>
    </div>
  </tr>
</table>

<h2 align="center">Dataset Structure</h2>
<body align="center">The database consists of a single table — <strong>user_events</strong> — with 9,381 rows and 7 columns: <strong>event_id, user_id, event_type, event_date, product_id, amount,</strong> and <strong>traffic_source</strong>. The dataset lives in BigQuery under the project <code>sql-ecommerce-sales-funnel.ecom_sales_funnel</code>.</body>

<h1 align="center">Insights Deep-Dive</h1>

<table align="center">
  <tr>
    <h2 align="center">Funnel Stage Breakdown</h2>
    <td width="1440" align="center">
      <img width="900" alt="Sales Funnel — User Drop-off by Stage" src="https://res.cloudinary.com/dcqk5bgqe/image/upload/v1773872896/funnel_chart_ucvbq2.png" />
    </td>
  </tr>
  <tr>
    <td width="1440">
      <table>
        <tr>
          <th align="left">Stage</th>
          <th align="left">Event</th>
          <th align="right">Distinct Users</th>
          <th align="right">Stage Conversion Rate</th>
        </tr>
        <tr>
          <td>Stage 1</td>
          <td>Page View</td>
          <td align="right">5,000</td>
          <td align="right">—</td>
        </tr>
        <tr>
          <td>Stage 2</td>
          <td>Add to Cart</td>
          <td align="right">1,553</td>
          <td align="right">31%</td>
        </tr>
        <tr>
          <td>Stage 3</td>
          <td>Checkout Start</td>
          <td align="right">1,103</td>
          <td align="right">71%</td>
        </tr>
        <tr>
          <td>Stage 4</td>
          <td>Payment Info</td>
          <td align="right">899</td>
          <td align="right">82%</td>
        </tr>
        <tr>
          <td>Stage 5</td>
          <td>Purchase</td>
          <td align="right">826</td>
          <td align="right">92%</td>
        </tr>
      </table>
      <br>
      <ul>
        <li>The <strong>view-to-cart drop (69% falloff)</strong> is the single largest point of revenue leakage in the funnel and represents the highest-priority area for optimization — better product discovery, imagery, and pricing presentation could meaningfully lift this rate.</li>
        <li>The <strong>cart-to-checkout gap (29% falloff)</strong> is the second-largest drop, often driven by unexpected shipping costs or friction in the cart experience.</li>
        <li>The <strong>lower funnel (checkout → payment → purchase) is highly efficient</strong>, losing only 27% of users across two steps. This suggests the checkout flow itself is well-designed once users are committed.</li>
      </ul>
    </td>
  </tr>
</table>

<table align="center">
  <tr>
    <h2 align="center">Conversion Rate by Traffic Source</h2>
    <td width="1440" align="center">
      <img width="900" alt="Conversion by Traffic Source" src="https://res.cloudinary.com/dcqk5bgqe/image/upload/v1773872896/traffic_source_chart_lwcdjv.png" />
    </td>
  </tr>
  <tr>
    <td width="1440">
      <table>
        <tr>
          <th align="left">Traffic Source</th>
          <th align="right">Views</th>
          <th align="right">Add to Cart</th>
          <th align="right">Purchases</th>
          <th align="right">ATC Rate</th>
          <th align="right">Purchase Rate</th>
          <th align="right">ATC → Purchase</th>
        </tr>
        <tr>
          <td>Email</td>
          <td align="right">522</td>
          <td align="right">326</td>
          <td align="right">177</td>
          <td align="right">62%</td>
          <td align="right"><strong>34%</strong></td>
          <td align="right">54%</td>
        </tr>
        <tr>
          <td>Paid Ads</td>
          <td align="right">968</td>
          <td align="right">358</td>
          <td align="right">204</td>
          <td align="right">37%</td>
          <td align="right">21%</td>
          <td align="right">57%</td>
        </tr>
        <tr>
          <td>Organic</td>
          <td align="right">2,038</td>
          <td align="right">669</td>
          <td align="right">343</td>
          <td align="right">33%</td>
          <td align="right">17%</td>
          <td align="right">51%</td>
        </tr>
        <tr>
          <td>Social</td>
          <td align="right">1,472</td>
          <td align="right">200</td>
          <td align="right">102</td>
          <td align="right">14%</td>
          <td align="right"><strong>7%</strong></td>
          <td align="right">51%</td>
        </tr>
      </table>
      <br>
      <ul>
        <li><strong>Email is the highest-converting channel</strong> by a significant margin — a 34% purchase rate and a 62% add-to-cart rate indicate users arriving via email are already primed to buy, likely due to targeted or promotional messaging.</li>
        <li><strong>Paid ads deliver strong ROI efficiency</strong> — a 21% purchase rate and the highest ATC-to-purchase conversion (57%) suggest paid traffic is well-targeted and that users who engage are highly likely to complete a transaction.</li>
        <li><strong>Organic is the volume leader</strong> with 2,038 views and 343 purchases, but its 17% purchase rate is average — a meaningful improvement in organic landing page quality or personalization could unlock significant incremental revenue.</li>
        <li><strong>Social is the weakest channel</strong> — despite 1,472 views (the second-highest volume), it converts at only 7%. Its 14% ATC rate is less than half of any other channel, indicating that social traffic arrives with low purchase intent. This channel likely needs a different funnel strategy (e.g., retargeting) rather than direct conversion optimization.</li>
      </ul>
    </td>
  </tr>
</table>

<table align="center">
  <tr>
    <h2 align="center">Time to Conversion</h2>
    <td width="1440" align="center">
      <img width="900" alt="Average Time to Conversion" src="https://res.cloudinary.com/dcqk5bgqe/image/upload/v1773872896/time_to_conversion_chart_aaojwi.png" />
    </td>
  </tr>
  <tr>
    <td width="1440">
      <table>
        <tr>
          <th align="left">Metric</th>
          <th align="right">Value</th>
        </tr>
        <tr>
          <td>Converted Users</td>
          <td align="right">826</td>
        </tr>
        <tr>
          <td>Avg. View → Cart Time</td>
          <td align="right">11.16 minutes</td>
        </tr>
        <tr>
          <td>Avg. Cart → Purchase Time</td>
          <td align="right">13.47 minutes</td>
        </tr>
        <tr>
          <td>Avg. View → Purchase Time</td>
          <td align="right">24.63 minutes</td>
        </tr>
      </table>
      <br>
      <ul>
        <li>The average customer journey from first page view to completed purchase takes just under <strong>25 minutes</strong>, indicating a largely impulse-driven or low-friction buying behavior.</li>
        <li>Users spend a near-equal amount of time browsing before adding to cart (~11 min) and deliberating after adding to cart (~13 min) — suggesting the cart/checkout stage has meaningful friction worth investigating.</li>
        <li>The short time-to-purchase window also implies that <strong>abandoned cart recovery campaigns</strong> would need to be fast-acting (within 1–2 hours) to recapture users who drop off after adding to cart.</li>
      </ul>
    </td>
  </tr>
</table>

<table align="center">
  <tr>
    <h2 align="center">Revenue Funnel</h2>
    <td width="1440" align="center">
      <img width="900" alt="Revenue Funnel Metrics" src="https://res.cloudinary.com/dcqk5bgqe/image/upload/v1773872896/revenue_metrics_chart_pecqg0.png" />
    </td>
  </tr>
  <tr>
    <td width="1440">
      <table>
        <tr>
          <th align="left">Metric</th>
          <th align="right">Value</th>
        </tr>
        <tr>
          <td>Total Visitors</td>
          <td align="right">5,000</td>
        </tr>
        <tr>
          <td>Total Buyers</td>
          <td align="right">826</td>
        </tr>
        <tr>
          <td>Total Orders</td>
          <td align="right">826</td>
        </tr>
        <tr>
          <td>Total Revenue</td>
          <td align="right"><strong>$87,975.11</strong></td>
        </tr>
        <tr>
          <td>Average Order Value (AOV)</td>
          <td align="right">$106.51</td>
        </tr>
        <tr>
          <td>Revenue per Buyer</td>
          <td align="right">$106.51</td>
        </tr>
        <tr>
          <td>Revenue per Visitor</td>
          <td align="right">$17.60</td>
        </tr>
      </table>
      <br>
      <ul>
        <li>At <strong>$106.51 AOV</strong>, the platform is positioned in a mid-market price tier — there may be upsell or bundling opportunities to push this meaningfully higher.</li>
        <li><strong>Revenue per visitor of $17.60</strong> is the clearest measure of how efficiently traffic is being monetized. Growing this metric — either by converting more visitors or increasing AOV — is the primary lever for revenue growth.</li>
        <li>Orders and buyers having a <strong>1:1 ratio</strong> suggests no repeat purchases occur within the dataset window, pointing to an opportunity to build post-purchase re-engagement campaigns that drive a second order.</li>
      </ul>
    </td>
  </tr>
</table>

<table align="center">
  <h1>Recommendations</h1>
  <h4>Based on the uncovered insights, here are actionable items that can improve funnel performance and revenue.</h4>
  <ul>
    <h3>Top-of-Funnel Optimization</h3>
    <li>Prioritize reducing the view-to-cart dropoff rate — converting even 5% more of the 5,000 page viewers would add ~250 users to the funnel and yield an estimated ~$26,000 in incremental revenue at current AOV.</li>
      <ul>
        <li>Test improvements to product page design: clearer CTAs, social proof (reviews/ratings), urgency signals (low stock indicators), and faster load times.</li>
      </ul>
    <h3>Social Channel Strategy</h3>
    <li>Social traffic's 7% purchase rate and 14% ATC rate indicate it is not suitable for direct conversion — reframe social as a top-of-funnel awareness channel.</li>
      <ul>
        <li>Implement retargeting campaigns to re-engage social visitors with paid ads after they leave the site, leveraging the paid ads channel's stronger 57% ATC-to-purchase rate.</li>
      </ul>
    <h3>Email Channel Expansion</h3>
    <li>Email delivers the highest purchase rate (34%) and ATC rate (62%) by a wide margin, yet has the smallest view volume (522). Growing the email list and send frequency is the highest-ROI lever available.</li>
      <ul>
        <li>Invest in email acquisition (pop-ups, gated offers) and expand campaign cadence to capture more of the platform's 5,000 unique visitor pool.</li>
      </ul>
    <h3>Abandoned Cart Recovery</h3>
    <li>Given the average cart-to-purchase time of ~13 minutes, a significant portion of the 727 users who added to cart but did not purchase were likely close to converting.</li>
      <ul>
        <li>Deploy fast-trigger abandoned cart emails (within 30–60 minutes) and consider cart persistence across sessions to recover these near-conversions.</li>
      </ul>
    <h3>Repeat Purchase Programs</h3>
    <li>The 1:1 buyer-to-order ratio reveals zero repeat purchases in the dataset window — a post-purchase lifecycle program could meaningfully grow revenue per buyer above the current $106.51.</li>
      <ul>
        <li>Launch a post-purchase email sequence (thank-you, usage tips, complementary product recommendations) triggered within 24–48 hours of first purchase.</li>
        <li>Consider a loyalty or points program to incentivize return visits, particularly targeting the 343 organic buyers who show baseline intent.</li>
      </ul>
  </ul>
</table>
