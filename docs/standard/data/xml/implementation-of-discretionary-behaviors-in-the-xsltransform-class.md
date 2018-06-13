---
title: Implementace volitelné chování ve třídě XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c2ffa755c642b2a3c7dd47d7007bff7239f500f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577069"
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>Implementace volitelné chování ve třídě XslTransform
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy. V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.  
  
 Volitelné chování jsou popsány chování uvedené v World Wide Web Consortium (W3C) XSL transformace XSLT () verze 1.0 doporučení (www.w3.org/TR/xslt), ve kterém implementace poskytovatele zvolí jeden z několika způsobů jako způsob pro zpracování situaci. Například části 7.3 vytváření zpracování pokynů, doporučení W3C říká, jedná se o chybu, pokud vytváření instancí obsah `xsl:processing-instruction` vytvoří uzly kromě textové uzly. Pro některé problémy W3C informuje je třeba rozhodnutí, jaké pokud procesor rozhodne zotavit z chyby. Pro problém uveden v části 7.3 W3C říká, že můžete implementace obnovit z této chyby, bez ohledu na uzlech a jejich obsah.  
  
 Následující tabulka uvádí proto pro každou z volitelné chování povolenou W3C, volitelné chování implementována pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementace <xref:System.Xml.Xsl.XslTransform> třídy a co kapitoly doporučení W3C XSLT 1.0 které tento problém je popsané.  
  
|Problém|Chování|Část|  
|-------------|--------------|-------------|  
|Textový uzel odpovídá obě `xsl:strip-space` a `xsl:preserve-space`.|Obnovení|3.4|  
|Zdrojový uzel odpovídá více než jedno pravidlo šablony.|Obnovení|5.5|  
|Obor názvů identifikátor URI (Uniform Resource) je deklarován jako alias pro více identifikátorů URI oboru názvů, všechny mají stejnou prioritu importu.|Obnovení|7.1.1|  
|Atribut názvu v `xsl:attribute` a `xsl:element` vygenerovat z šabloně hodnoty atributu není platný úplný název (QName).|Došlo k výjimce|7.1.2 a 7.1.3|  
|Přidání atributu do elementu po podřízené uzly již byly přidány do uzlu elementu.|Obnovení|7.1.3|  
|Přidání atributu do jakoukoli jinou hodnotu než uzlu elementu.|Obnovení|7.1.3|  
|Vytváření instancí část obsahu `xsl:attribute` element není textový uzel.|Obnovení|7.1.3|  
|Dvě sady atributů mají stejnou prioritu importu a rozšířená název. Mají stejný atribut a neexistuje žádný jiný atribut nastavit s vyšší důležitostí obsahující společný atribut se stejným názvem.|Obnovení|7.1.4|  
|`xsl:processing-instruction` atribut Name nepřinese ne dvojtečkou název (NCName) a cíl zpracování instrukcí.|Obnovení|7.3|  
|Vytváření instancí obsah `xsl:processing-instruction` vytvoří uzly kromě textové uzly.|Obnovení|7.3|  
|Výsledky vytváření instancí obsah `xsl:processing-instruction` obsahuje řetězec "`?>`".|Obnovení|7.3|  
|Výsledky vytváření instancí obsah `xsl:comment` obsahuje řetězec "–", nebo končí "-".|Obnovení|7.4|  
|Výsledky vytváření instancí obsah `xsl:comment` vytvoří uzly kromě textové uzly.|Obnovení|7.4|  
|Šablony v rámci elementu vazby proměnné vrátí do atribut uzlu nebo uzlu oboru názvů.|Obnovení|11.2|  
|Dojde k chybě při načítání prostředku z identifikátoru URI předána do funkce dokumentu.|Došlo k výjimce|12.1|  
|Odkaz na URI ve funkci dokument obsahuje identifikátor fragmentu a dojde k chybě při zpracování identifikátor fragmentu.|Došlo k výjimce|12.1|  
|Existuje více atributů se stejným názvem, které nejsou s názvem `cdata-section-elements` v `xls:output`, a tyto atributy mají stejnou prioritu importu.|Obnovení|16|  
|Procesor nepodporuje hodnotu uvedenou v kódování znaků `encoding` atribut `xsl:output` elementu.|Obnovení|16.1|  
|`disable-output-escaping` se používá pro textový uzel, a že textový uzel se používá k vytvoření něco jiného než textový uzel ve stromové struktuře výsledek.|`disable-output-escaping` atribut je ignorován|16.4|  
|Fragment stromu výsledek převodu na číslo nebo řetězec, pokud fragment stromu výsledek obsahuje textový uzel se výstup uvozovací znaky povolit.|Ignorováno|16.4|  
|Výstup uvozovací znaky je zakázán pro znaky, které nelze vyjádřit v kódování, procesor XSLT používá pro výstup.|Ignorováno|16.4|  
|Přidání uzlu do oboru názvů pro element po podřízené objekty byly přidány k němu nebo po atributy přidané do ní|Obnovení|Chybující e25|  
|`xsl:number` je NaN nekonečné nebo menší než 0,5.|Obnovení|Chybující e 24|  
|Druhý argument funkce dokumentu sada uzlů je prázdný a je relativní identifikátor URI odkazu|Obnovení|Chybující typu e14.|  
  
 Oddíly z chyby najdete v World Wide Web Consortium (W3C) XSL transformace XSLT () verze 1.0 specifikace chybující, nacházející se v www.w3.org/1999/11/REC-xslt-19991116-errata.  
  
