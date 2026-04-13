import React, { useState, useEffect } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { LineChart, Line, XAxis, YAxis, Tooltip, ResponsiveContainer, ReferenceLine } from "recharts";

function dynamicLimit({ multiple, maxLimit, inflection, shortCurv, longCurv }) {
  const x = multiple;
  const I = inflection;

  if (I <= 0) return 0;

  const num =
    (Math.PI / 2) +
    Math.atan(Math.pow(x / I, -shortCurv) - Math.pow(x / I, longCurv));

  const den =
    (Math.PI / 2) +
    Math.atan(Math.pow(1 / I, -shortCurv) - Math.pow(1 / I, longCurv));

  if (den === 0) return 0;

  const ratio = num / den;
  const limit = maxLimit * ratio;

  return Math.max(0, Math.min(maxLimit, limit));
}

function stepLimit(limit, maxLimit, steps) {
  if (steps <= 0) return limit;
  const stepSize = maxLimit / steps;
  return Math.ceil(limit / stepSize) * stepSize;
}

function runTests() {
  const params = { maxLimit: 0.25, inflection: 1.5, shortCurv: 2.5, longCurv: 0.2 };

  console.log("x=1 ~ max:", dynamicLimit({ multiple: 1, ...params }));
  console.log("x small:", dynamicLimit({ multiple: 0.01, ...params }));
  console.log("x large:", dynamicLimit({ multiple: 10, ...params }));
}

const inputStyle = {
  width: "100%",
  padding: "3px 18px 3px 3px",
  boxSizing: "border-box",
  background: "#fff3b0",
  color: "red",
  border: "1px solid #aaa",
  textAlign: "right"
};

export default function App() {
  const [maxLimit] = useState(0.25);
  const [inflection, setInflection] = useState("1.5");
  const [shortCurv, setShortCurv] = useState("2.5");
  const [longCurv, setLongCurv] = useState("0.2");
  const [steps, setSteps] = useState(4);

  const [equityVol, setEquityVol] = useState("45");
  const [indexVol, setIndexVol] = useState("7");

  const eq = parseFloat(equityVol);
  const idx = parseFloat(indexVol);
  const multiple = idx > 0 ? eq / idx : 0;

  useEffect(() => {
    runTests();
  }, []);

  const data = Array.from({ length: 50 }, (_, i) => {
    const m = i * 0.5;
    const limit = dynamicLimit({
      multiple: m,
      maxLimit,
      inflection: parseFloat(inflection),
      shortCurv: parseFloat(shortCurv),
      longCurv: parseFloat(longCurv)
    });

    return {
      multiple: m,
      limit,
      stepLimit: stepLimit(limit, maxLimit, steps)
    };
  });

  const maxX = Math.max(...data.map((d) => d.multiple), multiple);

  const currentDynamic = dynamicLimit({
    multiple,
    maxLimit,
    inflection: parseFloat(inflection),
    shortCurv: parseFloat(shortCurv),
    longCurv: parseFloat(longCurv)
  });

  const pct = (v) => `${(v * 100).toFixed(2)}%`;

  return (
    <div className="p-6 grid gap-6">
      {/* Header */}
      <div className="text-2xl md:text-3xl font-bold text-black">
        Dynamically Adjusting Risk Limits to a Reference Index
      </div>

      {/* Inputs */}
      <Card className="p-4">
        <CardContent className="grid gap-4">
          <div className="grid grid-cols-2 md:grid-cols-3 gap-4">
            <div>
              <label>Equity Vol (%)</label>
              <Input value={equityVol} onChange={(e) => setEquityVol(e.target.value)} style={inputStyle} />
            </div>
            <div>
              <label>Index Vol (%)</label>
              <Input value={indexVol} onChange={(e) => setIndexVol(e.target.value)} style={inputStyle} />
            </div>
            <div className="flex items-end">
              <div>
                <label>Multiple</label>
                <div className="text-lg font-bold">{multiple.toFixed(2)}x</div>
              </div>
            </div>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
            <div>
              <label>Inflection (I)</label>
              <Input value={inflection} onChange={(e) => setInflection(e.target.value)} style={inputStyle} />
            </div>
            <div>
              <label>Short Curvature (Cs)</label>
              <Input value={shortCurv} onChange={(e) => setShortCurv(e.target.value)} style={inputStyle} />
            </div>
            <div>
              <label>Long Curvature (Cl)</label>
              <Input value={longCurv} onChange={(e) => setLongCurv(e.target.value)} style={inputStyle} />
            </div>
          </div>

          <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
            <div>
              <label>Steps (N)</label>
              <Input value={steps} onChange={(e) => setSteps(parseInt(e.target.value) || 1)} style={inputStyle} />
            </div>
          </div>
        </CardContent>
      </Card>

      {/* Readout */}
      <Card className="p-4">
        <CardContent className="grid grid-cols-1 md:grid-cols-3 gap-4">
          <div>
            <div className="text-xs opacity-70">Multiple</div>
            <div className="text-xl font-bold">{multiple.toFixed(2)}x</div>
          </div>
          <div>
            <div className="text-xs opacity-70">Static Limit (Lmax)</div>
            <div className="text-xl font-bold">{pct(maxLimit)}</div>
          </div>
          <div>
            <div className="text-xs opacity-70">Dynamic Limit L(x)</div>
            <div className="text-xl font-bold">{pct(currentDynamic)}</div>
          </div>
        </CardContent>
      </Card>

      {/* Chart */}
      <Card className="p-4">
        <CardContent>
          <ResponsiveContainer width="100%" height={300}>
            <LineChart data={data}>
              <XAxis type="number" dataKey="multiple" domain={[0, maxX]} />
              <YAxis />
              <Tooltip />

              <Line type="monotone" dataKey="limit" stroke="#000" strokeWidth={3} dot={false} />
              <Line type="stepAfter" dataKey="stepLimit" stroke="#ff0000" strokeWidth={3} dot={false} />

              <ReferenceLine
                x={multiple}
                strokeDasharray="3 3"
                label={{ value: `x = ${multiple.toFixed(2)}`, position: "top" }}
              />
            </LineChart>
          </ResponsiveContainer>
        </CardContent>
      </Card>

      {/* Formula */}
      <Card className="p-4">
        <CardContent>
          <div className="text-sm font-mono">
            L(x) = Lmax · [ (π/2 + atan((x/I)^(-Cs) - (x/I)^Cl)) / (π/2 + atan((1/I)^(-Cs) - (1/I)^Cl)) ]
          </div>
        </CardContent>
      </Card>

      {/* Footer */}
      <div className="text-xs text-center text-gray-500 italic mt-6">
        © Quantik.org. All rights reserved. This model and its intellectual property may not be copied or distributed without prior consent.
      </div>
    </div>
  );
}
