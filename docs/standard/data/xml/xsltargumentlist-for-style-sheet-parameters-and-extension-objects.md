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
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a>Třída XsltArgumentList pro parametry list stylu a rozšíření objekty
<xref:System.Xml.Xsl.XsltArgumentList> Třída obsahuje jazyk XSL pro parametry transformace XSLT () a objektů rozšíření XSLT. Když předána do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu, tyto parametry a rozšíření objektů můžete vyvolat z šablony stylů.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> a <xref:System.Xml.Xsl.XsltArgumentList> třídy jsou v zastaralé [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést pomocí transformace XSLT <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 <xref:System.Xml.Xsl.XsltArgumentList> Třída obsahuje parametry XSLT a objektů rozšíření XSLT. Když předána do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodu, tyto parametry a rozšíření objektů můžete vyvolat z šablony stylů.  
  
 Následují výhody předávání objektů, místo používání vložený skript:  
  
-   Poskytuje lepší zapouzdření a opakovaného použití třídy.  
  
-   Umožňuje stylů menší a více udržovatelný.  
  
-   Podporuje volání metod na třídy, které patří do obory názvů, než jsou definovány v rámci sady podporované <xref:System> obory názvů.  
  
-   Podporuje předávání stromu fragmenty výsledek šablony stylů s použitím <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="xslt-style-sheet-parameters"></a>Parametry list stylu XSLT  
 Parametry XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metoda. Kvalifikovaný název a obor názvů identifikátor URI (Uniform Resource) jsou přidruženy k objektu parametru v daném čase.  
  
 Objekt parametr by měl odpovídat typu World Wide Web Consortium (W3C). Následující tabulka uvádí odpovídající typy W3C ekvivalent [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] třídy (typ), a zda je typ W3C typ XML Path Language (XPath) nebo typ XSLT.  
  
|Typ W3C|Ekvivalentní třídy rozhraní .NET Framework (typ)|Výraz XPath typ nebo typ XSLT|  
|--------------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|Číslo|System.Double|XPath|  
|Fragment výsledek stromu|System.Xml.XPath.XPathNavigator|XSLT|  
|Sada uzlů.|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Pokud objekt parametr není jedním z výše uvedených třídy, je nucen se dvojitou hodnotu nebo řetězec, podle potřeby. Typy Int16, UInt16, Int32, UInt32, Int64, UInt64, jedním a Decimal, vynuceně přesunuty do datový typ Double. Jsou všechny ostatní typy vynucené na řetězec pomocí `ToString` metoda.  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a>Pro parametr XSLT, musí uživatel postupujte takto:  
  
1.  Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> a přidat objekty pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.  
  
2.  Volání parametry z této šablony.  
  
3.  Předat <xref:System.Xml.Xsl.XsltArgumentList> k <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda.  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodu pro vytvoření parametr pro uložení data počítané slevy. Datum slevy je vypočítána na 20 dní od data pořadí.  
  
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
 Order.XML  
  
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
  
## <a name="xslt-extension-objects"></a>Rozšíření objektů XSLT  
 XSLT rozšíření objekty jsou přidány na <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda. Úplný název a identifikátor URI oboru názvů jsou přidruženy k rozšíření objektu v daném čase.  
  
 Když je objekt přidán, volající <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> musí být plně důvěryhodný v zásadě zabezpečení. Pokud je částečně důvěryhodné volající, přidání selže.  
  
 I když je objekt úspěšně přidán, nezaručuje to, že bude úspěšné provedení. Když <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda je volána, oprávnění jsou vypočtena podle důkaz uvedených v <xref:System.Xml.Xsl.XslTransform.Load%2A> čas a jestli je k transformaci celý proces přiřazená oprávnění sady. Pokud objekt rozšíření se pokusí spustit akci, která vyžaduje oprávnění nebyl nalezen v sadě, je vyvolána výjimka.  
  
 Datové typy vrácených objektů rozšíření jsou jedním ze čtyř typů základní XPath datové sady číslo, řetězec, logická hodnota a uzlu.  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a>Pokud chcete použít objekt XSLT rozšíření, uživatel potřebuje provést následující akce:  
  
1.  Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2.  Vyvolání objekt rozšíření z této šablony.  
  
3.  Předat <xref:System.Xml.Xsl.XsltArgumentList> k <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda.  
  
### <a name="example"></a>Příklad  
 Následující příklad vypočítá obvodu kruhu zadané jeho protokolu radius.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
