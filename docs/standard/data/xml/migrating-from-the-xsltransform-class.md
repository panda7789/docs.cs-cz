---
title: Migrace z třídy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 8383d8cb3e5819c46a0716c59323e492bb9add8e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937993"
---
# <a name="migrating-from-the-xsltransform-class"></a>Migrace z třídy XslTransform

Architektura XSLT byla přepracována v vydání sady Visual Studio 2005. <xref:System.Xml.Xsl.XslTransform> Třída byla nahrazena <xref:System.Xml.Xsl.XslCompiledTransform> třídou.

V následujících částech jsou popsány některé hlavní rozdíly mezi <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform> třídami a.

## <a name="performance"></a>Výkon

<xref:System.Xml.Xsl.XslCompiledTransform> Třída obsahuje mnoho vylepšení výkonu. Nový procesor XSLT zkompiluje šablonu stylů XSLT dolů do společného mezilehlého formátu, podobně jako modul CLR (Common Language Runtime) pro jiné programovací jazyky. Jakmile je šablona stylů zkompilována, může být uložena do mezipaměti a znovu použita.

<xref:System.Xml.Xsl.XslCompiledTransform> Třída také obsahuje další optimalizace, které jsou mnohem rychlejší než <xref:System.Xml.Xsl.XslTransform> třída.

> [!NOTE]
> <xref:System.Xml.Xsl.XslCompiledTransform> I když je celkový výkon třídy lepší než <xref:System.Xml.Xsl.XslTransform> třída, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda <xref:System.Xml.Xsl.XslCompiledTransform> třídy může při prvním volání transformace pracovat pomaleji než <xref:System.Xml.Xsl.XslTransform.Load%2A> metoda <xref:System.Xml.Xsl.XslTransform> třídy. Důvodem je, že soubor XSLT musí být zkompilován před jeho načtením. Další informace najdete v tomto blogovém příspěvku: [XslCompiledTransform pomalejší než XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)

## <a name="security"></a>Zabezpečení

Ve výchozím nastavení <xref:System.Xml.Xsl.XslCompiledTransform> třída zakáže podporu funkce XSLT `document()` a vloženého skriptování. Tyto funkce lze povolit vytvořením <xref:System.Xml.Xsl.XsltSettings> objektu, který má povolené funkce a předáním do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody. Následující příklad ukazuje, jak povolit skriptování a provést transformaci XSLT.

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

Další informace najdete v tématu věnovaném [bezpečnostním hlediskům XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).

## <a name="new-features"></a>Nové funkce

### <a name="temporary-files"></a>Dočasné soubory

Dočasné soubory jsou někdy generovány během zpracování XSLT. Pokud šablona stylů obsahuje bloky skriptu nebo pokud je zkompilována s nastavením ladění nastaveným na hodnotu true, mohou být ve složce% TEMP% vytvořeny dočasné soubory. Můžou nastat případy, kdy se některé dočasné soubory neodstraní kvůli problémům s časováním. Například pokud jsou soubory používány aktuální aplikací AppDomain nebo ladicím programem, finalizační metoda <xref:System.CodeDom.Compiler.TempFileCollection> objektu nebude schopna je odebrat.

<xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Vlastnost může být použita k dalšímu vyčištění, aby bylo zajištěno, že všechny dočasné soubory budou odebrány z klienta.

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Podpora elementu xsl: output a XmlWriter

<xref:System.Xml.Xsl.XslTransform> Třída ignorovala `xsl:output` nastavení při odeslání výstupu transformace do <xref:System.Xml.XmlWriter> objektu. <xref:System.Xml.Xsl.XslCompiledTransform> Třída <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> má vlastnost, která vrací <xref:System.Xml.XmlWriterSettings> objekt obsahující výstupní informace odvozené z `xsl:output` prvku v šabloně stylů. <xref:System.Xml.XmlWriterSettings> Objekt se používá k vytvoření <xref:System.Xml.XmlWriter> objektu se správným nastavením, které lze předat <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě. Toto chování ilustruje následující kód jazyka C#:

```csharp
// Create the XslTransform object and load the style sheet.
XslCompiledTransform xslt = new XslCompiledTransform();
xslt.Load(stylesheet);

// Load the file to transform.
XPathDocument doc = new XPathDocument(filename);

// Create the writer.
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);

// Transform the file and send the output to the console.
xslt.Transform(doc, writer);
writer.Close();
```

