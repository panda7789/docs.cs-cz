---
title: Migrace z třídy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 95e71e1fdd0ded145025316a5d6597b27a6cc970
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710645"
---
# <a name="migrating-from-the-xsltransform-class"></a>Migrace z třídy XslTransform

Architektura XSLT byla přepracována v vydání sady Visual Studio 2005. Třída <xref:System.Xml.Xsl.XslTransform> byla nahrazena <xref:System.Xml.Xsl.XslCompiledTransform>ou třídou.

V následujících částech jsou popsány některé z hlavních rozdílů mezi <xref:System.Xml.Xsl.XslCompiledTransform> a <xref:System.Xml.Xsl.XslTransform>mi třídami.

## <a name="performance"></a>Výkon

Třída <xref:System.Xml.Xsl.XslCompiledTransform> zahrnuje mnoho vylepšení výkonu. Nový procesor XSLT zkompiluje šablonu stylů XSLT dolů do společného mezilehlého formátu, podobně jako modul CLR (Common Language Runtime) pro jiné programovací jazyky. Jakmile je šablona stylů zkompilována, může být uložena do mezipaměti a znovu použita.

Třída <xref:System.Xml.Xsl.XslCompiledTransform> obsahuje také další optimalizace, které jsou mnohem rychlejší než <xref:System.Xml.Xsl.XslTransform>á třída.

> [!NOTE]
> I když je celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třídy lepší než <xref:System.Xml.Xsl.XslTransform> třídy, metoda <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> třídy <xref:System.Xml.Xsl.XslCompiledTransform> může při prvním volání na transformaci pracovat pomaleji než metoda <xref:System.Xml.Xsl.XslTransform.Load%2A> třídy <xref:System.Xml.Xsl.XslTransform>. Důvodem je, že soubor XSLT musí být zkompilován před jeho načtením. Další informace najdete v tomto blogovém příspěvku: [XslCompiledTransform pomalejší než XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)

## <a name="security"></a>Zabezpečení –

Ve výchozím nastavení třída <xref:System.Xml.Xsl.XslCompiledTransform> zakáže podporu funkce `document()` XSLT a vloženého skriptování. Tyto funkce lze povolit vytvořením objektu <xref:System.Xml.Xsl.XsltSettings> s povolenými funkcemi a předáním do metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>. Následující příklad ukazuje, jak povolit skriptování a provést transformaci XSLT.

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

Další informace najdete v tématu věnovaném [bezpečnostním hlediskům XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).

## <a name="new-features"></a>Nové funkce

### <a name="temporary-files"></a>Dočasné soubory

Dočasné soubory jsou někdy generovány během zpracování XSLT. Pokud šablona stylů obsahuje bloky skriptu nebo pokud je zkompilována s nastavením ladění nastaveným na hodnotu true, mohou být ve složce% TEMP% vytvořeny dočasné soubory. Můžou nastat případy, kdy se některé dočasné soubory neodstraní kvůli problémům s časováním. Například pokud jsou soubory používány aktuální aplikací AppDomain nebo ladicím programem, finalizační metoda objektu <xref:System.CodeDom.Compiler.TempFileCollection> nebude schopna je odebrat.

Vlastnost <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> lze použít k dodatečnému vyčištění, aby bylo zajištěno, že všechny dočasné soubory budou odebrány z klienta.

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Podpora elementu xsl: output a XmlWriter

Třída <xref:System.Xml.Xsl.XslTransform> ignorovala `xsl:output` nastavení, když byl výstup transformace odeslán do objektu <xref:System.Xml.XmlWriter>. Třída <xref:System.Xml.Xsl.XslCompiledTransform> má vlastnost <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A>, která vrací objekt <xref:System.Xml.XmlWriterSettings> obsahující výstupní informace odvozené z prvku `xsl:output` šablon stylů. Objekt <xref:System.Xml.XmlWriterSettings> slouží k vytvoření objektu <xref:System.Xml.XmlWriter> se správným nastavením, které lze předat metodě <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>. Toto chování C# je znázorněno v následujícím kódu:

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

