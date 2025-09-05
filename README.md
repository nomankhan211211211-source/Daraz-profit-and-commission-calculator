# Daraz-profit-and-commission-calculator
Daraz Profit Calculator – A simple web app to calculate product cost, Daraz commission, and final profit margin for sellers.
import { useState } from "react";

export default function DarazProfitCalculator() { const [cost, setCost] = useState(0); const [shipping, setShipping] = useState(0); const [price, setPrice] = useState(0); const [commissionRate, setCommissionRate] = useState(10);

const commission = (price * commissionRate) / 100; const totalCost = parseFloat(cost) + parseFloat(shipping) + commission; const profit = price - totalCost; const margin = price > 0 ? ((profit / price) * 100).toFixed(2) : 0;

return ( <div className="min-h-screen flex items-center justify-center bg-gray-100 p-4"> <div className="bg-white shadow-xl rounded-2xl p-6 w-full max-w-md"> <h1 className="text-2xl font-bold mb-4 text-center text-gray-800"> Daraz Profit Calculator </h1> <div className="space-y-3"> <div> <label className="block text-gray-700">Product Cost (Rs)</label> <input type="number" value={cost} onChange={(e) => setCost(e.target.value)} className="w-full p-2 border rounded-lg" /> </div>

<div>
        <label className="block text-gray-700">Shipping Charges (Rs)</label>
        <input
          type="number"
          value={shipping}
          onChange={(e) => setShipping(e.target.value)}
          className="w-full p-2 border rounded-lg"
        />
      </div>

      <div>
        <label className="block text-gray-700">Selling Price (Rs)</label>
        <input
          type="number"
          value={price}
          onChange={(e) => setPrice(e.target.value)}
          className="w-full p-2 border rounded-lg"
        />
      </div>

      <div>
        <label className="block text-gray-700">Daraz Commission %</label>
        <input
          type="number"
          value={commissionRate}
          onChange={(e) => setCommissionRate(e.target.value)}
          className="w-full p-2 border rounded-lg"
        />
      </div>
    </div>

    <div className="mt-6 bg-gray-50 p-4 rounded-lg shadow-inner">
      <p className="text-gray-700">Commission: Rs {commission.toFixed(2)}</p>
      <p className="text-gray-700">Total Cost: Rs {totalCost.toFixed(2)}</p>
      <p className="text-gray-700 font-semibold">
        Profit: Rs {profit.toFixed(2)} ({margin}% margin)
      </p>
    </div>
  </div>
</div>

); }

