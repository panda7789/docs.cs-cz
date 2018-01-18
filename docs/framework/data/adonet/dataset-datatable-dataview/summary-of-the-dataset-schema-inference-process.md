---
title: "Souhrn procesu odvození schéma datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 63ab866785f1fea66ed72fa17589a5be790fcdaa
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>Souhrn procesu odvození schéma datové sady
Odvození proces nejdřív zjistí, z dokumentu XML prvky, které bude odvodit jako tabulky. Z zbývající XML určuje proces odvození sloupce pro tyto tabulky. Pro vnořené tabulky, proces odvození generuje vnořené <xref:System.Data.DataRelation> a <xref:System.Data.ForeignKeyConstraint> objekty.  
  
 Následuje stručné souhrnné informace o odvozená pravidla:  
  
-   Prvky, které mají atributy jsou odvodit jako tabulky.  
  
-   Prvky, které mají podřízené elementy jsou odvodit jako tabulky.  
  
-   Elementy, které se opakují jsou odvodit jako jednu tabulku.  
  
-   Pokud dokument nebo kořenová prvek nemá žádné atributy a žádné podřízené prvky, které by odvodit jako sloupce, je odvodit jako <xref:System.Data.DataSet>. Element dokumentu, jinak je odvodit jako tabulku.  
  
-   Atributy jsou odvodit jako sloupce.  
  
-   Elementy, které mají žádné atributy nebo podřízené elementy a který neopakujte, jsou odvodit jako sloupce.  
  
-   U elementů, které jsou odvozené jako vnořených tabulek v rámci další prvky, které jsou také odvodit jako tabulek, vnořený **DataRelation** se vytvoří mezi dvěma tabulkami. Sloupec nové, primární klíče s názvem **TableName_Id** je přidán do obou tabulek a použít **DataRelation**. A **vlastnosti ForeignKeyConstraint** se vytvoří mezi dvěma tabulkami pomocí **TableName_Id** sloupce.  
  
-   U elementů, které jsou odvozené jako tabulky a který obsahují text, ale mít žádné podřízené prvky, nový sloupec s názvem **TableName_Text** je vytvořená pro text jednotlivých elementů. Pokud element je odvodit jako tabulku a má text, ale také obsahuje podřízené elementy, je text ignoruje.  
  
## <a name="see-also"></a>Viz také  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
