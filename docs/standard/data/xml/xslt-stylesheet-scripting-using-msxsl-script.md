---
title: 'XSLT šablony stylů skriptování pomocí < msxsl: script >'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78dec0d4c3c6e7cab6e179be9dbe61cfd01dc7fc
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835249"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a>Šablona stylů XSLT skriptování pomocí \<msxsl: script >
<xref:System.Xml.Xsl.XslTransform> Třída podporuje vložené skriptování pomocí `script` elementu.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 <xref:System.Xml.Xsl.XslTransform> Třída podporuje vložené skriptování pomocí `script` elementu. Při načtení šablony stylů žádné definované funkce jsou kompilovány pro jazyk Microsoft intermediate language (MSIL) pomocí právě zabalené v definici třídy a díky tomu mají bez ztráty výkonu.  
  
 `<msxsl:script>` Element je definována níže:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 kde `msxsl` je vázán předponu pro obor názvů `urn:schemas-microsoft-com:xslt`.  
  
 `language` Atribut není povinné, ale pokud je zadán, její hodnota musí být jeden z následujících: C#, VB, JScript, JavaScript, VisualBasic, or CSharp. Pokud není zadán, výchozí jazyk JScript. `language-name` Není malá a velká písmena, a proto jsou ekvivalentní 'Jazyka JavaScript' a "javascript".  
  
 `implements-prefix` Atribut je povinný. Tento atribut se používá k deklarování oboru názvů a přidružte jej k bloku skriptu. Hodnota tohoto atributu je předpona, která představuje obor názvů. Tento obor názvů lze definovat někde v šabloně stylů.  
  
 Vzhledem k tomu, `msxsl:script` element patří do oboru názvů `urn:schemas-microsoft-com:xslt`, šablony stylů musí obsahovat deklarace oboru názvů `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.  
  
 Pokud volající skript nemá <xref:System.Security.Permissions.SecurityPermissionFlag> přístupové oprávnění, pak se nikdy kompilaci skriptu v šabloně stylů a volání <xref:System.Xml.Xsl.XslTransform.Load%2A> se nezdaří.  
  
 Pokud má volající `UnmanagedCode` oprávnění, který zkompiluje, ale jsou závislé na legitimace uvedená v okamžiku načtení operace, které jsou povoleny.  
  
 Pokud používáte některou <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, které berou <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XPath.XPathNavigator> k načtení šablony stylů, budete muset použít <xref:System.Xml.Xsl.XslTransform.Load%2A> přetížení přebírající <xref:System.Security.Policy.Evidence> parametr jako jeden z jejích argumentů. Zajištění legitimity volající musí mít <xref:System.Security.Permissions.SecurityPermissionFlag> oprávnění k poskytování `Evidence` pro skript sestavení. Pokud volající toto oprávnění nemá, pak můžete nastavit `Evidence` parametr `null`. To způsobí, že <xref:System.Xml.Xsl.XslTransform.Load%2A> funkce selhat, pokud najde skriptu. `ControlEvidence` Oprávnění se považuje za velmi výkonné oprávnění, které by měl lze udělit pouze vysoce důvěryhodným kódem.  
  
 K získání legitimace z vašeho sestavení, použijte `this.GetType().Assembly.Evidence`. K získání legitimace z identifikátor URI (Uniform Resource), použijte `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.  
  
 Pokud používáte <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, které berou <xref:System.Xml.XmlResolver> ale žádné `Evidence`, zóny zabezpečení pro sestavení použije výchozí plné důvěryhodnosti. Další informace najdete v tématu <xref:System.Security.SecurityZone> a [pojmenované sady oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Funkce mohou být deklarovány v rámci `msxsl:script` elementu. V následující tabulce jsou uvedeny obory názvů, které jsou podporovány ve výchozím nastavení. Můžete použít třídy mimo uvedených oborů názvů. Tyto třídy však musí být plně kvalifikovaný.  
  
|Výchozí obory názvů|Popis|  
|------------------------|-----------------|  
|Systém|Třída systému.|  
|System.Collection|Třídy kolekcí.|  
|System.Text|Textové třídy.|  
|System.Text.RegularExpressions|Třídy regulárních výrazů.|  
|System.Xml|Základní třídy XML.|  
|System.Xml.Xsl|Třídy XSLT.|  
|System.Xml.XPath|Jazyk XML Path (XPath) třídy.|  
|Microsoft.VisualBasic|Třídy pro skripty jazyka Microsoft Visual Basic.|  
  
 Při deklaraci funkce, je obsažen v bloku skriptu. Šablony stylů může obsahovat více blocích skriptu, každý operační nezávisle na sobě. To znamená, že pokud jsou spuštěny uvnitř bloku skriptu, nelze volat funkci, která jste definovali v jiném bloku skriptu, pokud je deklarovaná mít stejný obor názvů a stejné skriptovací jazyk. Protože každý blok skriptu může být v jeho vlastní jazyk a blok je analyzován podle pravidel gramatika tento analyzátor jazyka, musíte použít správnou syntaxi jazyka používán. Například pokud jste v bloku skriptu C#, je chybně použit uzel Komentář XML `<!-- an XML comment -->` v bloku.  
  
 Zadané argumenty a návratové hodnoty určené funkce skriptu musí být jeden z typů XPath World Wide Web Consortium (W3C) nebo XSLT. V následující tabulce jsou uvedeny odpovídající typy W3C ekvivalentní rozhraní .NET Framework třídy (typ) a zda W3C zadejte je XPath typ nebo typ XSLT.  
  
|Typ|Třída ekvivalentní rozhraní .NET Framework (typ)|Výraz XPath typ nebo typ XSLT|  
|----------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|Číslo|System.Double|XPath|  
|Fragment stromu výsledek|System.Xml.XPath.XPathNavigator|XSLT|  
|Sada uzlů.|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Pokud funkce skriptu využívá jednu z následujících číselné typy: Int16, UInt16, Int32, UInt32, Int64, UInt64, jedním nebo desetinné číslo, budou ukončeny do dvakrát, která se mapuje na typ Číslo W3C XPath. Všechny ostatní typy jsou vynutit na řetězec volání `ToString` metody.  
  
 Pokud funkce skriptu využívá typ jiný než uvedených výše, nebo pokud funkci nejde zkompilovat při šablony stylů je načten do <xref:System.Xml.Xsl.XslTransform> objektu, je vyvolána výjimka.  
  
 Při použití `msxsl:script` elementu, důrazně doporučujeme, aby skript, bez ohledu na jazyk, umístit do oddílu CDATA. Například následující kód XML ukazuje šablony sekce CDATA, kde je umístěn váš kód.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 Důrazně doporučujeme, aby veškerý obsah skriptu umístit do oddílu CDATA, protože operátory, identifikátory nebo oddělovače pro daný jazyk mají potenciál je špatně interpretována jako XML. Následující příklad ukazuje použití logického operátoru AND ve skriptu.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 To vyvolá výjimku, protože tyto znaky nejsou uvozeny zpětným lomítkem. Dokument je načtena jako XML a žádné zvláštní zacházení se použije pro text mezi `msxsl:script` značky elementů.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá vložený skript k výpočtu obvod kruhu uveden jeho radius.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.               
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
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
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main()  
   {  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.               
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }  
}  
```  
  
## <a name="input"></a>Vstup  
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
  
 calc.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">    
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>   
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a>Výstup  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>    
```  
  
## <a name="see-also"></a>Viz také:

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
