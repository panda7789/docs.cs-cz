---
title: model DOM (Document Object Model) dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
ms.openlocfilehash: dbc53d713d77cfdc9d0dbb8a201f2b5627a76921
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283387"
---
# <a name="xml-document-object-model-dom"></a>model DOM (Document Object Model) dokumentu XML

Třída XML model DOM (Document Object Model) (DOM) je reprezentace dokumentu XML v paměti. Model DOM umožňuje programově číst, manipulovat a upravovat dokument XML. Třída **XmlReader** také přečte XML; ale poskytuje neuložený obsah do mezipaměti, jen pro čtení a přístup jen pro čtení. To znamená, že neexistují žádné možnosti pro úpravu hodnot atributu nebo obsahu prvku nebo možnost vkládat a odebírat uzly pomocí objektu **XmlReader**. Úpravy jsou primární funkcí modelu DOM. Je to běžný a strukturovaný způsob, jak jsou data XML reprezentována v paměti, přestože skutečná data XML jsou ukládána lineárním způsobem v souboru nebo přicházejí v jiném objektu. Níže jsou data XML.

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

Následující obrázek ukazuje, jak je strukturována paměť, když jsou tato data XML čtena do struktury DOM.

![Struktura dokumentu XML](media/xml-to-domtree.gif "XML_To_DOMTree") Struktura dokumentu XML

V rámci struktury dokumentu XML každý kroužek na tomto obrázku představuje uzel, který se nazývá objekt **XmlNode** . Objekt **XmlNode** je základní objekt ve stromové struktuře modelu DOM. Třída **XmlDocument** , která rozšiřuje **XmlNode**, podporuje metody pro provádění operací v dokumentu jako celku (například načtení do paměti nebo uložení XML do souboru. **XmlDocument** navíc poskytuje prostředky pro zobrazení a manipulaci s uzly v celém dokumentu XML. **XmlNode** i **XmlDocument** mají vylepšení výkonu a použitelnosti a mají metody a vlastnosti pro:

- Přístup k uzlům, které jsou specifické pro model DOM, jako jsou uzly elementů, uzly odkazů na entity a tak dále, upravte.

- Načtěte celé uzly kromě informací, které uzel obsahuje, jako je například text v uzlu element.

  > [!NOTE]
  > Pokud aplikace nevyžaduje strukturu nebo možnosti úprav poskytované modelem DOM, třídy **XmlReader** a **XmlWriter** poskytují neuložený datový proud, který je určen pouze pro přístup ke streamu XML. Další informace naleznete v tématech <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter>.

Objekty **uzlů** mají sadu metod a vlastností a také základní a jasně definované charakteristiky. Některé z těchto vlastností jsou:

- Uzly mají jeden nadřazený uzel, nadřazený uzel je nad uzlem přímo. Jediným uzlem, které nemají nadřazený objekt, je kořen dokumentu, protože se jedná o uzel nejvyšší úrovně, který obsahuje samotný dokument a fragmenty dokumentů.

- Většina uzlů může mít více podřízených uzlů, které jsou uzly přímo pod nimi. Následuje seznam typů uzlů, které mohou mít podřízené uzly.

  - **Dokumentů**

  - **DocumentFragment**

  - **EntityReference**

  - **Prvek**

  - **Atribut**

  Uzly **XmlDeclaration**, **Notation**, **entity**, **CDATASection**, **text**, **Comment**, **ProcessingInstruction**a **DocumentType** nemají podřízené uzly.

- Uzly, které jsou na stejné úrovni, reprezentované v diagramu **Kniha** a uzly **pubinfo** , jsou na stejné úrovni.

Jedna z vlastností modelu DOM je způsob, jakým zpracovává atributy. Atributy nejsou uzly, které jsou součástí vztahů nadřazených, podřízených a na stejné úrovni. Atributy jsou považovány za vlastnost uzlu elementu a jsou tvořeny názvem a dvojicí hodnot. Například pokud máte data XML sestávající z `format="dollar` "přidruženo k elementu" `price` , slovo `format` je název a hodnota `format` atributu je `dollar` . Chcete-li načíst `format="dollar"` atribut **cenového** uzlu, zavolejte metodu **GetAttribute** , pokud je kurzor umístěn v `price` uzlu element. Další informace naleznete v tématu [přístup k atributům v modelu DOM](accessing-attributes-in-the-dom.md).

V případě, že je kód XML čten do paměti, jsou vytvořeny uzly. Ale ne všechny uzly jsou stejného typu. Element v jazyce XML má odlišná pravidla a syntaxi než instrukce pro zpracování. Proto se při čtení různých dat typ uzlu přiřadí každému uzlu. Tento typ uzlu určuje vlastnosti a funkce uzlu.

Další informace o typech uzlů generovaných v paměti naleznete v tématu [typy uzlů XML](types-of-xml-nodes.md). Další informace o objektech vytvořených ve stromové struktuře uzlu najdete v tématu [mapování hierarchie objektů na data XML](mapping-the-object-hierarchy-to-xml-data.md).

Společnost Microsoft rozšířila rozhraní API, která jsou k dispozici v konsorcium World Wide Web (W3C) DOM úrovně 1 a 2, aby bylo snazší pracovat s dokumentem XML. I když plně podporují standardy W3C, další třídy, metody a vlastnosti přidávají funkce nad rámec toho, co je možné provést pomocí konsorcia W3C XML DOM. Nové třídy vám umožní přístup k relačním datům, což vám dává metody pro synchronizaci s daty ADO.NET a současně zpřístupňují data jako XML. Další informace najdete v tématu [synchronizace datové sady s objektu XmlDataDocument](../../../framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).

Model DOM je nejužitečnější pro čtení dat XML do paměti pro změnu struktury, pro přidání nebo odebrání uzlů nebo pro úpravu dat držených uzlem jako v textu obsaženém v prvku. K dispozici jsou však jiné třídy, které jsou rychlejší než model DOM v jiných scénářích. V případě rychlého, neuloženého datového proudu, který je pouze pro zápis do mezipaměti, použijte rozhraní **XmlReader** a **XmlWriter**. Pokud potřebujete náhodný přístup pomocí modelu kurzoru a **XPath**, použijte třídu **XPathNavigator** .

## <a name="see-also"></a>Viz také

- [Typy uzlů XML](types-of-xml-nodes.md)
- [Mapování hierarchie objektů na data XML](mapping-the-object-hierarchy-to-xml-data.md)
