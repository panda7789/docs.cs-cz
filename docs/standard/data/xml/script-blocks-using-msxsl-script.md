---
title: "Msxsl:script bloky pomocí skriptu"
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
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e127fb02725d11e62c45157b4e45327fc9f1ace
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="script-blocks-using-msxslscript"></a>Msxsl:script bloky pomocí skriptu
<xref:System.Xml.Xsl.XslCompiledTransform> Třída podporuje vložené skripty pomocí `msxsl:script` elementu. Při načtení šablony stylů žádné definované funkce jsou kompilovaná do převodního jazyka Microsoft (MSIL) Code Document Object Model (CodeDOM) a jsou při běhu spuštěn. Sestavení vygenerovat z bloku vloženého skriptu je samostatný než sestavení vygenerované šablony stylů.  
  
## <a name="enable-xslt-script"></a>Povolit XSLT skriptů  
 Podpora pro vložené skripty je volitelné nastavení XSLT na <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Podpora skriptování ve výchozím nastavení vypnutá. Chcete-li povolit podporu skript, vytvořit <xref:System.Xml.Xsl.XsltSettings> objektu s <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> vlastnost nastavena na hodnotu `true` a předat objekt, který má <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda.  
  
> [!NOTE]
>  Pouze v případě, že budete potřebovat podporu skriptu a práci ve plně důvěryhodný pro prostředí by měl být povoleno skriptování XSLT.  
  
## <a name="msxslscript-element-definition"></a>msxsl:Script definice elementu  
 `msxsl:script` Element rozšíření Microsoft pro XSLT 1.0 doporučení a má následující definice:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 `msxsl` Předpona je vázána `urn:schemas-microsoft-com:xslt` identifikátor URI oboru názvů. Musí zahrnovat šablony stylů `xmlns:msxsl=urn:schemas-microsoft-com:xslt` deklaraci oboru názvů.  
  
 `language` Atribut je volitelný. Jeho hodnota může být jazyk kódu vloženého kódu bloku. Jazyk je namapována na odpovídající pomocí modelu CodeDOM kompilátoru <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> metoda. <xref:System.Xml.Xsl.XslCompiledTransform> Třída může podporovat všechny jazykové rozhraní Microsoft .NET, za předpokladu, že příslušného poskytovatele je nainstalovaná na počítači a je zaregistrovaný v oddílu system.codedom souboru machine.config. Pokud `language` atribut nezadá, výchozí jazyk JScript. Název jazyka není malá a velká písmena, takže odpovídají 'JavaScript' a "javascript".  
  
 `implements-prefix` Atribut je povinný. Tento atribut slouží k deklarace oboru názvů a přidružte ji k blok skriptu. Hodnota tohoto atributu je předpona, která představuje obor názvů. Tato předpona může být definováno někde v šabloně stylů.  
  
> [!NOTE]
>  Při použití `msxsl:script` elementu, důrazně doporučujeme, aby na skript, bez ohledu na jazyk, být umístěna uvnitř oddílu CDATA. Vzhledem k tomu, že skript může obsahovat operátory, identifikátory nebo oddělovače pro daný jazyk, pokud není obsažen v rámci oddílu CDATA, má potenciál se k nesprávné interpretaci jako XML. Následující kód XML ukazuje šablonu oddílu CDATA umístění kódu.  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a>Funkce skriptu  
 Funkce můžete deklarované v rámci `msxsl:script` elementu. Pokud je deklarovaná funkci, je obsažený v bloku skriptu. Šablony stylů může obsahovat více skriptu bloků, každý operační nezávisle na sobě. To znamená, že pokud spouštění uvnitř bloku skriptu nelze volat funkci, která jste definovali v jiného bloku skriptu, pokud je deklarovaná do mají stejný obor názvů a stejný skriptovací jazyk. Protože každý blok skriptu může být v jeho vlastní jazyk a bloku je analyzována podle pravidel gramatika objektů tohoto analyzátoru jazyka doporučujeme používáte správnou syntaxi pro jazyk používán. Pokud jste v bloku skriptu Microsoft C#, například pomocí syntaxe komentáře jazyka C#.  
  
 Zadané argumenty a návratové hodnoty funkce můžou být jakéhokoli typu. Protože se typy W3C XPath podmnožinu běžné typy language runtime (CLR), typ převodu dojde na typy, které nejsou považovány za typ XPath. Následující tabulka uvádí odpovídající typy W3C a ekvivalentní typ CLR.  
  
|Typ W3C|Typ CLR|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 Číselné typy CLR se převedou na <xref:System.Double>. <xref:System.DateTime> Typ je převeden na <xref:System.String>. <xref:System.Xml.XPath.IXPathNavigable>typy budou převedené na <xref:System.Xml.XPath.XPathNavigator>. **[] Objektem XPathNavigator nastaveným na** jsou převedeny na <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Všechny ostatní typy vyvolána chyba.  
  
### <a name="importing-namespaces-and-assemblies"></a>Import obory názvů a sestavení  
 <xref:System.Xml.Xsl.XslCompiledTransform> Třída predefines sadu sestavení a obory názvů, které jsou podporovány ve výchozím nastavení `msxsl:script` elementu. Můžete však použít třídy a členové, které patří do oboru názvů, který není v seznamu předdefinovaných importováním sestavení a oboru názvů v `msxsl:script` bloku.  
  
#### <a name="assemblies"></a>Sestavení  
 Ve výchozím nastavení se odkazuje na následující dvě sestavení:  
  
-   System.dll  
  
-   System.Xml.dll  
  
-   Souboru Microsoft.VisualBasic.dll (Pokud jazyk skript jazyka Visual Basic)  
  
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
  
#### <a name="namespaces"></a>Obory názvů  
 Ve výchozím nastavení jsou zahrnuty následující obory názvů:  
  
-   Systém  
  
-   System.Collection  
  
-   System.Text  
  
-   System.Text.RegularExpressions  
  
-   System.Xml  
  
-   System.Xml.Xsl  
  
-   System.Xml.XPath  
  
-   Microsoft.VisualBasic (Pokud jazyk skript jazyka Visual Basic)  
  
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
 Následující příklad používá k výpočtu obvodu kruhu zadané jeho radius vloženého skriptu.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [Generování dynamických zdrojového kódu a kompilace](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
