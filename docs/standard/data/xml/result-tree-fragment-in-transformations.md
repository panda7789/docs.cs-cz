---
title: Fragment stromu výsledků v transformacích
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca6871886a64c864451eb3e2f6f4843e0150123b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43805712"
---
# <a name="result-tree-fragment-in-transformations"></a>Fragment stromu výsledků v transformacích

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) Další informace.

 Fragmenty stromu výsledek, označované také jako fragmenty stromu výsledek nejsou nic jiného než speciální typ sady uzlů. Všechny funkce můžete provádět s nimi, které lze provést na sadu uzlu. Nebo můžete také převést fragment stromu výsledek uzel sady s použitím `node-set()` funkce a následně ji jakéhokoli místa, že sada uzlů je možné použít.

 Fragment stromu výsledek je vytvořen pomocí `<xsl:variable>` nebo `<xsl:param>` element specifickým způsobem v šabloně stylů. Syntaxe `variable` a `parameter` prvky vypadá takto:

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

Pro `parameter` elementu, je hodnota přiřazena kvalifikovaný název (`Qname`) několika způsoby. Můžete přiřadit výchozí hodnotu parametru tak, že vrací obsah z výraz jazyk XML Path (XPath) v `select` atribut, nebo za její přiřazení obsahu těla šablony.

Pro `variable` elementu, hodnota je také přiřazený několika způsoby. Vrácením obsahu z výrazu XPath v ji můžete přiřadit `select` atribut, nebo za její přiřazení obsahu těla šablony.

Pro obě `parameter` a `variable` prvky, pokud je hodnota přiřazena pomocí výrazu XPath, pak jednu z čtyři základní typy jazyka XPath bude vrácen: logická hodnota, řetězec, číslo nebo uzel nastavení. Pokud hodnota je uvedená pomocí prázdné šablony textu, pak je vrácený datový typ výraz XPath a bude fragment stromu výsledek.

Pokud proměnná je vázán k fragment stromu výsledek místo jedné z čtyři základní typy dat XPath, pak toto je pouze, že dotaz XPath vrátí typ, který není jedním ze čtyř typů objektů jazyka XPath. Jejich chování a výsledků fragmenty jsou popsány v [specifikace World Wide Web Consortium (W3C)](https://www.w3.org/TR/xslt-10/), [části 11.1 výsledků fragmenty](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) prostřednictvím [části 11.6 předávání Parametry šablony](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates). Navíc [části 1 Úvod](https://www.w3.org/TR/xslt-10/#section-Introduction) popisuje, jak šablony může obsahovat elementy z oboru názvů XSLT, které vrátí nebo vytvoří výsledků fragmenty stromu.

Fragment stromu výsledek koncept, se chová jako uzel nastavení, není nic víc než jeden kořenový uzel. Ostatní uzly vrátil jsou však podřízené uzly. Programově zobrazit podřízené uzly, zkopírujte do stromu výsledek pomocí stromu fragmentu výsledek `<xsl:copy-of>` elementu. Při kopírování sady se provádí, všechny podřízené uzly jsou zkopírovány také do stromu výsledek v sekvenci. Dokud `copy` nebo `copy-of` se používá, fragment stromu výsledek není součástí stromu výsledek nebo výstup z transformace.

K iteraci přes vrácená uzlů fragment stromu výsledek <xref:System.Xml.XPath.XPathNavigator> se používá. Následující příklad kódu ukazuje, jak vytvořit fragment stromu výsledek předloze se styly voláním funkce s parametrem `fragment`, který obsahuje XML.

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

Tady je další ukázku zobrazující proměnnou, která je ve formátu RTF (RICH Text Format), a proto nastavení typu stromu fragmentu výsledek, který není převedena na uzlu. Místo toho je předán do funkce skriptu a <xref:System.Xml.XPath.XPathNavigator> slouží k navigaci v uzlech.

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

Výsledek transformace všechny XML pomocí této šablony stylů se zobrazí následující výstup.

## <a name="output"></a>Výstup

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

Jak je uvedeno výše, `node-set` funkce lze převést na sadu uzlu fragment stromu výsledek. Výsledný uzel vždy obsahuje jeden uzel, který je kořenový uzel stromu. Pokud převedete fragment výsledkového stromu na uzel nastavena, pak jste ji mohli používat kdekoli sadu regulární uzlu se používá, například jako v pro každý příkaz nebo v hodnotě `select` atribut. Následující řádky kódu zobrazit fragment převáděn na nastavit a použít jako sada uzlů uzlu:

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

Když fragment je převést na sadu uzlu, kterou již nebudete používat <xref:System.Xml.XPath.XPathNavigator> přejít nad ním. Pro sadu uzlu, je použít <xref:System.Xml.XPath.XPathNodeIterator> místo.

V následujícím příkladu `$var` je proměnná, která je uzel stromu v šabloně stylů. Pro každý příkaz v kombinaci s `node-set` fungovala, umožňuje uživateli k iteraci přes tento strom jako sada uzlů.

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

Tady je další příklad proměnné, která je ve formátu RTF, a proto z modulu snap-in fragment stromu výsledek typu, který je převeden na uzel nastaven před předáním funkci skript tak, aby objekt XPathNodeIterator.

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

Výsledek transformace XML pomocí této šablony stylů je následující:

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a>Viz také

<xref:System.Xml.XPath.XPathNodeIterator>  
<xref:System.Xml.XPath.XPathNodeIterator>  
[Transformace XSLT s třídou XslTransform](xslt-transformations-with-the-xsltransform-class.md)  
[Třída XslTransform implementuje procesor XSLT](xsltransform-class-implements-the-xslt-processor.md)  
