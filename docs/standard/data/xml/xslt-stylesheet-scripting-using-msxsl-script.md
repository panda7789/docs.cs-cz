---
title: Skriptování šablon stylů XSLT pomocí <msxsl:script >
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32695d3bc29693ab4cf1e2f9d721d35598ecfb86
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344710"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a>Skriptování šablony stylů XSLT pomocí \<msxsl: > skriptu
Třída <xref:System.Xml.Xsl.XslTransform> podporuje vložené skriptování pomocí elementu `script`.  
  
> [!NOTE]
> Třída <xref:System.Xml.Xsl.XslTransform> je v .NET Framework 2,0 zastaralá. Pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform> můžete provádět transformace XSLT (Extensible Stylesheet Language). Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Třída <xref:System.Xml.Xsl.XslTransform> podporuje vložené skriptování pomocí elementu `script`. Při načtení předlohy se styly se všechny definované funkce zkompiluje do jazyka MSIL (Microsoft Intermediate Language) zabalením do definice třídy a nedochází v důsledku ztráty výkonu.  
  
 `<msxsl:script>` element je definován níže:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 kde `msxsl` je předpona svázaná s oborem názvů `urn:schemas-microsoft-com:xslt`.  
  
 Atribut `language` není povinný, ale pokud je zadaný, musí být jeho hodnota jedna z následujících hodnot: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`nebo `CSharp`. Pokud není zadaný, použije se výchozí jazyk JScript. U `language-name` se nerozlišují velká a malá písmena, takže JavaScript a JavaScript jsou ekvivalentní.  
  
 Atribut `implements-prefix` je povinný. Tento atribut slouží k deklaraci oboru názvů a k jeho přidružení ke bloku skriptu. Hodnota tohoto atributu je předpona, která představuje obor názvů. Tento obor názvů lze definovat někde v šabloně stylů.  
  
 Vzhledem k tomu, že element `msxsl:script` patří do `urn:schemas-microsoft-com:xslt`oboru názvů, šablona stylů musí zahrnovat deklaraci oboru názvů `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.  
  
 Pokud volajícímu skriptu nemáte oprávnění k přístupu <xref:System.Security.Permissions.SecurityPermissionFlag>, skript v šabloně stylů nebude nikdy zkompilován a volání <xref:System.Xml.Xsl.XslTransform.Load%2A> se nezdaří.  
  
 Pokud má volající oprávnění `UnmanagedCode`, skript se zkompiluje, ale operace, které jsou povoleny, jsou závislé na legitimaci, která je zadána v době načítání.  
  
 Pokud používáte jednu z <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, které přebírají <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XPath.XPathNavigator> pro načtení předlohy se styly, je nutné použít přetížení <xref:System.Xml.Xsl.XslTransform.Load%2A>, které přijímá parametr <xref:System.Security.Policy.Evidence> jako jeden z jeho argumentů. Aby mohl volající poskytnout legitimaci, musí mít <xref:System.Security.Permissions.SecurityPermissionFlag> oprávnění, aby mohl poskytnout `Evidence` pro sestavení skriptu. Pokud volající nemá toto oprávnění, může nastavit parametr `Evidence` na hodnotu `null`. Způsobí to, že funkce <xref:System.Xml.Xsl.XslTransform.Load%2A> selže, pokud nalezne skript. Oprávnění `ControlEvidence` je považováno za velmi výkonné oprávnění, které by mělo být uděleno pouze vysoce důvěryhodnému kódu.  
  
 Chcete-li získat legitimaci ze sestavení, použijte `this.GetType().Assembly.Evidence`. K získání legitimace z identifikátoru URI (Uniform Resource Identifier) použijte `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.  
  
 Použijete-li <xref:System.Xml.Xsl.XslTransform.Load%2A> metody, které přebírají <xref:System.Xml.XmlResolver>, ale ne `Evidence`, je zóna zabezpečení pro sestavení nastavena na úplný vztah důvěryhodnosti. Další informace najdete v tématu <xref:System.Security.SecurityZone> a [pojmenované sady oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Funkce mohou být deklarovány v rámci `msxsl:script` elementu. V následující tabulce jsou uvedeny obory názvů, které jsou ve výchozím nastavení podporovány. Můžete použít třídy mimo uvedené obory názvů. Nicméně tyto třídy musí být plně kvalifikované.  
  
|Výchozí obory názvů|Popis|  
|------------------------|-----------------|  
|Systém|Systémová třída|  
|System.Collection|Třídy kolekcí.|  
|System.Text|Třídy textu.|  
|System.Text.RegularExpressions|Třídy regulárních výrazů.|  
|System.Xml|Základní třídy XML.|  
|System.Xml.Xsl|Třídy XSLT.|  
|System.Xml.XPath|Třídy jazyka XML Path (XPath).|  
|Microsoft.VisualBasic|Třídy pro skripty Microsoft Visual Basic.|  
  
 Je-li funkce deklarována, je obsažena v bloku skriptu. Šablony stylů mohou obsahovat více bloků skriptu, z nichž každý pracuje nezávisle na sobě. To znamená, že pokud provádíte uvnitř bloku skriptu, nemůžete volat funkci, která je definována v jiném bloku skriptu, pokud není deklarována tak, aby měla stejný obor názvů a stejný skriptovací jazyk. Vzhledem k tomu, že každý blok skriptu může být ve vlastním jazyce a blok je analyzován podle gramatických pravidel daného jazykového analyzátoru, je nutné použít správnou syntaxi používaného jazyka. Například pokud jste v bloku C# skriptu, pak se jedná o chybu při použití uzlu komentáře XML `<!-- an XML comment -->` v bloku.  
  
 Zadané argumenty a návratové hodnoty, které jsou definovány funkcemi skriptu, musí být jedním z typů XPath nebo XSLT typu konsorcium World Wide Web (W3C). V následující tabulce jsou uvedeny odpovídající typy W3C, ekvivalentní .NET Framework třídy (Type) a zda typ W3C je typ XPath nebo typ XSLT.  
  
|Type|Ekvivalentní třída .NET Framework (typ)|Typ XPath nebo typ XSLT|  
|----------|----------------------------------------------|-----------------------------|  
|String|System. String|XPath|  
|Boolean|System. Boolean|XPath|  
|Počet|System.Double|XPath|  
|Fragment stromu výsledků|System.Xml.XPath.XPathNavigator|XSLT|  
|Sada uzlů|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Pokud funkce skriptu využívá jeden z následujících číselných typů: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single nebo Decimal, jsou nuceni zdvojnásobit, což se mapuje na číslo typu XPath W3C. Všechny ostatní typy jsou vynuceny řetězcem voláním metody `ToString`.  
  
 Pokud funkce skriptu využívá jiný typ než ty, které jsou uvedeny výše, nebo pokud funkce není zkompilována, když je šablona stylů načtena do objektu <xref:System.Xml.Xsl.XslTransform>, je vyvolána výjimka.  
  
 Při použití prvku `msxsl:script` se důrazně doporučuje, aby se skript, bez ohledu na jazyk, umístil do oddílu CDATA. Například následující kód XML ukazuje šablonu oddílu CDATA, kde je váš kód umístěn.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 Důrazně doporučujeme, aby se veškerý obsah skriptu umístil do oddílu CDATA, protože operátory, identifikátory nebo oddělovače pro daný jazyk mají potenciál, který je špatně interpretován jako XML. Následující příklad ukazuje použití logického operátoru AND ve skriptu.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 Vyvolá výjimku, protože ampersandy nejsou uvozeny řídicími znaky. Dokument je načten jako XML a na text mezi značkami `msxsl:script` elementů se neaplikuje žádné speciální zacházení.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použit vložený skript k výpočtu obvodu kružnice s daným poloměrem.  
  
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
