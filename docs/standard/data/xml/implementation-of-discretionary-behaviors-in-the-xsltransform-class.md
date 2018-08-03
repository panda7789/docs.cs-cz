---
title: Implementace volitelného chování ve třídě XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c2ffa755c642b2a3c7dd47d7007bff7239f500f
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "33577069"
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>Implementace volitelného chování ve třídě XslTransform
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Volitelného chování jsou popsané, jak je uvedeno chování v transformace XSL (XSLT) verze World Wide Web Consortium (W3C) 1.0 doporučení (www.w3.org/TR/xslt), ve kterém implementace zprostředkovatele vybere jeden z několika dostupných možností jako způsob pro zpracování situaci. Například část 7.3 vytváření zpracování pokyny, doporučení W3C říká, jedná se o chybu, pokud vytvoření instance obsah `xsl:processing-instruction` vytvoří uzly než textové uzly. Pro některé problémy W3C říká je třeba jaká rozhodnutí pokud procesor rozhodne zotavit z chyby. Na problém uvedený v části 7.3 W3C říká, že implementace můžete obnovit tuto chybu ignorovat uzly a jejich obsah.  
  
 Proto pro každou z volitelného chování dovolují W3C, následující tabulka uvádí volitelného chování pro implementované [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provádění <xref:System.Xml.Xsl.XslTransform> třídy a jaké části v doporučení W3C XSLT 1.0, že tento problém je popsáno.  
  
|Problém|Chování|Oddíl|  
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
|`xsl:number` je NaN, nekonečné nebo menší než 0,5.|Obnovit|Chyby e 24|  
|Druhý argument funkce dokumentu sady uzlů je prázdný a je relativní odkaz na identifikátor URI|Obnovit|Chyby typu e14.|  
  
 World Wide Web Consortium (W3C) transformace XSL (XSLT) verze 1.0 Specifikace chyby, umístěný ve www.w3.org/1999/11/REC-xslt-19991116-errata najdete částem chyby.  
  
## <a name="custom-defined-implementation-behaviors"></a>Chování definované vlastní implementace  
 Jsou jedinečné pro chování <xref:System.Xml.Xsl.XslTransform> implementace třídy. Tato část popisuje implementaci specifickým pro zprostředkovatele `xsl:sort` a volitelné funkce, které jsou podporovány <xref:System.Xml.Xsl.XslTransform> třídy.  
  
## <a name="xslsort"></a>sort  
 Při použití transformace na řazení, doporučení W3C XSLT 1.0 díky některé pozorování. Možnosti jsou následující:  
  
-   Dva XSLT procesory mohou být odpovídající procesory, ale stále může řadit odlišně.  
  
-   Ne všechny XSLT procesory podporují stejné jazyky.  
  
-   S ohledem na jazyce, se může lišit různých procesorů na jejich řazení není určena pro konkrétní jazyk `xsl:sort.`  
  
 V následující tabulce jsou uvedeny chování řazení implementována pro jednotlivé datové typy v rozhraní .NET Framework provádění transformace pomocí <xref:System.Xml.Xsl.XslTransform>.  
  
|Datový typ|Chování řazení|  
|---------------|----------------------|  
|Text|Seřazena data pomocí common language runtime (CLR) String.Compare – metoda a jazykové verze národního prostředí. Pokud datový typ je rovno "text", řazení v <xref:System.Xml.Xsl.XslTransform> třídy se chová stejně jako chování porovnání řetězců modulu CLR.|  
|Číslo|Číselné hodnoty jsou považovány za čísla jazyk XML Path (XPath) a jsou seřazeny podle podrobnosti uvedené v doporučení W3C jazyk XML Path (XPath) verze 1.0, část 3.5 (www.w3.org/TR/xpath.html#numbers).|  
  
## <a name="optional-features-supported"></a>Volitelné funkce podporované  
 V následující tabulce jsou uvedeny funkce, které jsou volitelné pro procesor XSLT k implementaci a jsou implementovány v <xref:System.Xml.Xsl.XslTransform> třídy.  
  
|Funkce|Odkaz na umístění|Poznámky|  
|-------------|------------------------|-----------|  
|`disable-output-escaping` atribut na `<xsl:text...>` a `<xsl:value-of...>` značky.|W3C XSLT 1.0 doporučení,<br /><br /> Část 16.4|`disable-output-escaping` Atribut se ignoruje při `xsl:text` nebo `xsl:value-of` elementy se používají v `xsl:comment`, `xsl:processing-instruction`, nebo `xsl:attribute` elementu.<br /><br /> Výsledků fragmenty, které obsahují text a textový výstup, který byl uvozeny řídicími znaky se nepodporují.<br /><br /> Atribut uvozovací znaky zakázat výstup se ignoruje při transformování do <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> objektu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Xsl.XslTransform>  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
