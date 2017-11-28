---
title: model DOM (Document Object Model) dokumentu XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ff91e929876ceec8512e962b88795b6a8a29f3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-document-object-model-dom"></a>model DOM (Document Object Model) dokumentu XML
Třída XML modelu DOM (Document Object) je reprezentaci v paměti dokumentu XML. Modelu DOM umožňuje prostřednictvím kódu programu pro čtení, manipulaci a upravovat dokument XML. **XmlReader** XML přečte třída; však poskytuje přístup bez mezipaměti, dopředné, jen pro čtení. To znamená, že neexistují žádné možnosti, chcete-li upravit hodnoty atributu nebo obsah elementu nebo možnost Vložit a odebrání uzlů s **XmlReader**. Úpravy je primární funkce modelu DOM. Je běžné a způsobem strukturovaných, že XML data je reprezentována v paměti, i když skutečná data XML je lineárně uložené v souboru nebo brzo z jiného objektu. Následuje XML data.  
  
## <a name="input"></a>Vstup  
  
```xml  
<?xml version="1.0"?>  
  <books>  
    <book>  
        <author>Carson</author>  
        <price format="dollar">31.95</price>  
        <pubdate>05/01/2001</pubdate>  
    </book>  
    <pubinfo>  
        <publisher>MSPress</publisher>  
        <state>WA</state>  
    </pubinfo>  
  </books>   
```  
  
 Následující obrázek znázorňuje struktury paměti při tato data XML je pro čtení do struktury DOM.  
  
 ![Struktura dokumentu XML](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")  
Struktura dokumentu XML  
  
 V rámci strukturu dokumentu XML každý kruh na tomto obrázku představuje uzel, který se nazývá **XmlNode** objektu. **XmlNode** objektu je základní objekt ve stromové struktuře DOM. **Třídou XMLDocument nastavenou na** třídy, která rozšiřuje **XmlNode**, podporuje metody pro provádění operací na dokumentu jako celku (například načtení do paměti nebo ukládání do souboru XML. Kromě toho **třídou XMLDocument nastavenou na** poskytuje prostředky ke zobrazit a pracovat s uzly v celém dokumentu XML. Obě **XmlNode** a **třídou XMLDocument nastavenou na** vylepšení výkonu a použitelnost a metody a vlastnosti, které chcete:  
  
-   Přístup a upravte uzly, které jsou specifické pro DOM, jako je například uzly elementu, uzly odkaz na entitu a tak dále.  
  
-   Načtěte celý uzly, kromě informace, které obsahuje uzel, například textu v uzlu elementu.  
  
    > [!NOTE]
    >  Pokud aplikace nevyžaduje strukturu nebo úpravy funkce poskytované verzí DOM, **XmlReader** a **XmlWriter** třídy poskytovat přístup bez mezipaměti, dopředné datový proud XML. Další informace naleznete v tématu <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>.  
  
 **Uzel** objekty mají sadu metod a vlastností, jakož i základní a dobře definované vlastnosti. Některé z těchto vlastností jsou:  
  
-   Uzly mají jeden nadřazený uzel, nadřazený uzel se uzel přímo nad nimi. Pouze uzly, které nemají žádný nadřazený je kořen dokumentu, jako je uzel na nejvyšší úrovni a obsahuje dokument a fragmenty dokumentu.  
  
-   Většina uzlů může mít více podřízených uzlů, které jsou uzly přímo uvedenou pod nimi. Následuje seznam typů uzlů, které může mít podřízené uzly.  
  
    -   **Dokument**  
  
    -   **DocumentFragment**  
  
    -   **Třída EntityReference**  
  
    -   **Element**  
  
    -   **Atribut**  
  
     **XmlDeclaration**, **zápis**, **Entity**, **CDATASection**, **Text**,  **Komentář**, **ProcessingInstruction**, a **DocumentType** uzly nemají podřízené uzly.  
  
-   Uzly, které jsou na stejné úrovni, znázorněná na obrázku pomocí **kniha** a **pubinfo** uzly, jsou na stejné úrovni.  
  
 Jeden znakem modelu DOM je, jak zpracovává atributy. Atributy nejsou uzly, které jsou součástí nadřazené, podřízené a vztahy na stejné úrovni. Atributy jsou považovány za vlastnost uzlu elementu a jsou tvořeny název a hodnotu pár. Například, pokud máte data XML, který se skládá z `format="dollar`"přidružené element `price`, slovo `format` je název a hodnotu `format` atribut je `dollar`. Načíst `format="dollar"` atribut **cena** uzlu zavoláte **GetAttribute** metoda při kurzor se nachází v `price` element uzlu. Další informace najdete v tématu [přístup k atributům v modelu DOM](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).  
  
 XML je pro čtení do paměti, že uzly jsou vytvořeny. Ne všechny uzly jsou však stejného typu. Element v XML obsahuje různá pravidla a syntaxe než instrukce pro zpracování. Proto různých dat je pro čtení, je typ uzlu přiřazen do každého uzlu. Tento typ uzlu určuje vlastnosti a funkce uzlu.  
  
 Další informace o typech uzly vygenerované v paměti najdete v tématu [typy uzlů XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md). Další informace o objekty vytvořené v uzlu stromu najdete v tématu [mapování hierarchie objektů na XML Data](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
 Microsoft má rozšířené rozhraní API, které jsou k dispozici v World Wide Web Consortium (W3C) DOM úroveň 1 a Level 2, aby bylo snazší pro práci s dokument XML. Zároveň plně podporuje standardy W3C, přidejte další tříd, metod a vlastností funkce nad co můžete udělat pomocí modelu DOM. W3C XML Nové třídy umožňují přístup k relační data, která poskytuje metody pro synchronizaci s dat ADO.NET, současně úniku dat ve formátu XML. Další informace najdete v tématu [synchronizace datovou sadu s XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
 Modelu DOM je nejvhodnější pro načítání dat XML do paměti k změnit její strukturu, přidávat nebo odebírat uzly nebo změnit data ukládaná společností uzlu jako text obsažený v elementu. Ale jsou k dispozici jiné třídy, které jsou rychlejší než DOM v jiných scénářích. Pro datový proud rychlá bez mezipaměti, dopředné přístup k XML, použijte **XmlReader** a **XmlWriter**. Pokud potřebujete náhodný přístup s modelem kurzor a **XPath**, použijte **objektem XPathNavigator nastaveným** třídy.  
  
## <a name="see-also"></a>Viz také  
 [Typy uzlů XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
 [Mapování hierarchie objektů na XML Data](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
