---
title: Chyby XSLT s možností zotavení
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f7630b9a233db009b6095abc8d833870c1f33d8
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991284"
---
# <a name="recoverable-xslt-errors"></a>Chyby XSLT s možností zotavení
Verze 1.0 doporučení W3C transformace XSL (XSLT) zahrnuje oblasti, ve kterých může implementaci zprostředkovatele rozhodování o způsobu zpracování situaci. Tyto oblasti jsou považovány za volitelného chování. Například část 7.3 vytváření zpracování pokyny, XSLT 1.0 doporučení státy, jedná se o chybu, pokud vytvoření instance obsah `xsl:processing-instruction` vytvoří uzly než textové uzly. Pro některé problémy XSLT 1.0 doporučení indikuje, co rozhodnutí třeba pokud se rozhodne procesoru zotavit z chyby. Na problém uvedený v části 7.3 W3C říká, že implementace můžete obnovit tuto chybu ignorovat uzly a jejich obsah.  
  
## <a name="discretionary-behaviors"></a>Volitelného chování  
 Následující tabulka obsahuje seznam všech volitelného chování dovolují XSLT 1.0 doporučení a jak jsou zpracovávány těchto projevů <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
-   Obnovit znamená, že <xref:System.Xml.Xsl.XslCompiledTransform> třídy bude obnoven. k této chybě. <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=nameWithType> Události je možné nahlásit všechny události z procesoru XSLT.  
  
-   Chyba udává, že je vyvolána výjimka pro tuto podmínku.  
  
-   Najdete v části odkazy [doporučení W3C transformace XSL (XSLT) verze 1.0](http://www.w3.org/TR/xslt) a [chyby specifikaci W3C transformace XSL (XSLT) verze 1.0](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).  
  
|Podmínka XSLT|Oddíl|Chování XslCompiledTransform|  
|--------------------|-------------|-----------------------------------|  
|Textový uzel odpovídá obě `xsl:strip-space` a `xsl:preserve-space`.|3.4|Obnovit|  
|Zdrojový uzel odpovídá více než jedno pravidlo šablony.|5.5|Obnovit|  
|Obor názvů identifikátoru URI je deklarován jako alias pro více identifikátorů URI oboru názvů, všechny mají stejnou přednost importovat.|7.1.1|Obnovit|  
|`name` Atribut `xsl:attribute` a `xsl:element` vygenerovaná hodnota atributu není QName.|7.1.2, 7.1.3|Chyba *|  
|Dvě atribut sady stejné importu a rozšířit – název atributu mají společnou a neexistuje žádné další sadu atributů obsahující společný atribut, který má stejný název s vyšší význam.|7.1.4|Obnovit|  
|Přidání atributu do elementu po podřízené objekty byly přidány do něj.|7.1.3|Chyba *|  
|Vytváří se atribut s názvem 'xmlns'|7.1.3|Chyba *|  
|Přidání atributu do uzlu, který není element.|7.1.3|Chyba *|  
|Vytvoření uzlů než textovém uzlů během vytvoření instance obsah `xsl:attribute` atribut.|7.1.3|Chyba *|  
|`name` Atribut `xsl:processing-instruction` nevydává NCName a cíl instrukcí pro zpracování.|7.3|Chyba *|  
|Vytvoření instance obsah `xsl:processing-instruction` vytvoří uzly než textové uzly.|7.3|Chyba *|  
|Výsledek vytvoření instance obsah `xsl:processing-instruction` obsahuje řetězec "? >"|7.3|Obnovit|  
|Výsledek vytvoření instance obsah `xsl:processing-instruction` obsahuje řetězec "--" nebo končí řetězcem "-".|7.4|Obnovit|  
|Výsledek vytvoření instance obsah `xsl:comment` vytvoří uzly než textové uzly.|7.4|Chyba *|  
|Šablony v rámci elementu vazby proměnné vrátí uzel atributu nebo uzel oboru názvů.|11.2|Chyba *|  
|Je chyba při načítání prostředku z identifikátoru URI předaného do funkce dokumentu.|12.1|Chyba|  
|Odkaz na identifikátor URI ve funkci dokumentu obsahuje identifikátor fragmentu a dojde k chybě při zpracování identifikátor fragmentu.|12.1|Obnovit *|  
|Existuje víc atributů se stejným názvem, ale jinými hodnotami, které nejsou s názvem oddílu cdata prvky v `xsl:output` se stejným importu přednost.|16|Obnovit|  
|Procesor nepodporuje kódování v `xsl:output` kódování atributu.|16.1|Obnovit|  
|Zakazuje se výstup uvození pro textový uzel, který se používá pro něco jiného než textový uzel ve stromu výsledek.|16.4|Obnovit *|  
|Převod fragment stromu výsledek na číslo nebo řetězec. Pokud fragment stromu výsledek obsahuje textový uzel se výstup uvození povolena.|16.4|Obnovit *|  
|Výstup uvozovacích znaků je zakázaná pro znak, který nemůže být reprezentovaný v kódování, procesoru XSLT se používá pro výstup.|16.4|Obnovit *|  
|Přidání uzlu oboru názvů na prvek po podřízené objekty byly přidány do ní nebo po atributy byly přidány do něj.|chyby 25|Chyba *|  
|`value` Atribut `xsl:number` NaN, nekonečné nebo menší než 0,5|chyby 24|Obnovit|  
|Druhý argument funkce dokumentu sady uzlů je prázdný a odkaz na identifikátor URI je relativní.|chyby 14|Obnovit|  
  
 <sup>*</sup> Toto chování se liší od <xref:System.Xml.Xsl.XslTransform> třídy. Další informace najdete v tématu [implementace volitelného chování ve třídě XslTransform](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md).  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
