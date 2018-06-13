---
title: Třída XsltArgumentList pro parametry list stylu a rozšíření objekty
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 808d21ae0eabdc7502ef97facc3d45f2220883af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576806"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a><span data-ttu-id="5c4f3-102">Třída XsltArgumentList pro parametry list stylu a rozšíření objekty</span><span class="sxs-lookup"><span data-stu-id="5c4f3-102">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>
<span data-ttu-id="5c4f3-103"><xref:System.Xml.Xsl.XsltArgumentList> Třída obsahuje jazyk XSL pro parametry transformace XSLT () a objektů rozšíření XSLT.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-103">The <xref:System.Xml.Xsl.XsltArgumentList> class contains Extensible Stylesheet Language for Transformations (XSLT) parameters and XSLT extension objects.</span></span> <span data-ttu-id="5c4f3-104">Když předána do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu, tyto parametry a rozšíření objektů můžete vyvolat z šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-104">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c4f3-105"><xref:System.Xml.Xsl.XslTransform> a <xref:System.Xml.Xsl.XsltArgumentList> třídy jsou v zastaralé [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c4f3-105">The <xref:System.Xml.Xsl.XslTransform> and <xref:System.Xml.Xsl.XsltArgumentList> classes are obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="5c4f3-106">Můžete provést pomocí transformace XSLT <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-106">You can perform XSLT transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="5c4f3-107">V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="5c4f3-108"><xref:System.Xml.Xsl.XsltArgumentList> Třída obsahuje parametry XSLT a objektů rozšíření XSLT.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-108">The <xref:System.Xml.Xsl.XsltArgumentList> class contains XSLT parameters and XSLT extension objects.</span></span> <span data-ttu-id="5c4f3-109">Když předána do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu, tyto parametry a rozšíření objektů můžete vyvolat z šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-109">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
 <span data-ttu-id="5c4f3-110">Následují výhody předávání objektů, místo používání vložený skript:</span><span class="sxs-lookup"><span data-stu-id="5c4f3-110">The following are advantages to passing an object rather than using an embedded script:</span></span>  
  
-   <span data-ttu-id="5c4f3-111">Poskytuje lepší zapouzdření a opakovaného použití třídy.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-111">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="5c4f3-112">Umožňuje stylů menší a více udržovatelný.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-112">Allows style sheets to be smaller and more maintainable.</span></span>  
  
-   <span data-ttu-id="5c4f3-113">Podporuje volání metod na třídy, které patří do obory názvů, než jsou definovány v rámci sady podporované <xref:System> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-113">Supports calling methods on classes belonging to namespaces other than those defined within the set of supported <xref:System> namespaces.</span></span>  
  
-   <span data-ttu-id="5c4f3-114">Podporuje předávání stromu fragmenty výsledek šablony stylů s použitím <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-114">Supports passing result tree fragments to the style sheet with the use of the <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
## <a name="xslt-style-sheet-parameters"></a><span data-ttu-id="5c4f3-115">Parametry list stylu XSLT</span><span class="sxs-lookup"><span data-stu-id="5c4f3-115">XSLT Style Sheet Parameters</span></span>  
 <span data-ttu-id="5c4f3-116">Parametry XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-116">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="5c4f3-117">Kvalifikovaný název a obor názvů identifikátor URI (Uniform Resource) jsou přidruženy k objektu parametru v daném čase.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-117">A qualified name and namespace Uniform Resource Identifier (URI) are associated with the parameter object at that time.</span></span>  
  
 <span data-ttu-id="5c4f3-118">Objekt parametr by měl odpovídat typu World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="5c4f3-118">The parameter object should correspond to a World Wide Web Consortium (W3C) type.</span></span> <span data-ttu-id="5c4f3-119">Následující tabulka uvádí odpovídající typy W3C ekvivalent [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] třídy (typ), a zda je typ W3C typ XML Path Language (XPath) nebo typ XSLT.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-119">The following table shows the corresponding W3C types, the equivalent [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes (type), and whether the W3C type is an XML Path Language (XPath) type or XSLT type.</span></span>  
  
