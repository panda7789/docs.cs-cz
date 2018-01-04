---
title: "Převádění řetězců na rozhraní .NET Framework datové typy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d21667ada5592c62824a97b4a8a9b8127abab75a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="converting-strings-to-net-framework-data-types"></a>Převádění řetězců na rozhraní .NET Framework datové typy
Pokud chcete převést řetězec na datový typ rozhraní .NET Framework, použijte **XmlConvert** metoda, která vyhovuje potřebám aplikace. Seznam všech metod pro převod k dispozici v **XmlConvert** třídy najdete v tématu <xref:System.Xml.XmlConvert>.  
  
 Řetězec vrácený z **ToString** metoda je řetězec verze dat, který se předává v. Kromě toho existuje několik typů rozhraní .NET Framework, které převést pomocí **XmlConvert** třídy ještě nepoužívají metody v **metodu System.Convert** třídy. **XmlConvert** třída postupuje podle specifikace typu dat schématu XML (XSD) a má datový typ, který **XmlConvert** můžete namapovat.  
  
 Následující tabulka uvádí typy dat rozhraní .NET Framework a na typ řetězce, které jsou vráceny pomocí mapování datového typu XML schématu (XSD). Tyto typy rozhraní .NET Framework nelze zpracovat pomocí **metodu System.Convert**.  
  
|Typ rozhraní .NET Framework|Byl vrácen řetězec s|  
|-------------------------|---------------------|  
|Boolean|"PRAVDA", "Nepravda"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|Formát je "rrrr-MM-ddTHH:mm:sszzzzzz" a jeho podmnožin.|  
|Časový interval|Formát je PnYnMnTnHnMnS tedy `P2Y10M15DT10H30M20S` je doba trvání 2 roky, 10 měsíců, 15 dnů, 10 hodin, 30 minut, a 20 sekund.|  
  
> [!NOTE]
>  Pokud převod jakýkoli z typů rozhraní .NET Framework uvedené v tabulce na řetězec pomocí **ToString** metoda, vrácený řetězec není základní typ, ale na řetězcový typ. schématu XML (XSD).  
  
 **Data a času** a **časový interval** typ hodnoty se liší v tom, že **data a času** představuje okamžik v čase, zatímco **časový interval** představuje časovém intervalu. **Data a času** a **časový interval** formáty jsou uvedeny ve specifikaci typy dat schématu XML (XSD). Příklad:  
  
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
  
 Následující kód převede na řetězec, celé číslo:  
  
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
  
 Však při převodu řetězce **Boolean**, **jeden**, nebo **dvojité**, typ rozhraní .NET Framework, která je vrácena není stejný jako typ vrácený při použití **Metodu System.Convert** třídy.  
  
## <a name="string-to-boolean"></a>Řetězec na logickou hodnotu  
 Následující tabulka ukazuje, jaký typ se generuje pro daný vstupní řetězce při převodu řetězce **Boolean** pomocí **ToBoolean** metoda.  
  
|Vstupní parametr platný řetězec|Výstupní typ rozhraní .NET framework|  
|----------------------------------|--------------------------------|  
|"true"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|"0"|Boolean.False|  
  
 Například uděleno následující kód XML:  
  
 **Vstup**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 Obě srozumitelné následující kód, a **bvalue** je **System.Boolean.True**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>Řetězec, který má jeden  
 Následující tabulka ukazuje, jaký typ se generuje pro daný vstupní řetězce při převodu řetězce **jeden** pomocí **ToSingle** metoda.  
  
|Vstupní parametr platný řetězec|Výstupní typ rozhraní .NET framework|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>Řetězec dvojitou  
 Následující tabulka ukazuje, jaký typ se generuje pro daný vstupní řetězce při převodu řetězce **jeden** pomocí **ToDouble** metoda.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Převod datových typů XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [Převádění typů rozhraní .NET Framework na řetězce](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
