---
title: Odvozování sloupců
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: f3edd09b1fb8169e8f609514de38b3c37574079b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655228"
---
# <a name="inferring-columns"></a>Odvozování sloupců
Po ADO.NET bylo zjištěno z dokumentu XML, které prvky k odvození jako tabulka pro <xref:System.Data.DataSet>, pak odvodí sloupce pro tyto tabulky. ADO.NET 2.0 zavedl nový modul odvození schématu, která odvodí typ dat silného typu pro každou **simpleType** elementu. V předchozích verzích, datový typ vyvozeným **simpleType** element se vždy **XSD: String**.  
  
## <a name="migration-and-backward-compatibility"></a>Migrace a zpětné kompatibility  
 **ReadXml** metoda přebírá argument typu **InferSchema**. Tento argument můžete zadat odvození chování, které jsou kompatibilní s předchozími verzemi. Dostupné hodnoty pro **InferSchema** výčtu jsou uvedeny v následující tabulce.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 Poskytuje zpětnou kompatibilitu tím, že vždy odvození jednoduchý typ jako <xref:System.String>.  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Odvodí typ dat silného typu. Vyvolá výjimku, pokud je použita s <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Ignoruje všechny vložené schéma a načte data do existující <xref:System.Data.DataSet> schématu.  
  
## <a name="attributes"></a>Atributy  
 Jak jsou definovány v [odvozování tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), element s atributy se odvodit jako tabulku. Atributy daného prvku se pak odvodit jako sloupce pro tabulku. **ColumnMapping** vlastnost sloupců bude nastavena na **MappingType.Attribute**, aby bylo zajištěno, že názvy sloupců zapisují jako atributy, pokud schéma se zapíšou zpátky do XML. Hodnoty atributů jsou uloženy v řádku v tabulce. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Procesu odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **attr1** a **attr2**. **ColumnMapping** vlastnost obou sloupců bude nastavena na **MappingType.Attribute**.  
  
 **DataSet:** Prvek DocumentElement  
  
 **Tabulka:** element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Prvky bez atributy nebo podřízené prvky  
 Pokud element nemá žádné podřízené prvky a atributy, se odvodit jako sloupec. **ColumnMapping** vlastnost sloupec bude nastavena na **MappingType.Element**. Text pro podřízené prvky je uložen v řádku v tabulce. Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Procesu odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci, **ChildElement1** a **ChildElement2**. **ColumnMapping** vlastnost obou sloupců bude nastavena na **MappingType.Element**.  
  
 **DataSet:** Prvek DocumentElement  
  
 **Tabulka:** element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## <a name="see-also"></a>Viz také:
- [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