|<span data-ttu-id="5c4f3-120">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="5c4f3-120">W3C Type</span></span>|<span data-ttu-id="5c4f3-121">Ekvivalentní třídy rozhraní .NET Framework (typ)</span><span class="sxs-lookup"><span data-stu-id="5c4f3-121">Equivalent .NET Framework class (type)</span></span>|<span data-ttu-id="5c4f3-122">Výraz XPath typ nebo typ XSLT</span><span class="sxs-lookup"><span data-stu-id="5c4f3-122">XPath type or XSLT type</span></span>|  
|--------------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="5c4f3-123">String</span><span class="sxs-lookup"><span data-stu-id="5c4f3-123">String</span></span>|<span data-ttu-id="5c4f3-124">System.String</span><span class="sxs-lookup"><span data-stu-id="5c4f3-124">System.String</span></span>|<span data-ttu-id="5c4f3-125">XPath</span><span class="sxs-lookup"><span data-stu-id="5c4f3-125">XPath</span></span>|  
|<span data-ttu-id="5c4f3-126">Boolean</span><span class="sxs-lookup"><span data-stu-id="5c4f3-126">Boolean</span></span>|<span data-ttu-id="5c4f3-127">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="5c4f3-127">System.Boolean</span></span>|<span data-ttu-id="5c4f3-128">XPath</span><span class="sxs-lookup"><span data-stu-id="5c4f3-128">XPath</span></span>|  
|<span data-ttu-id="5c4f3-129">Číslo</span><span class="sxs-lookup"><span data-stu-id="5c4f3-129">Number</span></span>|<span data-ttu-id="5c4f3-130">System.Double</span><span class="sxs-lookup"><span data-stu-id="5c4f3-130">System.Double</span></span>|<span data-ttu-id="5c4f3-131">XPath</span><span class="sxs-lookup"><span data-stu-id="5c4f3-131">XPath</span></span>|  
|<span data-ttu-id="5c4f3-132">Fragment výsledek stromu</span><span class="sxs-lookup"><span data-stu-id="5c4f3-132">Result Tree Fragment</span></span>|<span data-ttu-id="5c4f3-133">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5c4f3-133">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="5c4f3-134">XSLT</span><span class="sxs-lookup"><span data-stu-id="5c4f3-134">XSLT</span></span>|  
|<span data-ttu-id="5c4f3-135">Sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-135">Node Set</span></span>|<span data-ttu-id="5c4f3-136">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="5c4f3-136">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="5c4f3-137">XPath</span><span class="sxs-lookup"><span data-stu-id="5c4f3-137">XPath</span></span>|  
  
 <span data-ttu-id="5c4f3-138">Pokud objekt parametr není jedním z výše uvedených třídy, je nucen se dvojitou hodnotu nebo řetězec, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-138">If the parameter object is not one of the above classes, it is forced to either a Double or String, as appropriate.</span></span> <span data-ttu-id="5c4f3-139">Typy Int16, UInt16, Int32, UInt32, Int64, UInt64, jedním a Decimal, vynuceně přesunuty do datový typ Double.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, Single and Decimal types are forced to a Double.</span></span> <span data-ttu-id="5c4f3-140">Jsou všechny ostatní typy vynucené na řetězec pomocí `ToString` metoda.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-140">All other types are forced to a String using the `ToString` method.</span></span>  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a><span data-ttu-id="5c4f3-141">Pro parametr XSLT, musí uživatel postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="5c4f3-141">To use the XSLT parameter, the user needs to do the following:</span></span>  
  
1.  <span data-ttu-id="5c4f3-142">Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> a přidat objekty pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-142">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the objects using <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span></span>  
  
2.  <span data-ttu-id="5c4f3-143">Volání parametry z této šablony.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-143">Call the parameters from the style sheet.</span></span>  
  
3.  <span data-ttu-id="5c4f3-144">Předat <xref:System.Xml.Xsl.XsltArgumentList> k <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-144">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="5c4f3-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c4f3-145">Example</span></span>  
 <span data-ttu-id="5c4f3-146">Následující příklad používá <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodu pro vytvoření parametr pro uložení data počítané slevy.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-146">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold a calculated discount date.</span></span> <span data-ttu-id="5c4f3-147">Datum slevy je vypočítána na 20 dní od data pořadí.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-147">The discount date is calculated to be 20 days from the order date.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
    writer.Close()  
  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="5c4f3-148">Vstup</span><span class="sxs-lookup"><span data-stu-id="5c4f3-148">Input</span></span>  
 <span data-ttu-id="5c4f3-149">Order.XML</span><span class="sxs-lookup"><span data-stu-id="5c4f3-149">order.xml</span></span>  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 <span data-ttu-id="5c4f3-150">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="5c4f3-150">discount.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="5c4f3-151">Výstup</span><span class="sxs-lookup"><span data-stu-id="5c4f3-151">Output</span></span>  
  
