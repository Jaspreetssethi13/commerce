// package.json { "name": "grdpress-ecommerce", "version": "1.0.0", "scripts": { "dev": "next dev", "build": "next build", "start": "next start" }, "dependencies": { "next": "13.4.12", "react": "18.2.0", "react-dom": "18.2.0" } }

// next.config.js const nextConfig = {} module.exports = nextConfig

// pages/index.tsx import React from "react"; import Script from "next/script";

export default function Home() { const handlePayment = () => { const options = { key: "RAZORPAY_KEY_ID", // Replace with your Razorpay Key ID amount: 199900, currency: "INR", name: "GRD PRESS", description: "Engraved Visitors' Book", image: "/logo.png", handler: function (response) { alert("Payment successful! Payment ID: " + response.razorpay_payment_id); window.location.href = "/thank-you"; }, prefill: { name: "", email: "", contact: "" }, theme: { color: "#f43f5e" } }; const rzp = new window.Razorpay(options); rzp.open(); };

return ( <div className="min-h-screen bg-white text-black px-6 py-10"> <Script src="https://checkout.razorpay.com/v1/checkout.js" /> <header className="flex justify-between items-center mb-10"> <img src="/logo.png" alt="GRD Press Logo" className="h-16" /> <button className="bg-red-600 text-white px-6 py-2 rounded-xl">Contact Us</button> </header>

<section className="text-center mb-12">
    <h1 className="text-4xl font-bold mb-4">GRD PRESS</h1>
    <p className="text-lg text-gray-600">Premium Engraved Visitor Books for Elite Institutions</p>
  </section>

  <section className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
    <div className="rounded-2xl shadow-lg border border-gray-200">
      <img
        src="/visitors-book.jpg"
        alt="Visitors Book"
        className="rounded-t-2xl w-full h-64 object-cover"
      />
      <div className="p-6">
        <h2 className="text-2xl font-semibold mb-2">Engraved Visitors' Book</h2>
        <p className="text-gray-600 mb-4">
          Featuring silver metal engraved design for the 3rd Battalion Sikh Light Infantry. Ideal for
          commemorative and official use.
        </p>
        <p className="text-xl font-bold mb-4">₹1,999</p>
        <button onClick={handlePayment} className="bg-black text-white w-full py-2 rounded-xl">Buy Now</button>
      </div>
    </div>
  </section>

  <footer className="mt-20 text-center text-sm text-gray-500">
    &copy; 2025 GRD PRESS. All rights reserved.
  </footer>
</div>

); }

// pages/thank-you.tsx export default function ThankYou() { return (

