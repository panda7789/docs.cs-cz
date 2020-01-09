---
title: Chyby XSLT s možností zotavení
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
ms.openlocfilehash: e3ff86cc80887d14fdffe50f256409cb70ff2d88
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710372"
---
# <a name="recoverable-xslt-errors"></a>Chyby XSLT s možností zotavení
Doporučení W3C XSL Transformers (XSLT) verze 1,0 obsahuje oblasti, ve kterých se může poskytovatel implementace rozhodnout, jak tuto situaci zpracovat. Tyto oblasti se považují za volitelné chování. Například v části 7,3 vytvoření instrukcí pro zpracování, v případě, že se při vytváření instance obsahu `xsl:processing-instruction` vytvoří jiné uzly než textové uzly, doporučení XSLT 1,0 uvádí, že se jedná o chybu. V případě některých problémů doporučení XSLT 1,0 určuje, jaké rozhodnutí by mělo být provedeno, pokud se procesor rozhodne obnovit z chyby. V případě problému uvedeného v části 7,3 oznámí W3C, že implementace se může zotavit z této chyby ignorováním uzlů a jejich obsahu.  
  
## <a name="discretionary-behaviors"></a>Volitelné chování  
 V následující tabulce jsou uvedeny všechny volitelné chování, které povoluje doporučení XSLT 1,0, a způsob, jakým jsou tato chování zpracována třídou <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
- Obnovení indikuje, že se z této chyby bude obnovovat třída <xref:System.Xml.Xsl.XslCompiledTransform>. Událost <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=nameWithType> lze použít k hlášení událostí z procesoru XSLT.  
  
- Chyba indikuje, že pro tuto podmínku je vyvolána výjimka.  
  
- Odkazy na oddíly najdete v [doporučení XSLT verze 1,0](https://www.w3.org/TR/xslt) a XSL [XSLT (w3c) verze 1,0 Specification seznam chyb](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).  
  
|Podmínka XSLT|Část|Chování XslCompiledTransform|  
|--------------------|-------------|-----------------------------------|  
|Textový uzel odpovídá `xsl:strip-space` i `xsl:preserve-space`.|3.4|Obnovit|  
|Zdrojový uzel se shoduje s více než jedním pravidlem šablony.|5.5|Obnovit|  
|Identifikátor URI oboru názvů je deklarován jako alias pro více identifikátorů URI oboru názvů, přičemž všechny mají stejnou prioritu importu.|7.1.1|Obnovit|  
|Atribut `name` v `xsl:attribute` a `xsl:element` vygenerovaný z hodnoty atributu není QName.|7.1.2, 7.1.3|Chyba|  
|Dvě sady atributů se stejným importem a rozšířeným názvem mají atribut společný a neexistuje žádná sada atributů obsahující společný atribut se stejným názvem s vyšší důležitostí.|7.1.4|Obnovit|  
|Přidání atributu do elementu po přidání podřízených objektů do objektu.|7.1.3|Chyba|  
|Vytváření atributu s názvem xmlns|7.1.3|Chyba|  
|Přidání atributu do uzlu, který není elementem.|7.1.3|Chyba|  
|Vytváření jiných uzlů než textových uzlů během vytváření instancí obsahu atributu `xsl:attribute`.|7.1.3|Chyba|  
|Atribut `name` `xsl:processing-instruction` nepřinese NCName i cíl instrukcí pro zpracování.|7.3|Chyba|  
|Vytvoření instance obsahu `xsl:processing-instruction` vytvoří jiné uzly než textové uzly.|7.3|Chyba|  
|Výsledek vytvoření instance obsahu `xsl:processing-instruction` obsahuje řetězec "? >"|7.3|Obnovit|  
|Výsledek vytvoření instance obsahu `xsl:processing-instruction` obsahuje řetězec "--" nebo končí "-".|7,4|Obnovit|  
|Výsledek vytvoření instance obsahu `xsl:comment` vytvoří jiné uzly než textové uzly.|7,4|Chyba|  
|Šablona v rámci prvku variabilní vazby vrací uzel atributu nebo uzel oboru názvů.|11.2|Chyba|  
|Došlo k chybě při načítání prostředku z identifikátoru URI předaného do funkce dokumentu.|12.1|Chyba|  
|Odkaz na identifikátor URI ve funkci dokumentu obsahuje identifikátor fragmentu a při zpracování identifikátoru fragmentu došlo k chybě.|12.1|Opravitelné|  
|Existuje více atributů se stejným názvem, ale různé hodnoty, které nejsou pojmenované prvky CDATA oddílu v `xsl:output` se stejnou prioritou importu.|16|Obnovit|  
|Procesor nepodporuje kódování v atributu `xsl:output` Encoding.|16.1|Obnovit|  
|Zakázání výstupních řídicích znaků pro textový uzel, který se používá pro něco jiného než textový uzel ve stromové struktuře výsledek.|16.4|Opravitelné|  
|Převod fragmentu stromu výsledků na číslo nebo řetězec, pokud fragment stromu výsledku obsahuje textový uzel s povoleným výstupním uvozovacím příkazem.|16.4|Opravitelné|  
|Výstupní uvozovací znaky jsou zakázané pro znak, který se nedá reprezentovat v kódování, které procesor XSLT používá pro výstup.|16.4|Opravitelné|  
|Přidání uzlu oboru názvů do elementu po přidání podřízených objektů nebo po jejich přidání do objektu Namespace.|Seznam chyb 25|Chyba|  
|Atribut `value` `xsl:number` je NAN, infinitá nebo menší než 0,5.|Seznam chyb 24|Obnovit|  
|Druhý argument node-nastaveno na funkci dokumentu je prázdný a odkaz na identifikátor URI je relativní.|Seznam chyb 14|Obnovit|  
  
 <sup>*</sup> Toto chování se liší od <xref:System.Xml.Xsl.XslTransform> třídy. Další informace naleznete v tématu [implementace volitelného chování ve třídě XslTransform](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md).  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
