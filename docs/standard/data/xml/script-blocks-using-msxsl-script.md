---
title: 'Skript pomocí bloky msxsl: Script'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b45b8ebe048a5917019349ea3a6a357b7e90a9c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565641"
---
# <a name="script-blocks-using-msxslscript"></a>Skript pomocí bloky msxsl: Script
<xref:System.Xml.Xsl.XslCompiledTransform> Třída podporuje vložené skripty pomocí `msxsl:script` elementu. Při načítání šablony stylů žádné definované funkce jsou kompilovaná Code Document Object Model (CodeDOM) pro jazyk Microsoft intermediate language (MSIL) a jsou spouštěny za běhu. Sestavení vygenerované z bloku vloženého skriptu je oddělená než sestavení vygenerované pro šablony stylů.  
  
## <a name="enable-xslt-script"></a>Povolit skriptu XSLT  
 Podpora pro vložené skripty je volitelné nastavení XSLT na <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Ve výchozím nastavení je zakázána podpora skriptování. Povolení podpory skriptu, vytvořit <xref:System.Xml.Xsl.XsltSettings> objekt s <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> vlastnost nastavena na `true` a předejte objekt, který má <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda.  
  
> [!NOTE]
>  Pouze v případě, že budete potřebovat podporu skriptu a práci v plně důvěryhodném prostředí by měl být povoleno skriptování XSLT.  
  
## <a name="msxslscript-element-definition"></a>msxsl: Script Element definice  
 `msxsl:script` Element je rozšířením společnosti Microsoft pro XSLT 1.0 doporučení a obsahuje následující definice:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 `msxsl` Předpona je svázána s `urn:schemas-microsoft-com:xslt` identifikátor URI oboru názvů. Šablona stylů musí zahrnovat `xmlns:msxsl=urn:schemas-microsoft-com:xslt` deklarace oboru názvů.  
  
 `language` Atribut je volitelný. Jeho hodnota je jazyk kódu vloženého kódu bloku. Jazyk je namapována na používání kompilátoru odpovídající CodeDOM <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> metody. <xref:System.Xml.Xsl.XslCompiledTransform> Třída může podporovat libovolný jazyk rozhraní Microsoft .NET, za předpokladu, že odpovídající zprostředkovatel je na počítači nainstalovaný a zaregistrovaný v oddíle system.codedom souboru machine.config. Pokud `language` atribut není zadán, výchozí jazyk JScript. Název jazyka není tak, aby byly ekvivalentní 'Jazyka JavaScript' a 'javascript: malá a velká písmena.  
  
 `implements-prefix` Atribut je povinný. Tento atribut se používá k deklarování oboru názvů a přidružte jej k bloku skriptu. Hodnota tohoto atributu je předpona, která představuje obor názvů. Tuto předponu lze definovat někde v šabloně stylů.  
  
> [!NOTE]
>  Při použití `msxsl:script` elementu, důrazně doporučujeme, aby skript, bez ohledu na jazyk, umístit do oddílu CDATA. Vzhledem k tomu, že skript může obsahovat operátory, identifikátory nebo oddělovače pro daný jazyk, pokud není obsažen v rámci oddílu CDATA, má potenciál je špatně interpretována jako XML. Následující kód XML ukazuje šablonu oddílu CDATA umístění kódu.  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a>Funkce skriptu  
 Funkce mohou být deklarovány v rámci `msxsl:script` elementu. Při deklaraci funkce, je obsažen v bloku skriptu. Šablony stylů může obsahovat více blocích skriptu, každý operační nezávisle na sobě. To znamená, že pokud jsou spuštěny uvnitř bloku skriptu, nelze volat funkci, která jste definovali v jiném bloku skriptu, pokud je deklarovaná mít stejný obor názvů a stejné skriptovací jazyk. Vzhledem k tomu, že každý blok skriptu může být v jeho vlastní jazyk a blok je analyzován podle pravidel gramatika tohoto analyzátoru jazyka doporučujeme použít správnou syntaxi jazyka používán. Například pokud jste v bloku skriptu jazyka Microsoft C#, použijte syntaxi komentář jazyka C#.  
  
 Zadané argumenty a návratové hodnoty funkce může být libovolného typu. Protože jsou typy W3C XPath podmnožiny běžných typů language runtime (CLR), převod typu se provádí na typy, které nejsou považovány za typem XPath. V následující tabulce jsou uvedeny odpovídající typy W3C a ekvivalentní typ CLR.  
  
|Typ W3C|Typ CLR|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 Číselné typy CLR se převedou na <xref:System.Double>. <xref:System.DateTime> Typ je převeden na <xref:System.String>. <xref:System.Xml.XPath.IXPathNavigable> typy budou převedené na <xref:System.Xml.XPath.XPathNavigator>. **[] Objektem XPathNavigator nastaveným na** je převedena na <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Všechny ostatní typy vyvolat chybu.  
  
### <a name="importing-namespaces-and-assemblies"></a>Importovat obory názvů a sestavení  
 <xref:System.Xml.Xsl.XslCompiledTransform> Třídy predefines sadu sestavení a obory názvů, které jsou podporovány ve výchozím nastavení `msxsl:script` elementu. Můžete však použít třídy a členy, které patří do oboru názvů, který není na seznamu předdefinovaných importováním sestavení a oboru názvů v `msxsl:script` bloku.  
  
#### <a name="assemblies"></a>Sestavení  
 Ve výchozím nastavení je odkazováno na následující dvě sestavení:  
  
-   System.dll  
  
-   System.Xml.dll  
  
-   Microsoft.VisualBasic.dll (je-li jazyk skriptu VB)  
  
 Můžete importovat další sestavení pomocí `msxsl:assembly` elementu. To zahrnuje sestavení při kompilaci šablony stylů. `msxsl:assembly` Element má následující definice:  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 `name` Atribut obsahuje název sestavení a `href` atribut obsahuje cestu k sestavení. Název sestavení může být úplný název, například "System.Data, verze = 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089", nebo krátký název, jako je například "System.Web".  
  
#### <a name="namespaces"></a>Jmenné prostory  
 Ve výchozím nastavení jsou zahrnuty následující obory názvů:  
  
-   Systém  
  
-   System.Collection  
  
-   System.Text  
  
-   System.Text.RegularExpressions  
  
-   System.Xml  
  
-   System.Xml.Xsl  
  
-   System.Xml.XPath  
  
-   Microsoft.VisualBasic (je-li jazyk skriptu VB)  
  
 Můžete přidat podporu pro další obory názvů pomocí `namespace` atribut. Hodnota atributu je název oboru názvů.  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad používá vložený skript k výpočtu obvod kruhu uveden jeho radius.  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a>Number.XML  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a>calc.xsl  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a>Výstup  
  
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

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Dynamické vytváření a kompilování zdrojového kódu](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
