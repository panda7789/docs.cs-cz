---
title: Převádění řetězců na datové typy rozhraní .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 376dd9df4666193f8e5a6be83f3fcaf5dc32f1a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027261"
---
# <a name="converting-strings-to-net-framework-data-types"></a>Převádění řetězců na datové typy rozhraní .NET Framework
Pokud chcete pro převod řetězce na datový typ rozhraní .NET Framework, použijte **XmlConvert** metodu, která vyhovuje potřebám aplikace. Pro všechny metody převodu k dispozici v seznamu **XmlConvert** najdete v tématu <xref:System.Xml.XmlConvert>.  
  
 Řetězec vrácený z **ToString** metody je řetězec verze dat, které je předáno. Kromě toho existuje několik typů rozhraní .NET Framework, které provádějí převod pomocí **XmlConvert** třídy, ale nepoužívají metody v **System.Convert** třídy. **XmlConvert** třídy následuje specifikace datového typu schématu XML (XSD) a má datový typ, který **XmlConvert** namapovat.  
  
 V následující tabulce jsou uvedeny datové typy rozhraní .NET Framework a typy řetězců, které jsou vráceny za použití mapování datového typu schématu XML (XSD). Tyto typy rozhraní .NET Framework nelze zpracovat pomocí **System.Convert**.  
  
|Typ rozhraní .NET Framework|Řetězec vrácený|  
|-------------------------|---------------------|  
|Boolean|"PRAVDA", "Nepravda"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|Formát je "yyyy-MM-ddTHH:mm:sszzzzzz" a její podskupiny.|  
|Časový interval|Formát je PnYnMnTnHnMnS tedy `P2Y10M15DT10H30M20S` je po dobu 2 let, 10 měsíců, 15 dnů, 10 hodin, 30 minut, a 20 sekund.|  
  
> [!NOTE]
>  Pokud převod typy rozhraní .NET Framework uvedená v tabulce na řetězec pomocí **ToString** metodu, vrácený řetězec není základní typ, ale typ řetězce schématu XML (XSD).  
  
 **Data a času** a **časový interval** typ hodnoty se liší v, který **data a času** představuje okamžik v čase, zatímco **TimeSpan** představuje časový interval. **Data a času** a **Timespan** jsou formáty určené ve specifikaci schématu XML (XSD) datové typy. Příklad:  
  
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
  
 **Output**  
  
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
  
 **Output**  
  
 `<Number>200</Number>`  
  
 Ale pokud převádíte řetězec na **logická**, **jeden**, nebo **Double**, typ rozhraní .NET Framework, která je vrácena není stejný jako typ vrácený při použití **System.Convert** třídy.  
  
## <a name="string-to-boolean"></a>Řetězec na logickou hodnotu  
 Následující tabulka ukazuje, jaký typ je generován pro daný vstupní řetězce při převodu řetězce do **logická** pomocí **ToBoolean** metody.  
  
|Vstupní parametr platný řetězec|Výstupní typ rozhraní .NET framework|  
|----------------------------------|--------------------------------|  
|"true"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|"0"|Boolean.False|  
  
 Mějme například následující kód XML:  
  
 **Vstup**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 Obě byly srozumitelné pro následující kód a **bvalue** je **System.Boolean.True**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>Řetězec na hodnotu Single  
 Následující tabulka ukazuje, jaký typ je generován pro daný vstupní řetězce při převodu řetězce k **jeden** pomocí **tosingle –** metody.  
  
|Vstupní parametr platný řetězec|Výstupní typ rozhraní .NET framework|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>Řetězec na Double  
 Následující tabulka ukazuje, jaký typ je generován pro daný vstupní řetězce při převodu řetězce k **jeden** pomocí **todouble –** metody.  
  
|Vstupní parametr platný řetězec|Výstupní typ rozhraní .NET framework|  
|----------------------------------|--------------------------------|  
|"INF"|Double.PositiveInfinity|  
|"-INF"|Double.NegativeInfinity|  
  
 Následující kód zápisy `<Infinity>INF</Infinity>`:  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>Viz také:

- [Převod datových typů XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [Převádění typů rozhraní .NET Framework na řetězce](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