```xml  
<order>  
   <total>36.9</total>   
   15% discount if paid by: 5/6/2001 5:01:15 PM   
</order>  
```  
  
## <a name="xslt-extension-objects"></a><span data-ttu-id="5c4f3-152">Rozšíření objektů XSLT</span><span class="sxs-lookup"><span data-stu-id="5c4f3-152">XSLT Extension Objects</span></span>  
 <span data-ttu-id="5c4f3-153">XSLT rozšíření objekty jsou přidány na <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-153">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="5c4f3-154">Úplný název a identifikátor URI oboru názvů jsou přidruženy k rozšíření objektu v daném čase.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-154">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
 <span data-ttu-id="5c4f3-155">Když je objekt přidán, volající <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> musí být plně důvěryhodný v zásadě zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-155">When an object is added, the caller of the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> must be fully trusted in the security policy.</span></span> <span data-ttu-id="5c4f3-156">Pokud je částečně důvěryhodné volající, přidání selže.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-156">If the caller is semi-trusted, the addition will fail.</span></span>  
  
 <span data-ttu-id="5c4f3-157">I když je objekt úspěšně přidán, nezaručuje to, že bude úspěšné provedení.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-157">Though an object is added successfully, it does not guarantee that the execution will be successful.</span></span> <span data-ttu-id="5c4f3-158">Když <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda je volána, oprávnění jsou vypočtena podle důkaz uvedených v <xref:System.Xml.Xsl.XslTransform.Load%2A> čas a jestli je k transformaci celý proces přiřazená oprávnění sady.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-158">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at <xref:System.Xml.Xsl.XslTransform.Load%2A> time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="5c4f3-159">Pokud objekt rozšíření se pokusí spustit akci, která vyžaduje oprávnění nebyl nalezen v sadě, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-159">If an extension object attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
 <span data-ttu-id="5c4f3-160">Datové typy vrácených objektů rozšíření jsou jedním ze čtyř typů základní XPath datové sady číslo, řetězec, logická hodnota a uzlu.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-160">The data types returned from extension objects are one of the four basic XPath data types of number, string, Boolean, and node set.</span></span>  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a><span data-ttu-id="5c4f3-161">Pokud chcete použít objekt XSLT rozšíření, uživatel potřebuje provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="5c4f3-161">To use the XSLT extension object, the user needs to do the following:</span></span>  
  
1.  <span data-ttu-id="5c4f3-162">Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-162">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span></span>  
  
2.  <span data-ttu-id="5c4f3-163">Vyvolání objekt rozšíření z této šablony.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-163">Invoke the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="5c4f3-164">Předat <xref:System.Xml.Xsl.XsltArgumentList> k <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-164">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="5c4f3-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c4f3-165">Example</span></span>  
 <span data-ttu-id="5c4f3-166">Následující příklad vypočítá obvodu kruhu zadané jeho protokolu radius.</span><span class="sxs-lookup"><span data-stu-id="5c4f3-166">The following example calculates the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate{  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="5c4f3-167">Vstup</span><span class="sxs-lookup"><span data-stu-id="5c4f3-167">Input</span></span>  
 <span data-ttu-id="5c4f3-168">Number.XML</span><span class="sxs-lookup"><span data-stu-id="5c4f3-168">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>    
```  
  
 <span data-ttu-id="5c4f3-169">Circle.xsl</span><span class="sxs-lookup"><span data-stu-id="5c4f3-169">circle.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>          
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="5c4f3-170">Výstup</span><span class="sxs-lookup"><span data-stu-id="5c4f3-170">Output</span></span>  
 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a><span data-ttu-id="5c4f3-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c4f3-171">See Also</span></span>  
 [<span data-ttu-id="5c4f3-172">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="5c4f3-172">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
