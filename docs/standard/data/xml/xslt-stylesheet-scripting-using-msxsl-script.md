---
title: "Pomocí skriptování šablony stylů XSLT &lt;msxsl:script&gt;"
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
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f9e7ceb40167d970b1886aec17b93f4bcf08f631
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="xslt-stylesheet-scripting-using-ltmsxslscriptgt"></a>Pomocí skriptování šablony stylů XSLT &lt;msxsl:script&gt;
<xref:System.Xml.Xsl.XslTransform> Třída podporuje použití vloženého skriptu `script` elementu.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 <xref:System.Xml.Xsl.XslTransform> Třída podporuje použití vloženého skriptu `script` elementu. Při načítání šablony stylů žádné definované funkce jsou kompilovaná do převodního jazyka Microsoft (MSIL) je uzavřen do definice třídy a v důsledku mít nedošlo ke ztrátě výkonu.  
  
 `<msxsl:script>` Element je definován pod:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 kde `msxsl` je vázán předponu pro obor názvů `urn:schemas-microsoft-com:xslt`.  
  
 `language` Atribut není povinné, ale -li zadána, jeho hodnota musí být jeden z následujících: C#, VB, JScript, JavaScript, VisualBasic nebo CSharp. Pokud není zadáno, výchozí jazyk JScript. `language-name` Není malá a velká písmena, proto odpovídají 'JavaScript' a "javascript".  
  
 `implements-prefix` Atribut je povinný. Tento atribut slouží k deklarace oboru názvů a přidružte ji k blok skriptu. Hodnota tohoto atributu je předpona, která představuje obor názvů. Tento obor názvů, může být definováno někde v šabloně stylů.  
  
 Protože `msxsl:script` element patří do oboru názvů `urn:schemas-microsoft-com:xslt`, šablony stylů musí obsahovat deklaraci oboru názvů `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.  
  
 Pokud má volající skriptu nemá <xref:System.Security.Permissions.SecurityPermissionFlag> oprávnění, pak bude nikdy kompilovat skript v šabloně stylů a volání <xref:System.Xml.Xsl.XslTransform.Load%2A> se nezdaří.  
  
 Pokud má volající `UnmanagedCode` zkompiluje skript oprávnění, ale jsou závislé na důkaz, která se dodává v okamžiku načtení operace, které jsou povoleny.  
  
 Pokud použijete jednu z <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, které berou <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XPath.XPathNavigator> načtení šablony stylů, budete muset použít <xref:System.Xml.Xsl.XslTransform.Load%2A> přetížení, které přijímá <xref:System.Security.Policy.Evidence> parametrů jako jedna z jeho argumenty. Pro prokázání, volající musí mít <xref:System.Security.Permissions.SecurityPermissionFlag> oprávnění k poskytování `Evidence` pro sestavení skriptu. Pokud má volající nemá toto oprávnění, pak se můžete nastavit `Evidence` parametru `null`. To způsobí, že <xref:System.Xml.Xsl.XslTransform.Load%2A> funkce, která se nezdaří, pokud najde skriptu. `ControlEvidence` Oprávnění je považován za velmi výkonné oprávnění, které by měl lze udělit pouze vysoce důvěryhodný kód.  
  
 Důkaz z vaší sestavení, použijte `this.GetType().Assembly.Evidence`. Důkaz z identifikátor URI (Uniform Resource), použijte `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.  
  
 Pokud používáte <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, které berou <xref:System.Xml.XmlResolver> , ale žádné `Evidence`, výchozí nastavení zóny zabezpečení pro sestavení úplný vztah důvěryhodnosti. Další informace najdete v tématu <xref:System.Security.SecurityZone> a [pojmenované sady oprávnění](http://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 Funkce můžete deklarované v rámci `msxsl:script` elementu. V následující tabulce jsou obory názvů, které jsou podporovány ve výchozím nastavení. Můžete třídy mimo uvedené obory názvů. Tyto třídy však musí být úplná.  
  
|Výchozí obory názvů|Popis|  
|------------------------|-----------------|  
|Systém|Třída systému.|  
|System.Collection|Třídy kolekce.|  
|System.Text|Text třídy.|  
|System.Text.RegularExpressions|Třídy regulárních výrazů.|  
|System.Xml|Základní třídy XML.|  
|System.Xml.Xsl|Třídy XSLT.|  
|System.Xml.XPath|Třídy XML Path Language (XPath).|  
|Microsoft.VisualBasic|Třídy pro skripty jazyka Microsoft Visual Basic.|  
  
 Pokud je deklarovaná funkci, je obsažený v bloku skriptu. Šablony stylů může obsahovat více skriptu bloků, každý operační nezávisle na sobě. To znamená, že pokud spouštění uvnitř bloku skriptu nelze volat funkci, která jste definovali v jiného bloku skriptu, pokud je deklarovaná do mají stejný obor názvů a stejný skriptovací jazyk. Protože každý blok skriptu může být v jeho vlastní jazyk a bloku je analyzována podle pravidel gramatika objektů tohoto analyzátoru jazyka, musíte použít správnou syntaxi pro jazyk používán. Například pokud jste v bloku skriptu jazyka C#, je použít uzel komentáře XML k chybě `<!-- an XML comment -->` v bloku.  
  
 Zadané argumenty a návratové hodnoty definované funkce skriptu musí být jeden z typů XPath World Wide Web Consortium (W3C) nebo XSLT. Následující tabulka uvádí odpovídající typy W3C ekvivalent rozhraní .NET Framework třídy (typ) a zda typ W3C je XPath typ nebo typ XSLT.  
  
|Typ|Ekvivalent rozhraní .NET Framework třídy (typ)|Výraz XPath typ nebo typ XSLT|  
|----------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|Číslo|System.Double|XPath|  
|Fragment výsledek stromu|System.Xml.XPath.XPathNavigator|XSLT|  
|Sada uzlů.|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Pokud funkci skript využívá jednu z následujících číselnými typy: Int16, UInt16, Int32, UInt32, Int64, UInt64, jedním nebo Decimal, že jsou nuceno dvakrát, která se mapuje na typ Číslo W3C XPath. Všechny ostatní typy jsou nuceno řetězec voláním `ToString` metoda.  
  
 Pokud funkci skript využívá typu než výše uvedené, nebo pokud funkce nekompiluje se při načtení šablony stylů do <xref:System.Xml.Xsl.XslTransform> objekt, je vyvolána výjimka.  
  
 Při použití `msxsl:script` elementu, důrazně doporučujeme, aby na skript, bez ohledu na jazyk, být umístěna uvnitř oddílu CDATA. Například následující kód XML ukazuje šablonu oddílu CDATA, kde je umístěn vašeho kódu.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 Důrazně doporučujeme, aby veškerý obsah skriptu umístit do oddílu CDATA, protože operátory, identifikátory nebo oddělovače pro daný jazyk mohou být právě k nesprávné interpretaci jako XML. Následující příklad ukazuje použití logický operátor AND ve skriptu.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp>  
    public string book(string abc, string xyz)  
    {  if ((abc== abc)&&(abc== xyz)) return bar+xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 To vyvolá výjimku, protože nejsou uvozené ampersandy. Načte se dokument ve formátu XML a žádné zvláštní zacházení se použije pro text mezi `msxsl:script` značky elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá k výpočtu obvodu kruhu zadané jeho radius vloženého skriptu.  
  
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
  
   public static void Main() {  
  
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
 number.xml  
  
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
     public double circumference(double radius){  
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
  
## <a name="see-also"></a>Viz také  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
