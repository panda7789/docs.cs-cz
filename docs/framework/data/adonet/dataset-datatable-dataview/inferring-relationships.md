---
title: Odvozování relací
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 7dc3fb0c6098d636e640aaf52b72a404c1486492
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516289"
---
# <a name="inferring-relationships"></a>Odvozování relací
Pokud element, který je odvozený jako tabulka má podřízený element, který je také odvodit jako tabulku <xref:System.Data.DataRelation> mezi dvěma tabulkami se nevytvoří. Nový sloupec s názvem **ParentTableName_Id** se přidají do tabulky vytvořené pro nadřazený element a tabulku vytvořenou pro podřízený element. **ColumnMapping** vlastnost tohoto sloupce identity bude nastavena na **MappingType.Hidden**. Sloupec bude automatické zvyšování hodnoty primárního klíče pro nadřazené tabulky a se použije pro **DataRelation** mezi dvěma tabulkami. Datový typ sloupce identity přidání bude **System.Int32**, na rozdíl od datového typu všechny ostatní odvozené sloupců, což je **System.String**. A <xref:System.Data.ForeignKeyConstraint> s **DeletRule** = **Cascade** také vytvoří nový sloupec v nadřazené a podřízené tabulky.  
  
 Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Procesu odvození vytvoří dvě tabulky: **Element1** a **ChildElement1**.  
  
 **Element1** tabulka bude mít dva sloupce: **Element1_Id** a **ChildElement2**. **ColumnMapping** vlastnost **Element1_Id** sloupec bude nastaven na **MappingType.Hidden**. **ColumnMapping** vlastnost **ChildElement2** sloupec bude nastaven na **MappingType.Element**. **Element1_Id** sloupec bude nastaven jako primární klíč **Element1** tabulky.  
  
 **ChildElement1** tabulka bude mít tři sloupce: **attr1**, **attr2** a **Element1_Id**. **ColumnMapping** vlastnost **attr1** a **attr2** sloupce se nastaví na **MappingType.Attribute**. **ColumnMapping** vlastnost **Element1_Id** sloupec bude nastaven na **MappingType.Hidden**.  
  
 A **DataRelation** a **Objekt ForeignKeyConstraint** se vytvoří pomocí **Element1_Id** sloupců z obou tabulek.  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **Tabulka:** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|Hodnota1|Hodnota2|0|  
  
 **DataRelation:** Element1_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **Tabulka:** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **Vnořené:** True  
  
 **Objekt ForeignKeyConstraint:** Element1_ChildElement1  
  
 **Sloupec:** Element1_Id  
  
 **ParentTable:** Element1  
  
 **Tabulka:** ChildElement1  
  
 **DeletRule:** Cascade  
  
 **AcceptRejectRule:** None  
  
## <a name="see-also"></a>Viz také  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Vnoření datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
