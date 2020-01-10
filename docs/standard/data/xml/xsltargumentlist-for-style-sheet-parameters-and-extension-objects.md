---
title: XsltArgumentList pro parametry šablon stylů a objektů rozšíření
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
ms.openlocfilehash: 5cd733d557dabe66145fdbb848c473411d63c62b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709618"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a><span data-ttu-id="a8ea6-102">XsltArgumentList pro parametry šablon stylů a objektů rozšíření</span><span class="sxs-lookup"><span data-stu-id="a8ea6-102">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>
<span data-ttu-id="a8ea6-103">Třída <xref:System.Xml.Xsl.XsltArgumentList> obsahuje rozšiřitelné parametry jazyka StyleSheet (XSLT) a objekty rozšíření XSLT.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-103">The <xref:System.Xml.Xsl.XsltArgumentList> class contains Extensible Stylesheet Language for Transformations (XSLT) parameters and XSLT extension objects.</span></span> <span data-ttu-id="a8ea6-104">Při předání do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> mohou být tyto parametry a objekty rozšíření vyvolány ze šablon stylů.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-104">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8ea6-105">Třídy <xref:System.Xml.Xsl.XslTransform> a <xref:System.Xml.Xsl.XsltArgumentList> jsou v .NET Framework 2,0 zastaralé.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-105">The <xref:System.Xml.Xsl.XslTransform> and <xref:System.Xml.Xsl.XsltArgumentList> classes are obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="a8ea6-106">Transformace XSLT lze provádět pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-106">You can perform XSLT transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="a8ea6-107">Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="a8ea6-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="a8ea6-108">Třída <xref:System.Xml.Xsl.XsltArgumentList> obsahuje parametry XSLT a objekty rozšíření XSLT.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-108">The <xref:System.Xml.Xsl.XsltArgumentList> class contains XSLT parameters and XSLT extension objects.</span></span> <span data-ttu-id="a8ea6-109">Při předání do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> mohou být tyto parametry a objekty rozšíření vyvolány ze šablon stylů.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-109">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
 <span data-ttu-id="a8ea6-110">Níže jsou uvedené výhody pro předání objektu místo použití vloženého skriptu:</span><span class="sxs-lookup"><span data-stu-id="a8ea6-110">The following are advantages to passing an object rather than using an embedded script:</span></span>  
  
- <span data-ttu-id="a8ea6-111">Poskytuje lepší zapouzdření a opakované použití tříd.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-111">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="a8ea6-112">Povoluje, aby byly šablony stylů menší a udržovatelnější.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-112">Allows style sheets to be smaller and more maintainable.</span></span>  
  
- <span data-ttu-id="a8ea6-113">Podporuje volání metod u tříd patřících do oborů názvů, které jsou definovány v rámci množiny podporovaných oborů názvů <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-113">Supports calling methods on classes belonging to namespaces other than those defined within the set of supported <xref:System> namespaces.</span></span>  
  
- <span data-ttu-id="a8ea6-114">Podporuje předávání fragmentů stromu výsledků do předlohy se styly s použitím <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-114">Supports passing result tree fragments to the style sheet with the use of the <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
## <a name="xslt-style-sheet-parameters"></a><span data-ttu-id="a8ea6-115">Parametry šablony stylů XSLT</span><span class="sxs-lookup"><span data-stu-id="a8ea6-115">XSLT Style Sheet Parameters</span></span>  
 <span data-ttu-id="a8ea6-116">Parametry XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> pomocí metody <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-116">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="a8ea6-117">Úplný název a identifikátor URI oboru názvů (Uniform Resource Identifier) jsou v daném okamžiku přidruženy k objektu Parameter.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-117">A qualified name and namespace Uniform Resource Identifier (URI) are associated with the parameter object at that time.</span></span>  
  
 <span data-ttu-id="a8ea6-118">Objekt Parameter by měl odpovídat typu konsorcium World Wide Web (W3C).</span><span class="sxs-lookup"><span data-stu-id="a8ea6-118">The parameter object should correspond to a World Wide Web Consortium (W3C) type.</span></span> <span data-ttu-id="a8ea6-119">V následující tabulce jsou uvedeny odpovídající typy W3C, ekvivalentní .NET Framework třídy (Type) a zda je typ W3C typu jazyk XML Path (XPath) nebo typu XSLT.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-119">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (type), and whether the W3C type is an XML Path Language (XPath) type or XSLT type.</span></span>  
  
