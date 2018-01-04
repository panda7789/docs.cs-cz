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
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="dae70-102">Převádění řetězců na rozhraní .NET Framework datové typy</span><span class="sxs-lookup"><span data-stu-id="dae70-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="dae70-103">Pokud chcete převést řetězec na datový typ rozhraní .NET Framework, použijte **XmlConvert** metoda, která vyhovuje potřebám aplikace.</span><span class="sxs-lookup"><span data-stu-id="dae70-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="dae70-104">Seznam všech metod pro převod k dispozici v **XmlConvert** třídy najdete v tématu <xref:System.Xml.XmlConvert>.</span><span class="sxs-lookup"><span data-stu-id="dae70-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="dae70-105">Řetězec vrácený z **ToString** metoda je řetězec verze dat, který se předává v.</span><span class="sxs-lookup"><span data-stu-id="dae70-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="dae70-106">Kromě toho existuje několik typů rozhraní .NET Framework, které převést pomocí **XmlConvert** třídy ještě nepoužívají metody v **metodu System.Convert** třídy.</span><span class="sxs-lookup"><span data-stu-id="dae70-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="dae70-107">**XmlConvert** třída postupuje podle specifikace typu dat schématu XML (XSD) a má datový typ, který **XmlConvert** můžete namapovat.</span><span class="sxs-lookup"><span data-stu-id="dae70-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="dae70-108">Následující tabulka uvádí typy dat rozhraní .NET Framework a na typ řetězce, které jsou vráceny pomocí mapování datového typu XML schématu (XSD).</span><span class="sxs-lookup"><span data-stu-id="dae70-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="dae70-109">Tyto typy rozhraní .NET Framework nelze zpracovat pomocí **metodu System.Convert**.</span><span class="sxs-lookup"><span data-stu-id="dae70-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="dae70-110">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dae70-110">.NET Framework type</span></span>|<span data-ttu-id="dae70-111">Byl vrácen řetězec s</span><span class="sxs-lookup"><span data-stu-id="dae70-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="dae70-112">Boolean</span><span class="sxs-lookup"><span data-stu-id="dae70-112">Boolean</span></span>|<span data-ttu-id="dae70-113">"PRAVDA", "Nepravda"</span><span class="sxs-lookup"><span data-stu-id="dae70-113">"true", "false"</span></span>|  
|<span data-ttu-id="dae70-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="dae70-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="dae70-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="dae70-115">"INF"</span></span>|  
|<span data-ttu-id="dae70-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="dae70-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="dae70-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="dae70-117">"-INF"</span></span>|  
|<span data-ttu-id="dae70-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="dae70-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="dae70-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="dae70-119">"INF"</span></span>|  
|<span data-ttu-id="dae70-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="dae70-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="dae70-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="dae70-121">"-INF"</span></span>|  
|<span data-ttu-id="dae70-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="dae70-122">DateTime</span></span>|<span data-ttu-id="dae70-123">Formát je "rrrr-MM-ddTHH:mm:sszzzzzz" a jeho podmnožin.</span><span class="sxs-lookup"><span data-stu-id="dae70-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="dae70-124">Časový interval</span><span class="sxs-lookup"><span data-stu-id="dae70-124">Timespan</span></span>|<span data-ttu-id="dae70-125">Formát je PnYnMnTnHnMnS tedy `P2Y10M15DT10H30M20S` je doba trvání 2 roky, 10 měsíců, 15 dnů, 10 hodin, 30 minut, a 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="dae70-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="dae70-126">Pokud převod jakýkoli z typů rozhraní .NET Framework uvedené v tabulce na řetězec pomocí **ToString** metoda, vrácený řetězec není základní typ, ale na řetězcový typ. schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="dae70-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="dae70-127">**Data a času** a **časový interval** typ hodnoty se liší v tom, že **data a času** představuje okamžik v čase, zatímco **časový interval** představuje časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="dae70-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="dae70-128">**Data a času** a **časový interval** formáty jsou uvedeny ve specifikaci typy dat schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="dae70-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="dae70-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="dae70-129">For example:</span></span>  
  
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
  
 <span data-ttu-id="dae70-130">**Output**</span><span class="sxs-lookup"><span data-stu-id="dae70-130">**Output**</span></span>  
  
 <span data-ttu-id="dae70-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="dae70-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="dae70-132">Následující kód převede na řetězec, celé číslo:</span><span class="sxs-lookup"><span data-stu-id="dae70-132">The following code converts an integer to a string:</span></span>  
  
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
  
 <span data-ttu-id="dae70-133">**Output**</span><span class="sxs-lookup"><span data-stu-id="dae70-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="dae70-134">Však při převodu řetězce **Boolean**, **jeden**, nebo **dvojité**, typ rozhraní .NET Framework, která je vrácena není stejný jako typ vrácený při použití **Metodu System.Convert** třídy.</span><span class="sxs-lookup"><span data-stu-id="dae70-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="dae70-135">Řetězec na logickou hodnotu</span><span class="sxs-lookup"><span data-stu-id="dae70-135">String to Boolean</span></span>  
 <span data-ttu-id="dae70-136">Následující tabulka ukazuje, jaký typ se generuje pro daný vstupní řetězce při převodu řetězce **Boolean** pomocí **ToBoolean** metoda.</span><span class="sxs-lookup"><span data-stu-id="dae70-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="dae70-137">Vstupní parametr platný řetězec</span><span class="sxs-lookup"><span data-stu-id="dae70-137">Valid string input parameter</span></span>|<span data-ttu-id="dae70-138">Výstupní typ rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="dae70-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="dae70-139">"true"</span><span class="sxs-lookup"><span data-stu-id="dae70-139">"true"</span></span>|<span data-ttu-id="dae70-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="dae70-140">Boolean.True</span></span>|  
