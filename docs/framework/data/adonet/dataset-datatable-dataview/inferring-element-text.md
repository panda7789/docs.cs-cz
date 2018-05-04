---
title: Odvození textu elementu
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: b32d8f3f89a16166ffc0e903ef1f63c3b97a249c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="inferring-element-text"></a>Odvození textu elementu
Pokud element obsahuje text a nemá žádné podřízené prvky k odvodit, protože tabulky, jako je například (elementy s atributy) nebo opakujících se prvků, nový sloupec s názvem **TableName_Text** přidá do tabulky, který je používán pro daný element. Text obsažené v elementu budou přidány do řádek v tabulce a uložená do nového sloupce. **ColumnMapping** vlastnost nového sloupce, bude nastavena pro **MappingType.SimpleContent**.  
  
 Zvažte například následující kód XML.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 Proces odvození vytvoří tabulku s názvem **Element1** s dva sloupce: **attr1** a **Element1_Text**. **ColumnMapping** vlastnost **attr1** sloupec bude nastavena pro **MappingType.Attribute**. **ColumnMapping** vlastnost **Element1_Text** sloupec bude nastavena pro **MappingType.SimpleContent**.  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1|Text1|  
  
 Pokud element obsahuje text, ale také obsahuje podřízené elementy, které obsahují text, nepřidají sloupce pro tabulku pro ukládání textu obsažené v elementu. Text obsažené v elementu budou ignorovány, zatímco text v podřízených elementů je součástí řádek v tabulce. Zvažte například následující kód XML.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 Proces odvození vytvoří tabulku s názvem **Element1** s jedním sloupcem s názvem **ChildElement1**. Text pro **ChildElement1** element budou zahrnuty do řádek v tabulce. Další text se budou ignorovat. **ColumnMapping** vlastnost **ChildElement1** sloupec bude nastavena pro **MappingType.Element**.  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## <a name="see-also"></a>Viz také  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
