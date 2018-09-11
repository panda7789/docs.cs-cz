---
title: Souhrn procesu odvození schématu datové sady
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 1583d5232a3dd483bbe2a6fa0b1bc8a3ae6a659f
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277624"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a>Souhrn procesu odvození schématu datové sady
Procesu odvození nejdřív zjistí, z dokumentu XML, prvky, které se odvodit jako tabulka. Ze zbývajících XML určuje proces odvození sloupce pro tyto tabulky. Pro vnořené tabulky procesu odvození generuje vnořené <xref:System.Data.DataRelation> a <xref:System.Data.ForeignKeyConstraint> objekty.  
  
 Tady je stručný přehled odvozených pravidel:  
  
-   Prvky, které mají atributy jsou odvozeny jako tabulka.  
  
-   Prvky, které mají podřízené prvky jsou odvozeny jako tabulka.  
  
-   Prvky, které se opakují jsou odvozeny jako jednu tabulku.  
  
-   Pokud má element dokumentu nebo kořenový, atributy a žádné podřízené prvky, které by odvodit jako sloupce, je odvozený jako <xref:System.Data.DataSet>. V opačném případě je element dokumentu odvozen jako tabulku.  
  
-   Atributy jsou odvozeny jako sloupce.  
  
-   Prvky, které mají žádné atributy nebo podřízené prvky a, které se neopakují, jsou odvozeny jako sloupce.  
  
-   Pro prvky, které jsou odvozeny jako vnořené tabulky v rámci další prvky, které jsou odvozeny také jako tabulky, vnořený **DataRelation** je vytvořen mezi dvěma tabulkami. Nové, primární klíčový sloupec s názvem **TableName_Id** bude přidána do obou tabulek a používá **DataRelation**. A **Objekt ForeignKeyConstraint** je vytvořen mezi dvěma tabulkami pomocí **TableName_Id** sloupce.  
  
-   Pro prvky, které jsou odvozeny jako tabulky a které obsahují text, ale mít žádné podřízené prvky, nový sloupec s názvem **TableName_Text** je vytvořená pro text jednotlivých prvků. Pokud element je odvozen jako tabulku a obsahuje text, ale má také podřízené prvky, text se ignoruje.  
  
## <a name="see-also"></a>Viz také  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
