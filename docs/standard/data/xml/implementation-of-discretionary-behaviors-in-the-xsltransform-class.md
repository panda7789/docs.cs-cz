---
title: Implementace volitelného chování ve třídě XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0a6b3faff0208634e711b9d7908e3fd8dc640ae
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170842"
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>Implementace volitelného chování ve třídě XslTransform

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralé v rozhraní .NET Framework 2.0. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) Další informace.

Volitelného chování, které jsou popsány jako uvedené v chování [World Wide Web Consortium (W3C) transformace XSL (XSLT) verze 1.0 doporučení](https://www.w3.org/TR/1999/REC-xslt-19991116), ve kterém implementaci zprostředkovatele vybere jeden z několika možných možnosti jako způsob, jak zpracovat situaci. Například část 7.3 vytváření zpracování pokyny, doporučení W3C říká, jedná se o chybu, pokud vytvoření instance obsah `xsl:processing-instruction` vytvoří uzly než textové uzly. Pro některé problémy W3C říká je třeba jaká rozhodnutí pokud procesor rozhodne zotavit z chyby. Na problém uvedený v části 7.3 W3C říká, že implementace můžete obnovit tuto chybu ignorovat uzly a jejich obsah.

Proto se pro každou z volitelného chování dovolují W3C, následující tabulka uvádí volitelného chování implementována pro implementaci rozhraní .NET Framework <xref:System.Xml.Xsl.XslTransform> třídy a jaké části v doporučení W3C XSLT 1.0, že tento problém je popsáno.

|Problém|Chování|Section|
|-------------|--------------|-------------|
|Textový uzel odpovídá obě `xsl:strip-space` a `xsl:preserve-space`.|Obnovit|3.4|
|Zdrojový uzel odpovídá více než jedno pravidlo šablony.|Obnovit|5.5|
|Obor názvů identifikátoru URI (Uniform Resource) je deklarován jako alias pro více identifikátorů URI oboru názvů, všechny mají stejnou přednost importovat.|Obnovit|7.1.1|
|Atribut name v `xsl:attribute` a `xsl:element` vygenerovaná šabloně hodnoty atributu není platný úplný název (QName).|Došlo k výjimce|7.1.2 a 7.1.3|
|Přidání atributu do elementu po podřízené uzly již byly přidány do uzlu elementu.|Obnovit|7.1.3|
|Přidání atributu na jinou hodnotu než uzlu elementu.|Obnovit|7.1.3|
|Vytvoření instance obsah `xsl:attribute` element není textový uzel.|Obnovit|7.1.3|
|Dvě atribut sady mají stejnou přednost importovat a rozbalený název. Obě mají stejný atribut a neexistuje žádný atribut nastavení obsahující společný atribut se stejným názvem, s vyšší význam.|Obnovit|7.1.4|
|`xsl:processing-instruction` atribut názvu nevydává no dvojtečka název (NCName) a cíl zpracování instrukcí.|Obnovit|7.3|
|Vytvoření instance obsah `xsl:processing-instruction` vytvoří uzly než textové uzly.|Obnovit|7.3|
|Výsledky pro vytváření instancí obsah `xsl:processing-instruction` obsahuje řetězec "`?>`".|Obnovit|7.3|
|Výsledky vytvoření instance obsah `xsl:comment` obsahuje řetězec "--", nebo končí řetězcem "-".|Obnovit|7.4|
|Výsledky pro vytváření instancí obsah `xsl:comment` vytvoří uzly než textové uzly.|Obnovit|7.4|
|Šablony v rámci elementu vazby proměnné vrátí uzel atributu nebo uzel oboru názvů.|Obnovit|11.2|
|Je chyba při načítání prostředku z identifikátoru URI předaného do funkce dokumentu.|Došlo k výjimce|12.1|
|Odkaz na identifikátor URI ve funkci dokumentu obsahuje identifikátor fragmentu a dojde k chybě při zpracování identifikátor fragmentu.|Došlo k výjimce|12.1|
|Existuje více atributů se stejným názvem, které nejsou s názvem `cdata-section-elements` v `xls:output`, a tyto atributy mají stejnou přednost importovat.|Obnovit|16|
|Procesor nepodporuje hodnotu uvedenou v kódování znaků `encoding` atribut `xsl:output` elementu.|Obnovit|16.1|
|`disable-output-escaping` se používá pro textový uzel, a tento textový uzel se používá k vytvoření něco jiného než textový uzel ve stromu výsledek.|`disable-output-escaping` Atribut se ignoruje.|16.4|
|Převod fragment stromu výsledek na číslo nebo řetězec. Pokud fragment stromu výsledek obsahuje textový uzel se výstup uvození povolena.|Ignorováno|16.4|
|Výstup uvození je zakázaná pro znaky, které nelze reprezentovat v kódování, procesoru XSLT se používá pro výstup.|Ignorováno|16.4|
|Přidání uzlu do oboru názvů na prvek po podřízené objekty byly přidány do ní nebo po atributy byly přidány k němu|Obnovit|E25 chyby|
|`xsl:number` je NaN, nekonečné nebo menší než 0,5.|Obnovit|Errata e24|
|Druhý argument funkce dokumentu sady uzlů je prázdný a je relativní odkaz na identifikátor URI|Obnovit|Errata e14|

Částem chyby lze nalézt v W3C [transformace XSL (XSLT) verze 1.0 Specifikace chyby](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).

## <a name="custom-defined-implementation-behaviors"></a>Chování definované vlastní implementace

Jsou jedinečné pro chování <xref:System.Xml.Xsl.XslTransform> implementace třídy. Tato část popisuje implementaci specifickým pro zprostředkovatele `xsl:sort` a volitelné funkce, které jsou podporovány <xref:System.Xml.Xsl.XslTransform> třídy.

## <a name="xslsort"></a>sort

Při použití transformace na řazení, doporučení W3C XSLT 1.0 díky některé pozorování. Možnosti jsou následující:

- Dva XSLT procesory mohou být odpovídající procesory, ale stále může řadit odlišně.

- Ne všechny XSLT procesory podporují stejné jazyky.

- S ohledem na jazyce, se může lišit různých procesorů na jejich řazení není určena pro konkrétní jazyk `xsl:sort.`

V následující tabulce jsou uvedeny chování řazení implementována pro jednotlivé datové typy v rozhraní .NET Framework provádění transformace pomocí <xref:System.Xml.Xsl.XslTransform>:

|Datový typ|Chování řazení|
|---------------|----------------------|
|Text|Seřazena data pomocí common language runtime (CLR) String.Compare – metoda a jazykové verze národního prostředí. Pokud datový typ je rovno "text", řazení v <xref:System.Xml.Xsl.XslTransform> třídy se chová stejně jako chování porovnání řetězců modulu CLR.|
|Číslo|Číselné hodnoty jsou považovány za čísla jazyk XML Path (XPath) a jsou seřazeny podle podrobnosti uvedené v W3C [jazyk XML Path (XPath) verze 1.0 doporučení, část 3.5](https://www.w3.org/TR/1999/REC-xpath-19991116/#numbers).|

## <a name="optional-features-supported"></a>Volitelné funkce podporované

V následující tabulce jsou uvedeny funkce, které jsou volitelné pro procesor XSLT k implementaci a jsou implementovány v <xref:System.Xml.Xsl.XslTransform> třídy.

|Funkce|Odkaz na umístění|Poznámky|
|-------------|------------------------|-----------|
|`disable-output-escaping` atribut na `<xsl:text...>` a `<xsl:value-of...>` značky.|W3C XSLT 1.0 doporučení,<br /><br /> Část 16.4|`disable-output-escaping` Atribut se ignoruje při `xsl:text` nebo `xsl:value-of` elementy se používají v `xsl:comment`, `xsl:processing-instruction`, nebo `xsl:attribute` elementu.<br /><br /> Výsledků fragmenty, které obsahují text a textový výstup, který byl uvozeny řídicími znaky se nepodporují.<br /><br /> Atribut uvozovací znaky zakázat výstup se ignoruje při transformování do <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> objektu.|

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XslTransform>
- [Třída XslTransform implementuje procesor XSLT](xsltransform-class-implements-the-xslt-processor.md)
- [Transformace XSLT s třídou XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [XPathNavigator v transformacích](xpathnavigator-in-transformations.md)
- [XPathNodeIterator v transformacích](xpathnodeiterator-in-transformations.md)
- [Vstup XPathDocument do XslTransform](xpathdocument-input-to-xsltransform.md)
- [Vstup XmlDataDocument do XslTransform](xmldatadocument-input-to-xsltransform.md)
- [Vstup XmlDocument do XslTransform](xmldocument-input-to-xsltransform.md)