|<span data-ttu-id="a8ea6-120">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="a8ea6-120">W3C Type</span></span>|<span data-ttu-id="a8ea6-121">Ekvivalentní třída .NET Framework (typ)</span><span class="sxs-lookup"><span data-stu-id="a8ea6-121">Equivalent .NET Framework class (type)</span></span>|<span data-ttu-id="a8ea6-122">Typ XPath nebo typ XSLT</span><span class="sxs-lookup"><span data-stu-id="a8ea6-122">XPath type or XSLT type</span></span>|  
|--------------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="a8ea6-123">String</span><span class="sxs-lookup"><span data-stu-id="a8ea6-123">String</span></span>|<span data-ttu-id="a8ea6-124">System. String</span><span class="sxs-lookup"><span data-stu-id="a8ea6-124">System.String</span></span>|<span data-ttu-id="a8ea6-125">XPath</span><span class="sxs-lookup"><span data-stu-id="a8ea6-125">XPath</span></span>|  
|<span data-ttu-id="a8ea6-126">Boolean</span><span class="sxs-lookup"><span data-stu-id="a8ea6-126">Boolean</span></span>|<span data-ttu-id="a8ea6-127">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="a8ea6-127">System.Boolean</span></span>|<span data-ttu-id="a8ea6-128">XPath</span><span class="sxs-lookup"><span data-stu-id="a8ea6-128">XPath</span></span>|  
|<span data-ttu-id="a8ea6-129">Počet</span><span class="sxs-lookup"><span data-stu-id="a8ea6-129">Number</span></span>|<span data-ttu-id="a8ea6-130">System.Double</span><span class="sxs-lookup"><span data-stu-id="a8ea6-130">System.Double</span></span>|<span data-ttu-id="a8ea6-131">XPath</span><span class="sxs-lookup"><span data-stu-id="a8ea6-131">XPath</span></span>|  
|<span data-ttu-id="a8ea6-132">Fragment stromu výsledků</span><span class="sxs-lookup"><span data-stu-id="a8ea6-132">Result Tree Fragment</span></span>|<span data-ttu-id="a8ea6-133">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a8ea6-133">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="a8ea6-134">XSLT</span><span class="sxs-lookup"><span data-stu-id="a8ea6-134">XSLT</span></span>|  
|<span data-ttu-id="a8ea6-135">Sada uzlů</span><span class="sxs-lookup"><span data-stu-id="a8ea6-135">Node Set</span></span>|<span data-ttu-id="a8ea6-136">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="a8ea6-136">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="a8ea6-137">XPath</span><span class="sxs-lookup"><span data-stu-id="a8ea6-137">XPath</span></span>|  
  
 <span data-ttu-id="a8ea6-138">Pokud objekt Parameter není jedna z výše uvedených tříd, je podle potřeby vynucen buď Double, nebo řetězec.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-138">If the parameter object is not one of the above classes, it is forced to either a Double or String, as appropriate.</span></span> <span data-ttu-id="a8ea6-139">Typy Int16, UInt16, Int32, UInt32, Int64, UInt64, Single a Decimal jsou vynuceny na hodnotu Double.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, Single and Decimal types are forced to a Double.</span></span> <span data-ttu-id="a8ea6-140">Všechny ostatní typy jsou vynuceny řetězcem pomocí metody `ToString`.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-140">All other types are forced to a String using the `ToString` method.</span></span>  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a><span data-ttu-id="a8ea6-141">Chcete-li použít parametr XSLT, musí uživatel provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="a8ea6-141">To use the XSLT parameter, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="a8ea6-142">Vytvořte <xref:System.Xml.Xsl.XsltArgumentList> a přidejte objekty pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-142">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the objects using <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span></span>  
  
2. <span data-ttu-id="a8ea6-143">Volání parametrů ze šablon stylů.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-143">Call the parameters from the style sheet.</span></span>  
  
3. <span data-ttu-id="a8ea6-144">Předejte <xref:System.Xml.Xsl.XsltArgumentList> do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-144">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a8ea6-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8ea6-145">Example</span></span>  
 <span data-ttu-id="a8ea6-146">Následující příklad používá metodu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> k vytvoření parametru pro uchování počítaného data slevy.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-146">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold a calculated discount date.</span></span> <span data-ttu-id="a8ea6-147">Datum slevy se počítá jako 20 dní od data objednávky.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-147">The discount date is calculated to be 20 days from the order date.</span></span>  
  
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
  