Třída <xref:System.Xml.Xsl.XslCompiledTransform> může generovat ladicí informace, které vám umožní ladit šablonu stylů pomocí ladicího programu Microsoft Visual Studio. Další informace naleznete v tématu <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.

## <a name="behavioral-differences"></a>Rozdíly v chování

### <a name="transforming-to-an-xmlreader"></a>Transformace na objekt XmlReader

Třída <xref:System.Xml.Xsl.XslTransform> obsahuje několik přetížení transformace, které vracejí výsledky transformace jako objekt <xref:System.Xml.XmlReader>. Tato přetížení lze použít k načtení výsledků transformace do reprezentace v paměti (například <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument>) bez toho, aby vznikla režie serializace a deserializace výsledného stromu XML. Následující C# kód ukazuje, jak načíst výsledky transformace do objektu <xref:System.Xml.XmlDocument>.

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

Třída <xref:System.Xml.Xsl.XslCompiledTransform> nepodporuje transformaci na objekt <xref:System.Xml.XmlReader>. Můžete však něco podobného pomocí metody <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> k načtení výsledného stromu XML přímo z <xref:System.Xml.XmlWriter>. Následující C# kód ukazuje, jak provést stejnou úlohu pomocí <xref:System.Xml.Xsl.XslCompiledTransform>.

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

<xref:System.Xml.Xsl.XslCompiledTransform> zavádí dvě nová omezení pro použití funkcí skriptu:

- Z výrazů XPath mohou být volány pouze veřejné metody.

- Přetížení lze odlišit od ostatních v závislosti na počtu argumentů. Pokud má více než jedno přetížení stejný počet argumentů, bude vyvolána výjimka.

V <xref:System.Xml.Xsl.XslCompiledTransform>vazba (vyhledávání názvů metod) ke skriptovým funkcím probíhá v době kompilace a šablony stylů, které pracovaly s XslTransform, mohou způsobit výjimku, když jsou načteny pomocí <xref:System.Xml.Xsl.XslCompiledTransform>.

<xref:System.Xml.Xsl.XslCompiledTransform> podporuje s podřízenými prvky `msxsl:using` a `msxsl:assembly` v rámci elementu `msxsl:script`. Prvky `msxsl:using` a `msxsl:assembly` slouží k deklaraci dalších oborů názvů a sestavení pro použití v bloku skriptu. Další informace najdete v tématu [bloky skriptu pomocí msxsl: Script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) .

<xref:System.Xml.Xsl.XslCompiledTransform> zakáže objekty rozšíření, které mají více přetížení se stejným počtem argumentů.

### <a name="msxml-functions"></a>Funkce MSXML

Do třídy <xref:System.Xml.Xsl.XslCompiledTransform> se přidala podpora dalších funkcí MSXML. Následující seznam popisuje nové nebo vylepšené funkce:

- msxsl: node-set: <xref:System.Xml.Xsl.XslTransform> nutné, aby argument funkce [funkce sady uzlů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) byl fragmentem stromu výsledku. Třída <xref:System.Xml.Xsl.XslCompiledTransform> nemá tento požadavek.

- msxsl: Version: Tato funkce je podporována v <xref:System.Xml.Xsl.XslCompiledTransform>.

- Funkce rozšíření XPath: [funkce MS: String-Compare](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [MS: UTC](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [MS: Namespace-URI](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [MS: funkce local-Name](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [MS: Number Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [MS: Format-Date](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100))a MS: funkce funkcí v [době formátování](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) jsou nyní podporovány.

- Funkce rozšíření XPath související se schématem: tyto funkce se nativně nepodporují <xref:System.Xml.Xsl.XslCompiledTransform>. Lze je však implementovat jako funkce rozšíření.

## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
