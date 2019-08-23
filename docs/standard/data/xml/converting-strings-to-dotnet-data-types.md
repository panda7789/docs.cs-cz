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
ms.openlocfilehash: 31f277d11cba8191c326d56f017b8acc6503c6b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968715"
---
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="12b48-102">Převádění řetězců na datové typy rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="12b48-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="12b48-103">Chcete-li převést řetězec na datový typ .NET Framework, použijte metodu **XmlConvert** , která odpovídá požadavkům aplikace.</span><span class="sxs-lookup"><span data-stu-id="12b48-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="12b48-104">Seznam všech metod převodu, které jsou k dispozici ve třídě **XmlConvert** , <xref:System.Xml.XmlConvert>naleznete v tématu.</span><span class="sxs-lookup"><span data-stu-id="12b48-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="12b48-105">Řetězec vrácený metodou **ToString** je řetězcová verze dat, která je předána.</span><span class="sxs-lookup"><span data-stu-id="12b48-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="12b48-106">Kromě toho existuje několik typů .NET Framework, které se převádějí pomocí třídy **XmlConvert** , ale nepoužívají metody ve třídě **System. Convert** .</span><span class="sxs-lookup"><span data-stu-id="12b48-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="12b48-107">Třída **XmlConvert** se řídí specifikací datového typu XSD (XML Schema) a má datový typ, na který může **XmlConvert** mapovat.</span><span class="sxs-lookup"><span data-stu-id="12b48-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="12b48-108">V následující tabulce jsou uvedeny .NET Framework datové typy a typy řetězců, které jsou vráceny pomocí mapování datových typů schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="12b48-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="12b48-109">Tyto typy .NET Framework nelze zpracovat pomocí **System. Convert**.</span><span class="sxs-lookup"><span data-stu-id="12b48-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="12b48-110">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="12b48-110">.NET Framework type</span></span>|<span data-ttu-id="12b48-111">Vrácený řetězec</span><span class="sxs-lookup"><span data-stu-id="12b48-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="12b48-112">Boolean</span><span class="sxs-lookup"><span data-stu-id="12b48-112">Boolean</span></span>|<span data-ttu-id="12b48-113">"pravda", "NEPRAVDA"</span><span class="sxs-lookup"><span data-stu-id="12b48-113">"true", "false"</span></span>|  
|<span data-ttu-id="12b48-114">Single. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="12b48-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="12b48-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="12b48-115">"INF"</span></span>|  
|<span data-ttu-id="12b48-116">Single. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="12b48-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="12b48-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="12b48-117">"-INF"</span></span>|  
|<span data-ttu-id="12b48-118">Double. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="12b48-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="12b48-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="12b48-119">"INF"</span></span>|  
|<span data-ttu-id="12b48-120">Double. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="12b48-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="12b48-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="12b48-121">"-INF"</span></span>|  
|<span data-ttu-id="12b48-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="12b48-122">DateTime</span></span>|<span data-ttu-id="12b48-123">Formát je "rrrr-MM-ddTHH: mm: sszzzzzz" a jeho podmnožiny.</span><span class="sxs-lookup"><span data-stu-id="12b48-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="12b48-124">Timespan</span><span class="sxs-lookup"><span data-stu-id="12b48-124">Timespan</span></span>|<span data-ttu-id="12b48-125">Formát je PnYnMnTnHnMnS, což `P2Y10M15DT10H30M20S` je doba 2 roky, 10 měsíců, 15 dní, 10 hodin, 30 minut a 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="12b48-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="12b48-126">Pokud převedete některý z .NET Framework typů uvedených v tabulce na řetězec pomocí metody **ToString** , vrácený řetězec není základní typ, ale typ řetězce XML Schema (XSD).</span><span class="sxs-lookup"><span data-stu-id="12b48-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="12b48-127">Typ hodnoty **DateTime** a **TimeSpan** se liší v tom, že hodnota DateTime představuje okamžitý čas, zatímco **hodnota** **TimeSpan** představuje časový interval.</span><span class="sxs-lookup"><span data-stu-id="12b48-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="12b48-128">Formáty **DateTime** a **TimeSpan** jsou zadány ve specifikaci datových typů schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="12b48-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="12b48-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="12b48-129">For example:</span></span>  
  
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
  
 <span data-ttu-id="12b48-130">**Output**</span><span class="sxs-lookup"><span data-stu-id="12b48-130">**Output**</span></span>  
  
 <span data-ttu-id="12b48-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="12b48-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="12b48-132">Následující kód převede celé číslo na řetězec:</span><span class="sxs-lookup"><span data-stu-id="12b48-132">The following code converts an integer to a string:</span></span>  
  
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
  
 <span data-ttu-id="12b48-133">**Output**</span><span class="sxs-lookup"><span data-stu-id="12b48-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="12b48-134">Nicméně pokud převádíte řetězec na **Boolean**, **Single**nebo **Double**, typ .NET Framework, který je vrácen, není stejný jako typ vrácený při použití třídy **System. Convert** .</span><span class="sxs-lookup"><span data-stu-id="12b48-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="12b48-135">Řetězec na logickou hodnotu</span><span class="sxs-lookup"><span data-stu-id="12b48-135">String to Boolean</span></span>  
 <span data-ttu-id="12b48-136">Následující tabulka ukazuje, jaký typ je vygenerován pro dané vstupní řetězce, při převodu řetězce na **logickou hodnotu** pomocí metody **ToBoolean** .</span><span class="sxs-lookup"><span data-stu-id="12b48-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="12b48-137">Platný vstupní parametr řetězce</span><span class="sxs-lookup"><span data-stu-id="12b48-137">Valid string input parameter</span></span>|<span data-ttu-id="12b48-138">Typ výstupu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="12b48-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="12b48-139">podmínka</span><span class="sxs-lookup"><span data-stu-id="12b48-139">"true"</span></span>|<span data-ttu-id="12b48-140">Logická hodnota. true</span><span class="sxs-lookup"><span data-stu-id="12b48-140">Boolean.True</span></span>|  
