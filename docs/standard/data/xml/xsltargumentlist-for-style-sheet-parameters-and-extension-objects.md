---
title: XsltArgumentList pro parametry šablon stylů a objektů rozšíření
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
ms.openlocfilehash: 34ffb9923337bbad90b2170a16d610d26c7f6f23
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160193"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a>XsltArgumentList pro parametry šablon stylů a objektů rozšíření
Třída <xref:System.Xml.Xsl.XsltArgumentList> obsahuje rozšiřitelné parametry jazyka StyleSheet (XSLT) a objekty rozšíření XSLT. Při předání do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> mohou být tyto parametry a objekty rozšíření vyvolány ze šablon stylů.  
  
> [!NOTE]
> Třídy <xref:System.Xml.Xsl.XslTransform> a <xref:System.Xml.Xsl.XsltArgumentList> jsou v .NET Framework 2,0 zastaralé. Transformace XSLT lze provádět pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Třída <xref:System.Xml.Xsl.XsltArgumentList> obsahuje parametry XSLT a objekty rozšíření XSLT. Při předání do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> mohou být tyto parametry a objekty rozšíření vyvolány ze šablon stylů.  
  
 Níže jsou uvedené výhody pro předání objektu místo použití vloženého skriptu:  
  
- Poskytuje lepší zapouzdření a opakované použití tříd.  
  
- Povoluje, aby byly šablony stylů menší a udržovatelnější.  
  
- Podporuje volání metod u tříd patřících do oborů názvů, které jsou definovány v rámci množiny podporovaných oborů názvů <xref:System>.  
  
- Podporuje předávání fragmentů stromu výsledků do předlohy se styly s použitím <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="xslt-style-sheet-parameters"></a>Parametry šablony stylů XSLT  
 Parametry XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> pomocí metody <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>. Úplný název a identifikátor URI oboru názvů (Uniform Resource Identifier) jsou v daném okamžiku přidruženy k objektu Parameter.  
  
 Objekt Parameter by měl odpovídat typu konsorcium World Wide Web (W3C). V následující tabulce jsou uvedeny odpovídající typy W3C, ekvivalentní .NET Framework třídy (Type) a zda je typ W3C typu jazyk XML Path (XPath) nebo typu XSLT.  
  
|Typ W3C|Ekvivalentní třída .NET Framework (typ)|Typ XPath nebo typ XSLT|  
|--------------|----------------------------------------------|-----------------------------|  
|Řetězec|System. String|XPath|  
|Logická hodnota|System. Boolean|XPath|  
|Číslo|System.Double|XPath|  
|Fragment stromu výsledků|System.Xml.XPath.XPathNavigator|XSLT|  
|Sada uzlů|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Pokud objekt Parameter není jedna z výše uvedených tříd, je podle potřeby vynucen buď Double, nebo řetězec. Typy Int16, UInt16, Int32, UInt32, Int64, UInt64, Single a Decimal jsou vynuceny na hodnotu Double. Všechny ostatní typy jsou vynuceny řetězcem pomocí metody `ToString`.  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a>Chcete-li použít parametr XSLT, musí uživatel provést následující akce:  
  
1. Vytvořte <xref:System.Xml.Xsl.XsltArgumentList> a přidejte objekty pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.  
  
2. Volání parametrů ze šablon stylů.  
  
3. Předejte <xref:System.Xml.Xsl.XsltArgumentList> do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>.  
  
### <a name="example"></a>Příklad  
 Následující příklad používá metodu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> k vytvoření parametru pro uchování počítaného data slevy. Datum slevy se počítá jako 20 dní od data objednávky.  
  
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
  
### <a name="input"></a>Vstup  
 Order. XML  
  
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
  
 sleva. xsl  
  
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
  
### <a name="output"></a>Výstup  
  
```xml  
<order>  
   <total>36.9</total>
   15% discount if paid by: 5/6/2001 5:01:15 PM
</order>  
```  
  
## <a name="xslt-extension-objects"></a>Objekty rozšíření XSLT  
 Objekty rozšíření XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> pomocí metody <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. Úplný název a identifikátor URI oboru názvů jsou v daném čase přidruženy k objektu rozšíření.  
  
 Když je přidán objekt, volající <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> musí být plně důvěryhodný v zásadách zabezpečení. Pokud je volající částečně důvěryhodný, přidání se nezdaří.  
  
 I když je objekt úspěšně přidán, není zaručeno, že spuštění bude úspěšné. Při volání metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> se oprávnění vypočítávají proti legitimaci poskytnuté v <xref:System.Xml.Xsl.XslTransform.Load%2A> čase a tato sada oprávnění je přiřazena k celému procesu transformace. Pokud se objekt rozšíření pokusí iniciovat akci, která vyžaduje oprávnění, která nebyla v sadě nalezena, je vyvolána výjimka.  
  
 Datové typy vrácené z objektů rozšíření jsou jedním ze čtyř základních datových typů XPath číslo, řetězec, logická hodnota a sada uzlů.  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a>Chcete-li použít objekt rozšíření XSLT, musí uživatel provést následující akce:  
  
1. Vytvořte <xref:System.Xml.Xsl.XsltArgumentList> a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2. Vyvolá objekt rozšíření ze seznamu stylů.  
  
3. Předejte <xref:System.Xml.Xsl.XsltArgumentList> do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>.  
  
### <a name="example"></a>Příklad  
 Následující příklad vypočítá obvodu kružnice s daným poloměrem.  
  
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
  
### <a name="input"></a>Vstup  
 Number. XML  
  
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
  
 Circle. xsl  
  
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
  
### <a name="output"></a>Výstup  
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
  
## <a name="see-also"></a>Viz také

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
