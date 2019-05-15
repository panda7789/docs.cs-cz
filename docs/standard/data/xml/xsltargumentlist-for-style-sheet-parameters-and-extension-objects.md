---
title: XsltArgumentList pro parametry šablon stylů a objektů rozšíření
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11cf0b694d75836ad903edeafc79a55ec4612b45
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586462"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a>XsltArgumentList pro parametry šablon stylů a objektů rozšíření
<xref:System.Xml.Xsl.XsltArgumentList> Třída obsahuje rozšiřitelný jazyk šablony stylů transformace XSLT () parametry a objekty rozšíření XSLT. Při předání do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu, tyto parametry a rozšíření objekty lze volat z šablony stylů.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> a <xref:System.Xml.Xsl.XsltArgumentList> třídy jsou zastaralé v [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provádět pomocí transformace XSLT <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 <xref:System.Xml.Xsl.XsltArgumentList> Třída obsahuje parametry XSLT a objekty rozšíření XSLT. Při předání do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu, tyto parametry a rozšíření objekty lze volat z šablony stylů.  
  
 Následují výhody pro předávání objektů, spíše než pomocí vloženého skriptu:  
  
- Poskytuje lepší zapouzdření a opakované použití tříd.  
  
- Povoluje stylů, aby bylo menší a jednodušší údržbu.  
  
- Podporuje volání metody u třídy, které patří do oborů názvů, než jsou definované v rámci sady podporované <xref:System> obory názvů.  
  
- Podporuje předávání výsledků fragmenty stromu s použitím šablony stylů <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="xslt-style-sheet-parameters"></a>Parametry list Styl XSLT  
 Parametry XSLT se přidají do <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody. Úplný název a obor názvů identifikátoru URI (Uniform Resource) jsou spojeny s parametrem objektu v daném čase.  
  
 Parametr objektu by měl odpovídat typu World Wide Web Consortium (W3C). Následující tabulka uvádí odpovídající typy W3C odpovídající třídy rozhraní .NET Framework (typ), a určuje, zda je typ W3C jazyk XML Path (XPath) nebo XSLT.  
  
|Typ W3C|Ekvivalentní třída rozhraní .NET Framework (typ)|Výraz XPath typ nebo typ XSLT|  
|--------------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|Číslo|System.Double|XPath|  
|Fragment stromu výsledek|System.Xml.XPath.XPathNavigator|XSLT|  
|Sada uzlů.|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Pokud parametr objektu není jeden z výše uvedených tříd, je vynucena na dvojitou hodnotu nebo řetězec, podle potřeby. Int16, UInt16, Int32, UInt32, Int64, UInt64, jednou a desetinných typy jsou vynutit na dvojitou hodnotu. Všechny ostatní typy jsou vynuceně na řetězec pomocí `ToString` metody.  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a>Pokud chcete použít parametr XSLT, uživatel musí provést následující kroky:  
  
1. Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> a přidejte objekt pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.  
  
2. Parametry volání z šablony stylů.  
  
3. Předání <xref:System.Xml.Xsl.XsltArgumentList> k <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody.  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodu pro vytvoření parametr pro uložení data počítané slevy. Slevy se počítá na 20 dní od data objednávky.  
  
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
 order.xml  
  
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
  
 discount.xsl  
  
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
 Objekty rozšíření XSLT se přidají do <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Úplný název a identifikátor URI oboru názvů jsou přidruženy k rozšíření objektu v daném čase.  
  
 Když je objekt přidán, volající <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> v zásadách zabezpečení musí být plně důvěryhodné. Pokud je částečně důvěryhodné volající, přidání se nezdaří.  
  
 I když je objekt úspěšně přidán, není zaručeno, že bude úspěšné provedení příkazu. Když <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda je volána, oprávnění se počítají proti důkazu v <xref:System.Xml.Xsl.XslTransform.Load%2A> čas a aby sada oprávnění přiřazený k transformaci celý proces. Pokud se objekt rozšíření se pokusí spustit akci, která vyžaduje oprávnění nebyla nalezena v sadě, je vyvolána výjimka.  
  
 Datové typy vrácených objektů rozšíření jsou jedním ze čtyř typů základní XPath dat sady číslo, řetězec, logická hodnota a uzel.  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a>Chcete-li použít objekt rozšíření XSLT, uživatel musí provést následující kroky:  
  
1. Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2. Vyvolejte objekt rozšíření ze šablony stylů.  
  
3. Předání <xref:System.Xml.Xsl.XsltArgumentList> k <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody.  
  
### <a name="example"></a>Příklad  
 Následující příklad vypočítá obvod kruhu uveden jeho radius.  
  
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
 Number.XML  
  
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
  
 Circle.xsl  
  
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
  
## <a name="see-also"></a>Viz také:

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