|<span data-ttu-id="12b48-141">"1"</span><span class="sxs-lookup"><span data-stu-id="12b48-141">"1"</span></span>|<span data-ttu-id="12b48-142">Logická hodnota. true</span><span class="sxs-lookup"><span data-stu-id="12b48-142">Boolean.True</span></span>|  
|<span data-ttu-id="12b48-143">chybné</span><span class="sxs-lookup"><span data-stu-id="12b48-143">"false"</span></span>|<span data-ttu-id="12b48-144">Boolean. false</span><span class="sxs-lookup"><span data-stu-id="12b48-144">Boolean.False</span></span>|  
|<span data-ttu-id="12b48-145">"0"</span><span class="sxs-lookup"><span data-stu-id="12b48-145">"0"</span></span>|<span data-ttu-id="12b48-146">Boolean. false</span><span class="sxs-lookup"><span data-stu-id="12b48-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="12b48-147">Například s ohledem na následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="12b48-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="12b48-148">**Vstup**</span><span class="sxs-lookup"><span data-stu-id="12b48-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 <span data-ttu-id="12b48-149">Obojí lze chápat pomocí následujícího kódu a **bValue** je **System. Boolean. true**:</span><span class="sxs-lookup"><span data-stu-id="12b48-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="12b48-150">Řetězec na jeden</span><span class="sxs-lookup"><span data-stu-id="12b48-150">String to Single</span></span>  
 <span data-ttu-id="12b48-151">Následující tabulka ukazuje, jaký typ je vygenerován pro dané vstupní řetězce, při převodu řetězce na **jeden** pomocí metody **ToSingle –** .</span><span class="sxs-lookup"><span data-stu-id="12b48-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="12b48-152">Platný vstupní parametr řetězce</span><span class="sxs-lookup"><span data-stu-id="12b48-152">Valid string input parameter</span></span>|<span data-ttu-id="12b48-153">Typ výstupu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="12b48-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="12b48-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="12b48-154">"INF"</span></span>|<span data-ttu-id="12b48-155">Single. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="12b48-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="12b48-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="12b48-156">"-INF"</span></span>|<span data-ttu-id="12b48-157">Single. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="12b48-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="12b48-158">Řetězec, který se má zdvojnásobit</span><span class="sxs-lookup"><span data-stu-id="12b48-158">String to Double</span></span>  
 <span data-ttu-id="12b48-159">Následující tabulka ukazuje, jaký typ je vygenerován pro dané vstupní řetězce, při převodu řetězce na **jeden** pomocí metody **ToDouble –** .</span><span class="sxs-lookup"><span data-stu-id="12b48-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="12b48-160">Platný vstupní parametr řetězce</span><span class="sxs-lookup"><span data-stu-id="12b48-160">Valid string input parameter</span></span>|<span data-ttu-id="12b48-161">Typ výstupu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="12b48-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="12b48-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="12b48-162">"INF"</span></span>|<span data-ttu-id="12b48-163">Double. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="12b48-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="12b48-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="12b48-164">"-INF"</span></span>|<span data-ttu-id="12b48-165">Double. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="12b48-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="12b48-166">Následující zápis `<Infinity>INF</Infinity>`kódu:</span><span class="sxs-lookup"><span data-stu-id="12b48-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="12b48-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12b48-167">See also</span></span>

- [<span data-ttu-id="12b48-168">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="12b48-168">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="12b48-169">Převádění typů rozhraní .NET Framework na řetězce</span><span class="sxs-lookup"><span data-stu-id="12b48-169">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
