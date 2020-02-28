---
title: Převádění řetězců na datové typy rozhraní .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
ms.openlocfilehash: e54990785cafd6061c6d53c13af6476a4b46e20e
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160349"
---
# <a name="converting-strings-to-net-framework-data-types"></a>Převádění řetězců na datové typy rozhraní .NET Framework
Chcete-li převést řetězec na datový typ .NET Framework, použijte metodu **XmlConvert** , která odpovídá požadavkům aplikace. Seznam všech metod převodu, které jsou k dispozici ve třídě **XmlConvert** , naleznete v tématu <xref:System.Xml.XmlConvert>.  
  
 Řetězec vrácený metodou **ToString** je řetězcová verze dat, která je předána. Kromě toho existuje několik typů .NET Framework, které se převádějí pomocí třídy **XmlConvert** , ale nepoužívají metody ve třídě **System. Convert** . Třída **XmlConvert** se řídí specifikací datového typu XSD (XML Schema) a má datový typ, na který může **XmlConvert** mapovat.  
  
 V následující tabulce jsou uvedeny .NET Framework datové typy a typy řetězců, které jsou vráceny pomocí mapování datových typů schématu XML (XSD). Tyto typy .NET Framework nelze zpracovat pomocí **System. Convert**.  
  
|Typ rozhraní .NET Framework|Vrácený řetězec|  
|-------------------------|---------------------|  
|Logická hodnota|"pravda", "NEPRAVDA"|  
|Single. PositiveInfinity|"INF"|  
|Single. NegativeInfinity|"-INF"|  
|Double. PositiveInfinity|"INF"|  
|Double. NegativeInfinity|"-INF"|  
|DateTime|Formát je "rrrr-MM-ddTHH: mm: sszzzzzz" a jeho podmnožiny.|  
|Časový interval|Formát je PnYnMnTnHnMnS, což je, `P2Y10M15DT10H30M20S` je doba 2 roky, 10 měsíců, 15 dní, 10 hodin, 30 minut a 20 sekund.|  
  
> [!NOTE]
> Pokud převedete některý z .NET Framework typů uvedených v tabulce na řetězec pomocí metody **ToString** , vrácený řetězec není základní typ, ale typ řetězce XML Schema (XSD).  
  
 Typ hodnoty **DateTime** a **TimeSpan** se liší v tom, že hodnota DateTime představuje okamžitý čas, zatímco **hodnota** **TimeSpan** představuje časový interval. Formáty **DateTime** a **TimeSpan** jsou zadány ve specifikaci datových typů schématu XML (XSD). Příklad:  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 **Výstup**  
  
 `<Date>2001-08-04T00:00:00</Date>`.  
  
 Následující kód převede celé číslo na řetězec:  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 **Výstup**  
  
 `<Number>200</Number>`  
  
 Nicméně pokud převádíte řetězec na **Boolean**, **Single**nebo **Double**, typ .NET Framework, který je vrácen, není stejný jako typ vrácený při použití třídy **System. Convert** .  
  
## <a name="string-to-boolean"></a>Řetězec na logickou hodnotu  
 Následující tabulka ukazuje, jaký typ je vygenerován pro dané vstupní řetězce, při převodu řetězce na **logickou hodnotu** pomocí metody **ToBoolean** .  
  
|Platný vstupní parametr řetězce|Typ výstupu .NET Framework|  
|----------------------------------|--------------------------------|  
|„true“|Logická hodnota. true|  
|1|Logická hodnota. true|  
|„false“|Boolean. false|  
|"0"|Boolean. false|  
  
 Například s ohledem na následující kód XML:  
  
 **Input** (Vstup)  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>
```  
  
 Obojí lze chápat pomocí následujícího kódu a **bValue** je **System. Boolean. true**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>Řetězec na jeden  
 Následující tabulka ukazuje, jaký typ je vygenerován pro dané vstupní řetězce, při převodu řetězce na **jeden** pomocí metody **ToSingle –** .  
  
|Platný vstupní parametr řetězce|Typ výstupu .NET Framework|  
|----------------------------------|--------------------------------|  
|"INF"|Single. PositiveInfinity|  
|"-INF"|Single. NegativeInfinity|  
  
## <a name="string-to-double"></a>Řetězec, který se má zdvojnásobit  
 Následující tabulka ukazuje, jaký typ je vygenerován pro dané vstupní řetězce, při převodu řetězce na **jeden** pomocí metody **ToDouble –** .  
  
|Platný vstupní parametr řetězce|Typ výstupu .NET Framework|  
|----------------------------------|--------------------------------|  
|"INF"|Double. PositiveInfinity|  
|"-INF"|Double. NegativeInfinity|  
  
 Následující kód zapisuje `<Infinity>INF</Infinity>`:  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>Viz také

- [Převod datových typů XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [Převádění typů rozhraní .NET Framework na řetězce](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
