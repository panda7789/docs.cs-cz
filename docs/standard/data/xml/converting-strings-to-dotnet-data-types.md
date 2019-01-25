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
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544598"
---
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="a181a-102">Převádění řetězců na datové typy rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a181a-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="a181a-103">Pokud chcete pro převod řetězce na datový typ rozhraní .NET Framework, použijte **XmlConvert** metodu, která vyhovuje potřebám aplikace.</span><span class="sxs-lookup"><span data-stu-id="a181a-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="a181a-104">Pro všechny metody převodu k dispozici v seznamu **XmlConvert** najdete v tématu <xref:System.Xml.XmlConvert>.</span><span class="sxs-lookup"><span data-stu-id="a181a-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="a181a-105">Řetězec vrácený z **ToString** metody je řetězec verze dat, které je předáno.</span><span class="sxs-lookup"><span data-stu-id="a181a-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="a181a-106">Kromě toho existuje několik typů rozhraní .NET Framework, které provádějí převod pomocí **XmlConvert** třídy, ale nepoužívají metody v **System.Convert** třídy.</span><span class="sxs-lookup"><span data-stu-id="a181a-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="a181a-107">**XmlConvert** třídy následuje specifikace datového typu schématu XML (XSD) a má datový typ, který **XmlConvert** namapovat.</span><span class="sxs-lookup"><span data-stu-id="a181a-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="a181a-108">V následující tabulce jsou uvedeny datové typy rozhraní .NET Framework a typy řetězců, které jsou vráceny za použití mapování datového typu schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="a181a-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="a181a-109">Tyto typy rozhraní .NET Framework nelze zpracovat pomocí **System.Convert**.</span><span class="sxs-lookup"><span data-stu-id="a181a-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="a181a-110">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a181a-110">.NET Framework type</span></span>|<span data-ttu-id="a181a-111">Řetězec vrácený</span><span class="sxs-lookup"><span data-stu-id="a181a-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="a181a-112">Boolean</span><span class="sxs-lookup"><span data-stu-id="a181a-112">Boolean</span></span>|<span data-ttu-id="a181a-113">"PRAVDA", "Nepravda"</span><span class="sxs-lookup"><span data-stu-id="a181a-113">"true", "false"</span></span>|  
|<span data-ttu-id="a181a-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="a181a-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="a181a-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="a181a-115">"INF"</span></span>|  
|<span data-ttu-id="a181a-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="a181a-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="a181a-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="a181a-117">"-INF"</span></span>|  
|<span data-ttu-id="a181a-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="a181a-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="a181a-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="a181a-119">"INF"</span></span>|  
|<span data-ttu-id="a181a-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="a181a-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="a181a-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="a181a-121">"-INF"</span></span>|  
|<span data-ttu-id="a181a-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="a181a-122">DateTime</span></span>|<span data-ttu-id="a181a-123">Formát je "yyyy-MM-ddTHH:mm:sszzzzzz" a její podskupiny.</span><span class="sxs-lookup"><span data-stu-id="a181a-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="a181a-124">Časový interval</span><span class="sxs-lookup"><span data-stu-id="a181a-124">Timespan</span></span>|<span data-ttu-id="a181a-125">Formát je PnYnMnTnHnMnS tedy `P2Y10M15DT10H30M20S` je po dobu 2 let, 10 měsíců, 15 dnů, 10 hodin, 30 minut, a 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="a181a-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a181a-126">Pokud převod typy rozhraní .NET Framework uvedená v tabulce na řetězec pomocí **ToString** metodu, vrácený řetězec není základní typ, ale typ řetězce schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="a181a-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="a181a-127">**Data a času** a **časový interval** typ hodnoty se liší v, který **data a času** představuje okamžik v čase, zatímco **TimeSpan** představuje časový interval.</span><span class="sxs-lookup"><span data-stu-id="a181a-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="a181a-128">**Data a času** a **Timespan** jsou formáty určené ve specifikaci schématu XML (XSD) datové typy.</span><span class="sxs-lookup"><span data-stu-id="a181a-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="a181a-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a181a-129">For example:</span></span>  
  
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
  
 <span data-ttu-id="a181a-130">**Output**</span><span class="sxs-lookup"><span data-stu-id="a181a-130">**Output**</span></span>  
  
 <span data-ttu-id="a181a-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="a181a-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="a181a-132">Následující kód převede celé číslo na řetězec:</span><span class="sxs-lookup"><span data-stu-id="a181a-132">The following code converts an integer to a string:</span></span>  
  
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
  
 <span data-ttu-id="a181a-133">**Output**</span><span class="sxs-lookup"><span data-stu-id="a181a-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="a181a-134">Ale pokud převádíte řetězec na **logická**, **jeden**, nebo **Double**, typ rozhraní .NET Framework, která je vrácena není stejný jako typ vrácený při použití **System.Convert** třídy.</span><span class="sxs-lookup"><span data-stu-id="a181a-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="a181a-135">Řetězec na logickou hodnotu</span><span class="sxs-lookup"><span data-stu-id="a181a-135">String to Boolean</span></span>  
 <span data-ttu-id="a181a-136">Následující tabulka ukazuje, jaký typ je generován pro daný vstupní řetězce při převodu řetězce do **logická** pomocí **ToBoolean** metody.</span><span class="sxs-lookup"><span data-stu-id="a181a-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="a181a-137">Vstupní parametr platný řetězec</span><span class="sxs-lookup"><span data-stu-id="a181a-137">Valid string input parameter</span></span>|<span data-ttu-id="a181a-138">Výstupní typ rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="a181a-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="a181a-139">"true"</span><span class="sxs-lookup"><span data-stu-id="a181a-139">"true"</span></span>|<span data-ttu-id="a181a-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="a181a-140">Boolean.True</span></span>|  
