---
title: "Chyby obnovitelné XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 78149e0e1c84a457f68b67ea8fe4c82098e794ad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="recoverable-xslt-errors"></a>Chyby obnovitelné XSLT
Doporučení W3C XSL transformace XSLT () verze 1.0 zahrnuje oblasti, ve kterých může implementaci zprostředkovatele rozhodování o způsobu zpracování situaci. Tyto oblasti jsou považovány za volitelné chování. Například části 7.3 vytváření zpracování pokynů, XSLT 1.0 doporučení stavy, jedná se o chybu, pokud vytváření instancí obsah `xsl:processing-instruction` vytvoří uzly kromě textové uzly. Některé problémy je třeba 1.0 XSLT doporučení označuje, co decision provést pokud procesor rozhodne zotavit z chyby. Pro problém uveden v části 7.3 W3C říká, že můžete implementace obnovit z této chyby, bez ohledu na uzlech a jejich obsah.  
  
## <a name="discretionary-behaviors"></a>Volitelné chování  
 Následující tabulka obsahuje seznam všech volitelné chování povolen na základě doporučení XSLT 1.0 a jak jsou zpracovávány těchto projevů <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
-   Obnovit znamená, že <xref:System.Xml.Xsl.XslCompiledTransform> třída obnoví z této chyby. <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=nameWithType> Událostí lze použít k hlášení všechny události z procesoru XSLT.  
  
-   Chyba označuje, že je pro tuto podmínku vyvolána výjimka.  
  
-   Odkazy na části lze nalézt v [W3C XSL transformace XSLT () verze 1.0 doporučení](http://go.microsoft.com/fwlink/?LinkId=49919) a [W3C XSL transformace XSLT () verze 1.0 specifikace chybující](http://go.microsoft.com/fwlink/?LinkId=49917).  
  
|Podmínka XSLT|Část|Chování XslCompiledTransform|  
|--------------------|-------------|-----------------------------------|  
|Textový uzel odpovídá obě `xsl:strip-space` a `xsl:preserve-space`.|3.4|Obnovení|  
|Zdrojový uzel odpovídá více než jedno pravidlo šablony.|5.5|Obnovení|  
|Obor názvů URI je deklarován jako alias pro více identifikátorů URI oboru názvů, všechny mají stejnou prioritu importu.|7.1.1|Obnovení|  
|`name` Atribut `xsl:attribute` a `xsl:element` vygenerovat z hodnota atributu QName není.|7.1.2, 7.1.3|Chyba *|  
|Dva atribut sady s stejného importu a rozšířit název mají atribut společné a neexistuje žádný další sadu atributů obsahující společný atribut, který má stejný název s vyšší důležitostí.|7.1.4|Obnovení|  
|Přidání atributu do element po podřízené objekty přidané do ní.|7.1.3|Chyba *|  
|Vytváření atribut s názvem 'xmlns'|7.1.3|Chyba *|  
|Přidání atributu do uzlu, který není element.|7.1.3|Chyba *|  
|Vytváření uzly kromě textové uzly při konkretizaci část obsahu `xsl:attribute` atribut.|7.1.3|Chyba *|  
|`name` Atribut `xsl:processing-instruction` nepřinese atributem NCName a cíl instrukcí pro zpracování.|7.3|Chyba *|  
|Vytváření instancí obsah `xsl:processing-instruction` vytvoří uzly kromě textové uzly.|7.3|Chyba *|  
|Výsledek vytvoření instance obsah `xsl:processing-instruction` obsahuje řetězec "? >"|7.3|Obnovení|  
|Výsledek vytvoření instance obsah `xsl:processing-instruction` obsahuje řetězec "–" nebo končí "-".|7.4|Obnovení|  
|Výsledek vytvoření instance obsah `xsl:comment` vytvoří uzly kromě textové uzly.|7.4|Chyba *|  
|Šablony v rámci elementu vazby proměnné vrátí do atribut uzlu nebo uzlu oboru názvů.|11.2|Chyba *|  
|Dojde k chybě při načítání prostředku z identifikátoru URI předána do funkce dokumentu.|12.1|Chyba|  
|Odkaz na URI ve funkci dokument obsahuje identifikátor fragmentu a dojde k chybě při zpracování identifikátor fragmentu.|12.1|Obnovit *|  
|Existuje více atributů se stejným názvem, ale různé hodnoty, které nejsou s názvem elementů oddílu cdata v `xsl:output` se stejným importovat prioritu.|16|Obnovení|  
|Procesor nepodporuje kódování v `xsl:output` kódování atributu.|16.1|Obnovení|  
|Zakazuje se výstup uvození pro textový uzel, který se používá pro něco jiného než textový uzel ve stromové struktuře výsledek.|16.4|Obnovit *|  
|Fragment stromu výsledek převodu na číslo nebo řetězec, pokud fragment stromu výsledek obsahuje textový uzel se výstup uvozovací znaky povolit.|16.4|Obnovit *|  
|Výstup uvozovací znaky je zakázán pro znak, který není možné vyjádřit v kódování, procesor XSLT používá pro výstup.|16.4|Obnovit *|  
|Přidání uzlu do oboru názvů pro element po podřízené objekty byly přidány k němu nebo po atributy přidané do ní.|Chybující 25|Chyba *|  
|`value` Atribut `xsl:number` je NAN nekonečné nebo menší než 0,5|Chybující 24|Obnovení|  
|Druhý argument funkce dokumentu sada uzlů je prázdný a je relativní identifikátor URI odkazu.|Chybující 14|Obnovení|  
  
 <sup>*</sup>Toto chování se liší od <xref:System.Xml.Xsl.XslTransform> třídy. Další informace najdete v tématu [implementace volitelné chování ve třídě XslTransform](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md).  
  
## <a name="see-also"></a>Viz také  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
