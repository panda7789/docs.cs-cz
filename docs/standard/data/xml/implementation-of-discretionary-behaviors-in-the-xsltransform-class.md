---
title: Implementace volitelného chování ve třídě XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
ms.openlocfilehash: b37cb0f4bf9a85053d70d549ae005c7d50a50bc0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710801"
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>Implementace volitelného chování ve třídě XslTransform

> [!NOTE]
> Třída <xref:System.Xml.Xsl.XslTransform> je v .NET Framework 2,0 zastaralá. Pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform> můžete provádět transformace XSLT (Extensible Stylesheet Language). Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .

Volitelné chování jsou popsána jako chování uvedená v [doporučení XSLT verze 1,0 v konsorcium World Wide Web (W3C)](https://www.w3.org/TR/1999/REC-xslt-19991116), ve kterém poskytovatel implementací zvolí jednu z několika možných možností jako způsob, jak provést určitou situaci. Například v části 7,3 vytvoření instrukcí pro zpracování, doporučení W3C říká, že se jedná o chybu při vytváření instance obsahu `xsl:processing-instruction` vytvoří jiné uzly než textové uzly. V případě některých problémů konsorcium W3C informuje o tom, jaké rozhodnutí by mělo být provedeno v případě, že se procesor rozhodne zotavit z chyby. V případě problému uvedeného v části 7,3 oznámí W3C, že implementace se může zotavit z této chyby ignorováním uzlů a jejich obsahu.

Pro každé z volitelných chování povolených konsorciem W3C proto tabulka níže uvádí volitelné chování implementované pro .NET Framework implementaci <xref:System.Xml.Xsl.XslTransform> třídy a informace o tom, co se zabývá doporučením konsorcia W3C 1,0 v tomto problému.

|Problém|Chování|Část|
|-------------|--------------|-------------|
|Textový uzel odpovídá `xsl:strip-space` i `xsl:preserve-space`.|Obnovit|3.4|
|Zdrojový uzel se shoduje s více než jedním pravidlem šablony.|Obnovit|5.5|
|Obor názvů URI (Uniform Resource Identifier) je deklarovaný jako alias pro více identifikátorů URI oboru názvů, přičemž všechny mají stejnou prioritu importu.|Obnovit|7.1.1|
|Atribut Name v `xsl:attribute` a `xsl:element` vygenerovaný ze šablony hodnoty atributu není platný kvalifikovaný název (QName).|Vyvolaná výjimka|7.1.2 a 7.1.3|
|Přidáním atributu do elementu po podřízených uzlech již byly přidány do uzlu element.|Obnovit|7.1.3|
|Přidání atributu pro cokoli jiného než uzel elementu.|Obnovit|7.1.3|
|Vytvoření instance obsahu `xsl:attribute`ho prvku není textový uzel.|Obnovit|7.1.3|
|Dvě sady atributů mají stejnou prioritu importu a rozbalený název. Oba mají stejný atribut a neexistuje žádná sada atributů, která obsahuje společný atribut se stejným názvem s vyšší důležitostí.|Obnovit|7.1.4|
|atribut názvu `xsl:processing-instruction` nepřinese název bez dvojtečky (NCName) a cíl instrukcí pro zpracování.|Obnovit|7.3|
|Vytvoření instance obsahu `xsl:processing-instruction` vytvoří jiné uzly než textové uzly.|Obnovit|7.3|
|Výsledky vytváření instancí obsahu `xsl:processing-instruction` obsahují řetězec "`?>`".|Obnovit|7.3|
|Výsledky vytváření instancí obsahu `xsl:comment` obsahují řetězec "--" nebo končí znakem "-".|Obnovit|7,4|
|Výsledky vytvoření instance obsahu `xsl:comment` vytvoří jiné uzly než textové uzly.|Obnovit|7,4|
|Šablona v rámci prvku variabilní vazby vrací uzel atributu nebo uzel oboru názvů.|Obnovit|11.2|
|Došlo k chybě při načítání prostředku z identifikátoru URI předaného do funkce dokumentu.|Vyvolaná výjimka|12.1|
|Odkaz na identifikátor URI ve funkci dokumentu obsahuje identifikátor fragmentu a při zpracování identifikátoru fragmentu došlo k chybě.|Vyvolaná výjimka|12.1|
|Existuje více atributů se stejným názvem, které nejsou pojmenovány `cdata-section-elements` v `xls:output`a tyto atributy mají stejnou prioritu importu.|Obnovit|16|
|Procesor nepodporuje hodnotu kódování znaků zadanou v atributu `encoding` elementu `xsl:output`.|Obnovit|16.1|
|`disable-output-escaping` se používá pro textový uzel a tento textový uzel se používá k vytvoření dalšího objektu, než je textový uzel ve stromové struktuře výsledek.|atribut `disable-output-escaping` se ignoruje.|16.4|
|Převod fragmentu stromu výsledků na číslo nebo řetězec, pokud fragment stromu výsledku obsahuje textový uzel s povoleným výstupním uvozovacím příkazem.|Ignorováno|16.4|
|Pro znaky, které nelze reprezentovat v kódování, které procesor XSLT používá pro výstup, je zakázané výstupní uvozovací znaky.|Ignorováno|16.4|
|Přidání uzlu oboru názvů do elementu po přidání podřízených objektů nebo po jejich přidání do objektu Namespace|Obnovit|Seznam chyb E25|
|`xsl:number` je NaN, infinitá nebo menší než 0,5.|Obnovit|Seznam chyb E24|
|Druhý argument node-set pro funkci dokumentu je prázdný a odkaz na identifikátor URI je relativní.|Obnovit|Seznam chyb Žádný typu E14|

Oddíly z seznam chyb najdete v článku [specifikace XSL (XSLT) verze 1,0 specifikace seznam chyb](https://www.w3.org/1999/11/REC-xslt-19991116-errata/)W3C.

## <a name="custom-defined-implementation-behaviors"></a>Chování uživatelsky definované implementace

Existuje chování, které je jedinečné pro implementaci <xref:System.Xml.Xsl.XslTransform> třídy. Tato část popisuje implementaci `xsl:sort` specifickou pro konkrétního zprostředkovatele a volitelné funkce, které jsou podporovány třídou <xref:System.Xml.Xsl.XslTransform>.

## <a name="xslsort"></a>sort

Při použití transformace k řazení se v doporučení W3C XSLT 1,0 zobrazí několik pozorování. Možnosti jsou následující:

- Dva procesory XSLT mohou být v souladu s procesory, ale stále mohou řadit odlišně.

- Ne všechny procesory XSLT podporují stejné jazyky.

- S ohledem na jazyky se můžou různé procesory lišit podle jejich řazení u určitého jazyka, který není zadaný na `xsl:sort.`.

Následující tabulka uvádí chování při řazení implementující pro každý datový typ v .NET Framework implementaci transformace pomocí <xref:System.Xml.Xsl.XslTransform>:

|Datový typ|Chování řazení|
|---------------|----------------------|
|Text|Data jsou řazena pomocí řetězce modulu CLR (Common Language Runtime). Compare a kulturního národního prostředí. Když se datový typ rovná "text", řazení ve třídě <xref:System.Xml.Xsl.XslTransform> se chová stejně jako chování porovnávání řetězců CLR.|
|Počet|Číselné hodnoty jsou považovány za čísla jazyka XML Path (XPath) a jsou seřazeny podle podrobností uvedených v [doporučení jazyka XML pro cestu jazyka W3C (XPath) verze 1,0, oddíl 3,5](https://www.w3.org/TR/1999/REC-xpath-19991116/#numbers).|

## <a name="optional-features-supported"></a>Volitelné podporované funkce

V následující tabulce jsou uvedeny funkce, které jsou volitelné pro implementaci procesoru XSLT a jsou implementovány ve třídě <xref:System.Xml.Xsl.XslTransform>.

|Funkce|Umístění odkazu|Poznámky|
|-------------|------------------------|-----------|
|`disable-output-escaping` atribut u značek `<xsl:text...>` a `<xsl:value-of...>`.|Doporučení W3C XSLT 1,0,<br /><br /> Oddíl 16,4|Atribut `disable-output-escaping` je ignorován, pokud jsou prvky `xsl:text` nebo `xsl:value-of` použity v prvku `xsl:comment`, `xsl:processing-instruction`nebo `xsl:attribute`.<br /><br /> Fragmenty stromu výsledků, které obsahují text a textový výstup, který byl uvozen řídicími znaky, nejsou podporovány.<br /><br /> Atribut Disable-Output-uvozovacího prvku se při transformaci na objekt <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> ignoruje.|

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XslTransform>
- [Třída XslTransform implementuje procesor XSLT](xsltransform-class-implements-the-xslt-processor.md)
- [Transformace XSLT s třídou XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [XPathNavigator v transformacích](xpathnavigator-in-transformations.md)
- [XPathNodeIterator v transformacích](xpathnodeiterator-in-transformations.md)
- [Vstup XPathDocument do XslTransform](xpathdocument-input-to-xsltransform.md)
- [Vstup XmlDataDocument do XslTransform](xmldatadocument-input-to-xsltransform.md)
- [Vstup XmlDocument do XslTransform](xmldocument-input-to-xsltransform.md)