|<span data-ttu-id="a181a-141">"1"</span><span class="sxs-lookup"><span data-stu-id="a181a-141">"1"</span></span>|<span data-ttu-id="a181a-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="a181a-142">Boolean.True</span></span>|  
|<span data-ttu-id="a181a-143">"false"</span><span class="sxs-lookup"><span data-stu-id="a181a-143">"false"</span></span>|<span data-ttu-id="a181a-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="a181a-144">Boolean.False</span></span>|  
|<span data-ttu-id="a181a-145">"0"</span><span class="sxs-lookup"><span data-stu-id="a181a-145">"0"</span></span>|<span data-ttu-id="a181a-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="a181a-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="a181a-147">Mějme například následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="a181a-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="a181a-148">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="a181a-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 <span data-ttu-id="a181a-149">Obě byly srozumitelné pro následující kód a **bvalue** je **System.Boolean.True**:</span><span class="sxs-lookup"><span data-stu-id="a181a-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="a181a-150">Řetězec na hodnotu Single</span><span class="sxs-lookup"><span data-stu-id="a181a-150">String to Single</span></span>  
 <span data-ttu-id="a181a-151">Následující tabulka ukazuje, jaký typ je generován pro daný vstupní řetězce při převodu řetězce k **jeden** pomocí **tosingle –** metody.</span><span class="sxs-lookup"><span data-stu-id="a181a-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="a181a-152">Vstupní parametr platný řetězec</span><span class="sxs-lookup"><span data-stu-id="a181a-152">Valid string input parameter</span></span>|<span data-ttu-id="a181a-153">Výstupní typ rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="a181a-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="a181a-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="a181a-154">"INF"</span></span>|<span data-ttu-id="a181a-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="a181a-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="a181a-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="a181a-156">"-INF"</span></span>|<span data-ttu-id="a181a-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="a181a-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="a181a-158">Řetězec na Double</span><span class="sxs-lookup"><span data-stu-id="a181a-158">String to Double</span></span>  
 <span data-ttu-id="a181a-159">Následující tabulka ukazuje, jaký typ je generován pro daný vstupní řetězce při převodu řetězce k **jeden** pomocí **todouble –** metody.</span><span class="sxs-lookup"><span data-stu-id="a181a-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="a181a-160">Vstupní parametr platný řetězec</span><span class="sxs-lookup"><span data-stu-id="a181a-160">Valid string input parameter</span></span>|<span data-ttu-id="a181a-161">Výstupní typ rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="a181a-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="a181a-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="a181a-162">"INF"</span></span>|<span data-ttu-id="a181a-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="a181a-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="a181a-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="a181a-164">"-INF"</span></span>|<span data-ttu-id="a181a-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="a181a-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="a181a-166">Následující kód zápisy `<Infinity>INF</Infinity>`:</span><span class="sxs-lookup"><span data-stu-id="a181a-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="a181a-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a181a-167">See also</span></span>

- [<span data-ttu-id="a181a-168">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="a181a-168">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="a181a-169">Převádění typů rozhraní .NET Framework na řetězce</span><span class="sxs-lookup"><span data-stu-id="a181a-169">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