### <a name="debug-option"></a>Možnost ladění

<xref:System.Xml.Xsl.XslCompiledTransform> Třída může generovat ladicí informace, které vám umožní ladit šablonu stylů pomocí ladicího programu Microsoft Visual Studio. Další informace naleznete v tématu <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.

## <a name="behavioral-differences"></a>Rozdíly v chování

### <a name="transforming-to-an-xmlreader"></a>Transformace na objekt XmlReader

<xref:System.Xml.Xsl.XslTransform> Třída má několik přetížení transformace, které vracejí výsledky transformace jako <xref:System.Xml.XmlReader> objekt. Tato přetížení lze použít k načtení výsledků transformace do reprezentace v paměti (například <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument>) bez toho, aby vznikla režie serializace a deserializace výsledného stromu XML. Následující kód jazyka C# ukazuje, jak načíst výsledky transformace do <xref:System.Xml.XmlDocument> objektu.

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<xref:System.Xml.Xsl.XslCompiledTransform> Třída nepodporuje transformaci na <xref:System.Xml.XmlReader> objekt. Můžete však něco podobného pomocí <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> metody načíst výsledný strom XML přímo z. <xref:System.Xml.XmlWriter> Následující kód jazyka C# ukazuje, jak provést stejnou úlohu pomocí <xref:System.Xml.Xsl.XslCompiledTransform>.

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a>Volitelné chování

Doporučení W3C XSL Transformers (XSLT) verze 1,0 obsahuje oblasti, ve kterých se může poskytovatel implementace rozhodnout, jak tuto situaci zpracovat. Tyto oblasti se považují za volitelné chování. Existuje několik oblastí, kde se <xref:System.Xml.Xsl.XslCompiledTransform> chová jinak než <xref:System.Xml.Xsl.XslTransform> třída. Další informace najdete v tématu [obnovitelné chyby XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).

### <a name="extension-objects-and-script-functions"></a>Objekty rozšíření a funkce skriptu

<xref:System.Xml.Xsl.XslCompiledTransform>zavádí dvě nová omezení používání funkcí skriptu:

- Z výrazů XPath mohou být volány pouze veřejné metody.

- Přetížení lze odlišit od ostatních v závislosti na počtu argumentů. Pokud má více než jedno přetížení stejný počet argumentů, bude vyvolána výjimka.

V <xref:System.Xml.Xsl.XslCompiledTransform>nástroji je vazba (vyhledávání názvů metod) na funkce skriptu vyvolána v době kompilace a šablony stylů, které pracovaly s XslTransform, mohou způsobit výjimku, když jsou načteny pomocí <xref:System.Xml.Xsl.XslCompiledTransform>.

<xref:System.Xml.Xsl.XslCompiledTransform>podporuje elementy `msxsl:using` s `msxsl:assembly` a podřízenými prvky `msxsl:script` v rámci elementu. Elementy `msxsl:using` a `msxsl:assembly` slouží k deklaraci dalších oborů názvů a sestavení pro použití v bloku skriptu. Další informace najdete v tématu [bloky skriptu pomocí msxsl: Script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) .

<xref:System.Xml.Xsl.XslCompiledTransform>zakáže objekty rozšíření, které mají více přetížení se stejným počtem argumentů.

### <a name="msxml-functions"></a>Funkce MSXML

Do <xref:System.Xml.Xsl.XslCompiledTransform> třídy se přidala podpora pro další funkce MSXML. Následující seznam popisuje nové nebo vylepšené funkce:

- msxsl: node-set: <xref:System.Xml.Xsl.XslTransform> vyžaduje se, aby argument funkce [funkce sady uzlů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) byl fragmentem stromu výsledku. <xref:System.Xml.Xsl.XslCompiledTransform> Třída nemá tento požadavek.

- msxsl: verze: Tato funkce je podporována v <xref:System.Xml.Xsl.XslCompiledTransform>.

- Funkce rozšíření XPath: [funkce MS: String-Compare](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [MS: UTC](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [MS: Namespace-URI](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [MS: funkce local-Name](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [MS: Number Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [MS: Format-Date](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100))a MS: funkce funkcí v [době formátování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) jsou nyní podporovány.

- Funkce rozšíření XPath související se schématem: tyto funkce nejsou nativně podporovány nástrojem <xref:System.Xml.Xsl.XslCompiledTransform>. Lze je však implementovat jako funkce rozšíření.

## <a name="see-also"></a>Viz také

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
