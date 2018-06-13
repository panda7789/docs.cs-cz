---
title: Odvození relace
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 9833966fa5a16bef70a6ae2b9ca618fde0e05fbb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759033"
---
# <a name="inferring-relationships"></a>Odvození relace
Pokud má element, který je používán jako tabulku podřízený element, který je také odvodit jako tabulku, <xref:System.Data.DataRelation> se vytvoří mezi dvěma tabulkami. Nový sloupec s názvem **ParentTableName_Id** bude přidán do tabulky vytvořili pro nadřazený element i v tabulce pro podřízený element vytvořit. **ColumnMapping** vlastnost v tomto sloupci identity bude nastavena pro **MappingType.Hidden**. Sloupec bude automaticky rostoucí primární klíč pro nadřazenou tabulkou a bude použit pro **DataRelation** mezi dvěma tabulkami. Datový typ sloupce identity přidané bude **System.Int32**, na rozdíl od všech ostatních odvozené sloupce datový typ, který je **System.String**. A <xref:System.Data.ForeignKeyConstraint> s **DeletRule** = **Cascade** bude vytvořen také pomocí nového sloupce v nadřazené a podřízené tabulky.  
  
 Zvažte například následující kód XML:  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří dvě tabulky: **Element1** a **ChildElement1**.  
  
 **Element1** tabulka bude mít dva sloupce: **Element1_Id** a **ChildElement2**. **ColumnMapping** vlastnost **Element1_Id** sloupec bude nastavena pro **MappingType.Hidden**. **ColumnMapping** vlastnost **ChildElement2** sloupec bude nastavena pro **MappingType.Element**. **Element1_Id** sloupec bude nastaven jako primární klíč **Element1** tabulky.  
  
 **ChildElement1** tabulka bude mít tři sloupce: **attr1**, **attr2** a **Element1_Id**. **ColumnMapping** vlastnost **attr1** a **attr2** sloupců bude nastavena pro **MappingType.Attribute**. **ColumnMapping** vlastnost **Element1_Id** sloupec bude nastavena pro **MappingType.Hidden**.  
  
 A **DataRelation** a **vlastnosti ForeignKeyConstraint** se vytvoří pomocí **Element1_Id** sloupců z obou tabulek.  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **Tabulka:** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|value1|Value2|0|  
  
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
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
