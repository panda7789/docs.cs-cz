---
title: model DOM (Document Object Model) dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b3a2432deb1e956060ab3615db01821658f8782
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508676"
---
# <a name="xml-document-object-model-dom"></a>model DOM (Document Object Model) dokumentu XML
Třída XML Document Object Model (DOM) je v paměti reprezentace dokumentu XML. V modelu DOM můžete prostřednictvím kódu programu čtení, manipulaci a upravit dokument XML. **XmlReader** XML přečte třída; však poskytuje přístup bez mezipaměti, pouze vpřed, jen pro čtení. To znamená, že neexistují žádné možnosti upravit hodnoty atributu nebo obsahu elementu nebo možnost vkládat a odebrání uzlů s **XmlReader**. Pro úpravy je primární funkce modelu DOM. Je běžné a způsobem strukturovaná, že XML data reprezentované v paměti, ačkoli skutečná data XML je uložen v lineárně v souboru nebo přicházející z jiného objektu. Následuje XML data.  
  
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
  
 Následující obrázek znázorňuje, jak paměti strukturovaná přečtení tato data XML do modelu DOM struktury.  
  
 ![Strukturu dokumentu XML](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")  
Strukturu dokumentu XML  
  
 V rámci struktury dokumentu XML, každý kruhu na tomto obrázku představuje uzlu, která je volána **XmlNode** objektu. **XmlNode** objekt je základní objekt ve stromové struktuře modelu DOM. **XmlDocument** třídu, která rozšiřuje **XmlNode**, podporuje metody pro provádění operací na dokument jako celek (například načtení do paměti nebo uložení souboru XML do souboru. Kromě toho **XmlDocument** poskytuje prostředky k zobrazení a manipulaci s uzly v celém dokumentu XML. Obě **XmlNode** a **XmlDocument** mají vylepšení výkonu a použitelnosti a mají metody a vlastnosti pro:  
  
-   Přístup a úpravy uzlů, které jsou specifické pro modelu DOM, jako jsou uzly element, uzly odkaz na entitu a tak dále.  
  
-   Načte celý uzly kromě informace, které obsahuje uzel, například podle textu v uzlu elementu.  
  
    > [!NOTE]
    >  Pokud aplikace nevyžaduje, aby struktura nebo poskytované v modelu DOM, možností pro úpravy **XmlReader** a **XmlWriter** třídy poskytnout přístup bez mezipaměti, dopředné datový proud XML. Další informace naleznete v tématu <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>.  
  
 **Uzel** objekty mají sadu metod a vlastností, jakož i základní a jasně definované vlastnosti. Zde jsou některé z těchto vlastností:  
  
-   Uzly mít jeden nadřazený uzel, nadřazený uzel je uzel přímo nad nimi. Uzel nejvyšší úrovně a obsahuje samotný dokument a fragmentů dokumentu, je pouze uzly, které nemají nadřazené kořen dokumentu.  
  
-   Většina uzlů může mít více podřízených uzlů, které jsou uzly pod nimi. Následuje seznam typy uzlů, které mohou obsahovat podřízené uzly.  
  
    -   **Dokument**  
  
    -   **DocumentFragment**  
  
    -   **EntityReference**  
  
    -   **Element**  
  
    -   **Atribut**  
  
     **XmlDeclaration**, **Notation**, **Entity**, **CDATASection**, **Text**,  **Komentář**, **ProcessingInstruction**, a **DocumentType** uzly nemají podřízené uzly.  
  
-   Uzly, které jsou na stejné úrovni, v diagramu pomocí **knihy** a **pubinfo** uzly, jsou na stejné úrovni.  
  
 Jedna vlastnost v modelu DOM se způsob, jakým zpracovává atributy. Atributy nejsou uzly, které jsou součástí nadřazeného, podřízené a vztahy na stejné úrovni. Atributy jsou považovány za vlastnost uzlu elementu a se skládá z názvu a hodnoty pár. Například, pokud máte data XML, který se skládá z `format="dollar`"přidružené k tomuto prvku `price`, slovo `format` je název a hodnota `format` atribut je `dollar`. K načtení `format="dollar"` atribut **cena** uzlu, volání **GetAttribute** metodu, když je ukazatel myši nachází na `price` uzlu elementu. Další informace najdete v tématu [přístup k atributům v modelu DOM](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).  
  
 Protože XML je načíst do paměti, se vytvoří uzly. Ale ne všechny uzly jsou stejného typu. Element v XML má různá pravidla a syntaxe než instrukce pro zpracování. Proto jako je čtení různá data, typ uzlu je přiřazena k jednotlivým uzlům. Tento typ uzlu určuje vlastnosti a funkce uzlu.  
  
 Další informace o typech uzlů vygenerované v paměti, naleznete v tématu [typy uzlů XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md). Další informace o objekty vytvořené v uzlu stromu, naleznete v tématu [mapování hierarchie objektů na XML Data](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
 Microsoft rozšířil rozhraní API, která jsou k dispozici v World Wide Web Consortium (W3C) modelu DOM úrovně 1 a 2 úroveň usnadňují práci s dokumentu XML. Při plné podpoře standardů W3C, přidejte další třídy, metody a vlastnosti funkce nad rámec co se dá dělat pomocí modelu DOM. W3C XML Nové třídy umožňují přístup k relační data, poskytuje metody pro synchronizaci s dat ADO.NET, současně vystavení dat jako XML. Další informace najdete v tématu [synchronizace datové sady s datovým dokumentem XML](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
 V modelu DOM je zvláště užitečná pro čtení dat XML do paměti pro změnu jeho strukturu, můžete přidat nebo odebrat uzly nebo upravit data ukládaná společností uzel jako text obsažen v elementu. Ale jsou k dispozici další třídy, které jsou rychlejší než v modelu DOM v jiných scénářích. Rychlá, bez mezipaměti, dopředné stream přístup XML, použijte **XmlReader** a **XmlWriter**. Pokud potřebujete s modelem kurzor náhodný přístup a **XPath**, použijte **objektem XPathNavigator nastaveným na** třídy.  
  
## <a name="see-also"></a>Viz také:

- [Typy uzlů XML](../../../../docs/standard/data/xml/types-of-xml-nodes.md)
- [Mapování hierarchie objektů na data XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
