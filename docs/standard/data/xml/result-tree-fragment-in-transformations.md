---
title: Fragment stromu výsledků v transformacích
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
ms.openlocfilehash: e454c1194e8c280042857f106e22d0d0509417e3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156358"
---
# <a name="result-tree-fragment-in-transformations"></a>Fragment stromu výsledků v transformacích

> [!NOTE]
> Třída <xref:System.Xml.Xsl.XslTransform> je v .NET Framework 2,0 zastaralá. Pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform> můžete provádět transformace XSLT (Extensible Stylesheet Language). Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .

 Fragmenty stromové struktury výsledků, označované také jako fragmenty stromové struktury výsledků, nejsou žádné více než speciální typ sady uzlů. Můžete na nich provádět libovolné funkce, které lze provést v sadě uzlů. Nebo můžete také převést fragment stromu výsledků na sadu uzlů pomocí funkce `node-set()` a následně jej použít na místo, kde lze použít sadu uzlů.

 Fragment stromové struktury výsledků je vytvořen v důsledku použití prvku `<xsl:variable>` nebo `<xsl:param>` v určitém způsobu v šabloně stylů. Syntaxe pro `variable` a `parameter` prvky je následující:

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

Pro `parameter` element je hodnota přiřazena k kvalifikovanému názvu (`Qname`) několika způsoby. Můžete určit výchozí hodnotu parametru vrácením obsahu z výrazu jazyka XML Path (XPath) v atributu `select` nebo přiřazením obsahu textu šablony.

Pro `variable` element je hodnota také přiřazena několika způsoby. Můžete ji přiřadit vrácením obsahu z výrazu XPath v atributu `select` nebo přiřazením obsahu textu šablony.

Pro prvky `parameter` i `variable` platí, že pokud je hodnota přiřazena výrazem XPath, pak bude vrácen jeden ze čtyř základních typů XPath: Boolean, String, Number nebo set Node. Pokud je hodnota zadána pomocí neprázdného těla šablony, pak je vrácen datový typ, který není XPath, a který bude fragmentem stromu výsledek.

Pokud je proměnná svázána s fragmentem stromu výsledek místo jednoho ze čtyř základních datových typů XPath, je to jediná doba, kterou dotaz XPath vrátí typ, který není jedním ze čtyř typů objektů XPath. Fragmenty stromu výsledků a jejich chování jsou popsány v tématu [specifikace konsorcium World Wide Web (W3C)](https://www.w3.org/TR/xslt-10/), [fragmenty stromu výsledků oddílu 11,1](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) až do [části 11,6 předání parametrů do šablon](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates). [Oddíl 1 Úvod](https://www.w3.org/TR/xslt-10/#section-Introduction) popisuje, jak šablony mohou obsahovat prvky z oboru názvů XSLT, který vrací nebo vytváří fragmenty stromu výsledků.

Fragment stromu výsledku v konceptu se chová jako sada uzlů s nevětším než jedním kořenovým uzlem. Zbývající uzly vráceny ale jsou podřízené uzly. Pro programové zobrazení podřízených uzlů zkopírujte fragment stromu výsledek do stromu výsledek pomocí elementu `<xsl:copy-of>`. Po provedení kopie jsou všechny podřízené uzly zkopírovány také do stromu výsledek v sekvenci. Dokud se nepoužije `copy` nebo `copy-of`, fragment stromu výsledku není součástí stromu výsledků nebo výstupem transformace.

Pro iteraci na vrácených uzlech fragmentu stromu výsledek se používá <xref:System.Xml.XPath.XPathNavigator>. Následující ukázka kódu ukazuje, jak vytvořit fragment stromu výsledku v rámci předlohy se styly voláním funkce s parametrem `fragment`, který obsahuje XML.

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

Tady je další ukázka ukazující proměnnou, která je ve formátu RTF (Rich Text Format), a proto typ fragmentu stromu výsledků, který není převeden na sadu uzlů. Místo toho je předán do funkce skriptu a <xref:System.Xml.XPath.XPathNavigator> slouží k procházení uzlů.

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

Výsledek transformace jakéhokoli XML s touto šablonou stylů je zobrazen v následujícím výstupu.

## <a name="output"></a>Výstup

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

Jak je uvedeno výše, funkce `node-set` umožňuje převést fragment stromu výsledků na sadu uzlů. Výsledný uzel vždy obsahuje jeden uzel, který je kořenovým uzlem stromu. Převedete-li fragment stromu výsledků na sadu uzlů, můžete jej použít kdekoli, kde je použita běžná sada uzlů, například v příkazu for-each nebo v hodnotě atributu `select`. Následující řádky kódu znázorňují fragment, který je převeden na sadu uzlů a který se používá jako sada uzlů:

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

Když je fragment převeden na sadu uzlů, již nepoužíváte <xref:System.Xml.XPath.XPathNavigator> k procházení. Pro sadu uzlů místo toho použijte <xref:System.Xml.XPath.XPathNodeIterator>.

V následujícím příkladu `$var` je proměnná, která je stromem uzlů v šabloně stylů. Příkaz for-each v kombinaci s funkcí `node-set` umožňuje uživateli iterovat v rámci tohoto stromu jako sadu uzlů.

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

Tady je další příklad proměnné, která je ve formátu RTF, a proto fragment stromu výsledku typu, která je převedená na uzel, než se předává do funkce skriptu jako objekt XPathNodeIterator.

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

Následuje výsledek transformace XML s touto šablonou stylů:

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a>Viz také

- <xref:System.Xml.XPath.XPathNodeIterator>
- [Transformace XSLT s třídou XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Třída XslTransform implementuje procesor XSLT](xsltransform-class-implements-the-xslt-processor.md)
