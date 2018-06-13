---
title: Fragment stromu výsledek v transformace
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c64baef3037cdb7b45ede3febacdbc1e76304c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574696"
---
# <a name="result-tree-fragment-in-transformations"></a>Fragment stromu výsledek v transformace
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Výsledek stromu fragmenty, také známé jako výsledek stromu fragmenty, jsou nic jiného než zvláštním typem sada uzlů. Můžete provádět žádné funkce na nich, které lze provést na sada uzlů. Nebo můžete také převést fragment výsledek stromu na uzel nastavit pomocí `node-set()` funkce a následně použít jakékoli místo lze sada uzlů.  
  
 Fragment stromu výsledek je vytvořen v důsledku použití `<xsl:variable>` nebo `<xsl:param>` element konkrétní způsobem v šabloně stylů. Syntaxe `variable` a `parameter` elementy vypadá takto:  
  
```xml  
<xsl:param name=Qname select= XPath Expression >  
    template body  
</xsl:param>  
  
<xsl:variable name=Qname select=XPath Expression >  
    template body  
</xsl:variable>  
```  
  
 Pro `parameter` element, hodnota je přiřazen k úplný název (`Qname`) několika způsoby. Můžete přiřadit výchozí hodnotu parametru vrácením obsah z výrazu XML Path Language (XPath) v `select` atribut, nebo pomocí jeho přiřazení obsah textu šablony.  
  
 Pro `variable` elementu, hodnota je také přiřazený několika způsoby. Můžete je přiřadit vrácením obsah z výraz XPath v `select` atribut, nebo pomocí jeho přiřazení obsah textu šablony.  
  
 Pro oba `parameter` a `variable` prvky, pokud hodnota je přiřazena službou výraz XPath, pak jedním ze čtyř základních typů XPath, bude vrácen: logická hodnota, řetězec, číslo nebo uzel nastavit. Pokud je zadána hodnota pomocí šablony neprázdný text vracen datový typ jiný XPath a který bude fragment stromu výsledek.  
  
 Pokud proměnnou je vázán na fragment výsledek stromu místo jedním ze čtyř typů dat základní XPath, to je jenom jednou, dotaz XPath vrátí typ, který není jedním z čtyři typy objektů jazyka XPath. Výsledek stromu fragmenty a jejich chování jsou popsané v specifikace World Wide Web Consortium (W3C) na www.w3.org/XSLT, část 11.1 výsledek stromu fragmenty prostřednictvím části 11.6 předání parametrů šablon. Také část 1 Úvod popisuje, jak šablony může obsahovat elementy z oboru názvů XSLT, které vrátí nebo vytvoří výsledek fragmenty stromu.  
  
 Fragment stromu výsledek koncept, se chová jako uzel s nic jiného než jediném kořenovém uzlu. Zbývající uzly vrátil jsou však podřízené uzly. Podřízené uzly prostřednictvím kódu programu najdete zkopírujte fragment stromu výsledek výsledek stromu pomocí `<xsl:copy-of>` elementu. Při kopírování z provádí, jsou všechny podřízené uzly také zkopírován do stromu výsledek v pořadí. Dokud `copy` nebo `copy-of` se používá, fragment stromu výsledek není součástí stromu výsledek nebo výstup transformace.  
  
 Iterace nad vrácený uzly stromu fragment výsledek <xref:System.Xml.XPath.XPathNavigator> se používá. Následující ukázka kódu ukazuje, jak vytvořit fragment výsledek stromové struktury v rámci šablony stylů voláním funkce s parametrem `fragment`, který obsahuje XML.  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
    <xsl:var name="fragment">  
        <node1>  
            <node2/>  
        </node1>  
    <xsl:var>  
  
  <msxsl:script language="C#" implements-prefix="user">  
    function NodeFragment(XPathNavigator nav)  
    {  
      if (nav.HasSelection == false)  
        XPathNavigator.MoveToNext();  
      return;  
    }  
  </msxsl:script>  
  
    <xsl:template match="/">  
            <xsl:value-of select="user:NodeFragment(msxml:node-set($fragment))"/>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 Zde je další ukázku zobrazující proměnnou, která je ve formátu RTF (RICH Text Format), a proto nastavte typ fragment stromu výsledek, který není převeden do uzlu. Místo toho je předán do funkce skript a <xref:System.Xml.XPath.XPathNavigator> se používá k přejděte přes uzly.  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
        xmlns:user="urn:books"  
        exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>  
  
<xsl:variable name="node-fragment">  
    <book>Book1</book>  
    <book>Book2</book>  
    <book>Book3</book>  
    <book>Book4</book>  
</xsl:variable>  
  
<msxsl:script implements-prefix="user" language="c#">  
  
<![CDATA[  
    string func(XPathNavigator nav)  
    {  
        bool b = nav.MoveToFirstChild();  
        if (b)  
            return nav.Value;  
        else  
            return "Does not exist";  
    }  
  
]]>  
  
</msxsl:script>  
  
<xsl:template match="/">  
    <first_book>  
        <xsl:value-of select="user:func($node-fragment)"/>  
    </first_book>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 Výsledek převod žádné XML pomocí této šablony stylů se zobrazí v následující výstup.  
  
## <a name="output"></a>Výstup  
  
```xml  
<first_book xmlns:user="urn:books">Book1</first_book>  
```  
  
 Jak jsme uvedli výše, `node-set` funkce umožňuje převést fragment stromu výsledek sada uzlů. Výsledný uzel vždy obsahuje jeden uzel, který je kořenový uzel stromu. Pokud převedete fragment výsledek stromu na uzel nastavit, a můžete ji použít kdekoli sada regulární uzlů se používá, například jako pro každý příkaz nebo v hodnotě `select` atribut. Následující řádky kódu ukazují fragment převáděn na uzlu nastavení a použita jako sada uzlů:  
  
 `<xsl:for-each select="msxsl:node-set($node-fragment)">`  
  
 `<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`  
  
 Při převodu fragment sada uzlů, nadále používat <xref:System.Xml.XPath.XPathNavigator> přejděte nad ním. Pro sada uzlů můžete použít <xref:System.Xml.XPath.XPathNodeIterator> místo.  
  
 V následujícím příkladu `$var` je proměnná, která je uzel stromu v šabloně stylů. Příkaz pro každou kombinaci s `node-set` fungovat, umožňuje uživatelům Iterujte přes tento strom jako sada uzlů.  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
    <xsl:variable name="states">  
        <node1>AL</node1>  
        <node1>CA</node1>  
        <node1>CO</node1>  
        <node1>WA</node1>  
    </xsl:variable>  
  
    <xsl:template match="/">  
            <xsl:for-each select="msxsl:node-set($states)"/>   
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 Dalším příkladem proměnné, která je ve formátu RTF, a proto fragment stromu výsledek typu, který je převést na uzlu nastavit před předáním funkce skriptu jako XPathNodeIterator.  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
        xmlns:user="urn:books"  
        exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>  
  
<xsl:variable name="node-fragment">  
    <book>Book1</book>  
    <book>Book2</book>  
    <book>Book3</book>  
    <book>Book4</book>  
</xsl:variable>  
  
<msxsl:script implements-prefix="user" language="c#">  
  
<![CDATA[  
    string func(XPathNodeIterator it)  
    {  
        it.MoveNext();   
        return it.Current.Value;   
        //it.Current returns XPathNavigator positioned on the current node  
    }  
  
]]>  
  
</msxsl:script>  
<xsl:template match="/">  
    <books>  
        <xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>  
    </books>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 Toto je výsledek transformace XML pomocí této šablony stylů:  
  
```xml  
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