|<span data-ttu-id="dae70-141">"1"</span><span class="sxs-lookup"><span data-stu-id="dae70-141">"1"</span></span>|<span data-ttu-id="dae70-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="dae70-142">Boolean.True</span></span>|  
|<span data-ttu-id="dae70-143">"false"</span><span class="sxs-lookup"><span data-stu-id="dae70-143">"false"</span></span>|<span data-ttu-id="dae70-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="dae70-144">Boolean.False</span></span>|  
|<span data-ttu-id="dae70-145">"0"</span><span class="sxs-lookup"><span data-stu-id="dae70-145">"0"</span></span>|<span data-ttu-id="dae70-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="dae70-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="dae70-147">Například uděleno následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="dae70-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="dae70-148">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="dae70-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 <span data-ttu-id="dae70-149">Obě srozumitelné následující kód, a **bvalue** je **System.Boolean.True**:</span><span class="sxs-lookup"><span data-stu-id="dae70-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="dae70-150">Řetězec, který má jeden</span><span class="sxs-lookup"><span data-stu-id="dae70-150">String to Single</span></span>  
 <span data-ttu-id="dae70-151">Následující tabulka ukazuje, jaký typ se generuje pro daný vstupní řetězce při převodu řetězce **jeden** pomocí **ToSingle** metoda.</span><span class="sxs-lookup"><span data-stu-id="dae70-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="dae70-152">Vstupní parametr platný řetězec</span><span class="sxs-lookup"><span data-stu-id="dae70-152">Valid string input parameter</span></span>|<span data-ttu-id="dae70-153">Výstupní typ rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="dae70-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="dae70-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="dae70-154">"INF"</span></span>|<span data-ttu-id="dae70-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="dae70-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="dae70-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="dae70-156">"-INF"</span></span>|<span data-ttu-id="dae70-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="dae70-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="dae70-158">Řetězec dvojitou</span><span class="sxs-lookup"><span data-stu-id="dae70-158">String to Double</span></span>  
 <span data-ttu-id="dae70-159">Následující tabulka ukazuje, jaký typ se generuje pro daný vstupní řetězce při převodu řetězce **jeden** pomocí **ToDouble** metoda.</span><span class="sxs-lookup"><span data-stu-id="dae70-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="dae70-160">Vstupní parametr platný řetězec</span><span class="sxs-lookup"><span data-stu-id="dae70-160">Valid string input parameter</span></span>|<span data-ttu-id="dae70-161">Výstupní typ rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="dae70-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="dae70-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="dae70-162">"INF"</span></span>|<span data-ttu-id="dae70-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="dae70-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="dae70-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="dae70-164">"-INF"</span></span>|<span data-ttu-id="dae70-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="dae70-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="dae70-166">Následující kód zápisy `<Infinity>INF</Infinity>`:</span><span class="sxs-lookup"><span data-stu-id="dae70-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="dae70-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="dae70-167">See Also</span></span>  
 [<span data-ttu-id="dae70-168">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="dae70-168">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [<span data-ttu-id="dae70-169">Převádění typů rozhraní .NET Framework na řetězce</span><span class="sxs-lookup"><span data-stu-id="dae70-169">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