### <a name="input"></a><span data-ttu-id="a8ea6-148">Vstup</span><span class="sxs-lookup"><span data-stu-id="a8ea6-148">Input</span></span>  
 <span data-ttu-id="a8ea6-149">Order. XML</span><span class="sxs-lookup"><span data-stu-id="a8ea6-149">order.xml</span></span>  
  
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
  
 <span data-ttu-id="a8ea6-150">sleva. xsl</span><span class="sxs-lookup"><span data-stu-id="a8ea6-150">discount.xsl</span></span>  
  
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
  
### <a name="output"></a><span data-ttu-id="a8ea6-151">Výstup</span><span class="sxs-lookup"><span data-stu-id="a8ea6-151">Output</span></span>  
  
```xml  
<order>  
   <total>36.9</total>   
   15% discount if paid by: 5/6/2001 5:01:15 PM   
</order>  
```  
  
## <a name="xslt-extension-objects"></a><span data-ttu-id="a8ea6-152">Objekty rozšíření XSLT</span><span class="sxs-lookup"><span data-stu-id="a8ea6-152">XSLT Extension Objects</span></span>  
 <span data-ttu-id="a8ea6-153">Objekty rozšíření XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> pomocí metody <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-153">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="a8ea6-154">Úplný název a identifikátor URI oboru názvů jsou v daném čase přidruženy k objektu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-154">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
 <span data-ttu-id="a8ea6-155">Když je přidán objekt, volající <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> musí být plně důvěryhodný v zásadách zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-155">When an object is added, the caller of the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> must be fully trusted in the security policy.</span></span> <span data-ttu-id="a8ea6-156">Pokud je volající částečně důvěryhodný, přidání se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-156">If the caller is semi-trusted, the addition will fail.</span></span>  
  
 <span data-ttu-id="a8ea6-157">I když je objekt úspěšně přidán, není zaručeno, že spuštění bude úspěšné.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-157">Though an object is added successfully, it does not guarantee that the execution will be successful.</span></span> <span data-ttu-id="a8ea6-158">Při volání metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> se oprávnění vypočítávají proti legitimaci poskytnuté v <xref:System.Xml.Xsl.XslTransform.Load%2A> čase a tato sada oprávnění je přiřazena k celému procesu transformace.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-158">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at <xref:System.Xml.Xsl.XslTransform.Load%2A> time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="a8ea6-159">Pokud se objekt rozšíření pokusí iniciovat akci, která vyžaduje oprávnění, která nebyla v sadě nalezena, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-159">If an extension object attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
 <span data-ttu-id="a8ea6-160">Datové typy vrácené z objektů rozšíření jsou jedním ze čtyř základních datových typů XPath číslo, řetězec, logická hodnota a sada uzlů.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-160">The data types returned from extension objects are one of the four basic XPath data types of number, string, Boolean, and node set.</span></span>  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a><span data-ttu-id="a8ea6-161">Chcete-li použít objekt rozšíření XSLT, musí uživatel provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="a8ea6-161">To use the XSLT extension object, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="a8ea6-162">Vytvořte <xref:System.Xml.Xsl.XsltArgumentList> a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-162">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span></span>  
  
2. <span data-ttu-id="a8ea6-163">Vyvolá objekt rozšíření ze seznamu stylů.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-163">Invoke the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="a8ea6-164">Předejte <xref:System.Xml.Xsl.XsltArgumentList> do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-164">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a8ea6-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8ea6-165">Example</span></span>  
 <span data-ttu-id="a8ea6-166">Následující příklad vypočítá obvodu kružnice s daným poloměrem.</span><span class="sxs-lookup"><span data-stu-id="a8ea6-166">The following example calculates the circumference of a circle given its radius.</span></span>  
  
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
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="a8ea6-167">Vstup</span><span class="sxs-lookup"><span data-stu-id="a8ea6-167">Input</span></span>  
 <span data-ttu-id="a8ea6-168">Number. XML</span><span class="sxs-lookup"><span data-stu-id="a8ea6-168">number.xml</span></span>  
  
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
  
 <span data-ttu-id="a8ea6-169">Circle. xsl</span><span class="sxs-lookup"><span data-stu-id="a8ea6-169">circle.xsl</span></span>  
  
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
  
### <a name="output"></a><span data-ttu-id="a8ea6-170">Výstup</span><span class="sxs-lookup"><span data-stu-id="a8ea6-170">Output</span></span>  
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
  
## <a name="see-also"></a><span data-ttu-id="a8ea6-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8ea6-171">See also</span></span>

- [<span data-ttu-id="a8ea6-172">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="a8ea6-172">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
