import React, { useState, useEffect } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";

export default function PremiosConSuerte() {
  const [nombre, setNombre] = useState("");
  const [cedula, setCedula] = useState("");
  const [telefono, setTelefono] = useState("");
  const [email, setEmail] = useState("");
  const [boletos, setBoletos] = useState(1);
  const [comprobante, setComprobante] = useState(null);
  const [fechaSorteo, setFechaSorteo] = useState("");

  useEffect(() => {
    const siguienteSorteo = new Date();
    siguienteSorteo.setDate(siguienteSorteo.getDate() + (7 - siguienteSorteo.getDay()));
    siguienteSorteo.setHours(20, 0, 0, 0);
    setFechaSorteo(siguienteSorteo.toLocaleString());
  }, []);

  return (
    <div className="p-4 max-w-xl mx-auto">
      <h1 className="text-3xl font-bold text-center mb-4">Premios con Suerte 🎁</h1>

      <Card className="mb-6">
        <CardContent className="p-4">
          <p className="mb-2">Participa en el sorteo semanal de licores, entradas y más.</p>
          <p className="text-sm text-gray-600">Precio del boleto: $0.50 a $1.00</p>
          <p className="text-sm text-gray-600">Fecha del próximo sorteo: <strong>{fechaSorteo}</strong></p>
        </CardContent>
      </Card>

      <Card>
        <CardContent className="p-4 space-y-3">
          <h2 className="text-xl font-semibold">Compra tu boleto</h2>

          <Input placeholder="Nombre completo" value={nombre} onChange={(e) => setNombre(e.target.value)} />
          <Input placeholder="Cédula" value={cedula} onChange={(e) => setCedula(e.target.value)} />
          <Input placeholder="Teléfono" value={telefono} onChange={(e) => setTelefono(e.target.value)} />
          <Input placeholder="Correo electrónico" value={email} onChange={(e) => setEmail(e.target.value)} />
          <Input type="number" min={1} max={10} placeholder="Número de boletos" value={boletos} onChange={(e) => setBoletos(e.target.value)} />

          <div>
            <p className="text-sm">Realiza tu transferencia a la cuenta del Banco Pichincha:</p>
            <p className="text-sm font-bold">Cuenta N°: 1234567890</p>
            <p className="text-sm">Titular: Premios con Suerte</p>
          </div>

          <Input type="file" accept="image/*,.pdf" onChange={(e) => setComprobante(e.target.files[0])} />

          <Button className="w-full">Enviar comprobante</Button>
        </CardContent>
      </Card>
    </div>
  );
}