## <a name="custom-defined-implementation-behaviors"></a>Chování definované vlastní implementace  
 Jsou jedinečné pro chování <xref:System.Xml.Xsl.XslTransform> implementaci třídy. Tato část popisuje implementace specifický pro zprostředkovatele `xsl:sort` a volitelné funkce, které jsou podporovány <xref:System.Xml.Xsl.XslTransform> třídy.  
  
## <a name="xslsort"></a>sort  
 Při použití transformace seřadit, díky doporučení W3C XSLT 1.0 některé připomínky. Možnosti jsou následující:  
  
-   Dva procesory XSLT může být vyhovující procesory, ale stále může seřadit jinak.  
  
-   Ne všechny procesory XSLT podporují stejné jazyky.  
  
-   S ohledem na jazyce, se mohou lišit různé procesory na jejich řazení pro konkrétní jazyk není zadaný na `xsl:sort.`  
  
 Následující tabulka uvádí chování implementována pro každý typ dat v rozhraní .NET Framework implementace transformace pomocí <xref:System.Xml.Xsl.XslTransform>.  
  
|Datový typ|Chování řazení|  
|---------------|----------------------|  
|Text|Data jsou seřazená pomocí common language runtime (CLR) String.Compare – metoda a kulturního národní prostředí. Pokud datový typ je rovno "text", řazení v <xref:System.Xml.Xsl.XslTransform> třídy se chová stejně chování porovnání řetězce modulu CLR.|  
|Číslo|Číselné hodnoty jsou považovány za čísla XML Path Language (XPath) a jsou seřazeny podle podrobnosti uvedené v doporučení W3C XML Path Language (XPath) verze 1.0, část 3.5 (www.w3.org/TR/xpath.html#numbers).|  
  
## <a name="optional-features-supported"></a>Volitelné funkce podporované  
 Následující tabulka uvádí funkce, které jsou volitelné pro procesor XSLT k implementaci a jsou implementované v <xref:System.Xml.Xsl.XslTransform> třídy.  
  
|Funkce|Odkaz na umístění|Poznámky|  
|-------------|------------------------|-----------|  
|`disable-output-escaping` atribut na `<xsl:text...>` a `<xsl:value-of...>` značky.|W3C XSLT 1.0 doporučení,<br /><br /> Část 16.4|`disable-output-escaping` Atribut je ignorován při `xsl:text` nebo `xsl:value-of` elementy používají `xsl:comment`, `xsl:processing-instruction`, nebo `xsl:attribute` element.<br /><br /> Výsledek fragmenty stromu, které obsahují text a výstup textu, který má řídicí sekvencí nejsou podporovány.<br /><br /> Atribut uvozovací znaky zakázat výstup se ignoruje, pokud transformace na <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> objektu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Xsl.XslTransform>  
 [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Transformace XSLT s třídou XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XPathNavigator v transformacích](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator v transformacích](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Vstup XPathDocument do XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Vstup XmlDataDocument do XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Vstup XmlDocument do XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
