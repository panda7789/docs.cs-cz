---
title: "Definice schématu DataTable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ae4d5af0238108d0f309ae311e172450bf226c23
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="datatable-schema-definition"></a>Definice schématu DataTable
Schéma a struktura tabulky je reprezentována sloupce a omezení. Můžete definovat schéma <xref:System.Data.DataTable> pomocí <xref:System.Data.DataColumn> objekty a také <xref:System.Data.ForeignKeyConstraint> a <xref:System.Data.UniqueConstraint> objekty. Sloupce v tabulce můžete mapovat na sloupce ve zdroji dat, obsahují počítané hodnoty z výrazů, automaticky zvýšit jejich hodnoty nebo obsahovat hodnot primárního klíče.  
  
 Odkazy na název sloupce, vztahy a omezení v tabulce rozlišují velká a malá písmena. V tabulce, která mají stejný název, ale které se liší v případě může proto existovat dvě nebo více sloupců, vztahů nebo omezení. Například můžete mít **Sloupec1** a **Sloupec1**. V například případě odkaz na některý ze sloupců podle názvu musí v případě názvu sloupce přesně shodovat; v opačném případě je vyvolána výjimka. Například pokud tabulka **myTable** obsahuje sloupce **Sloupec1** a **Sloupec1**, by odkazujete **Sloupec1** podle názvu jako  **myTable.Columns["Col1"]**, a **Sloupec1** jako **myTable.Columns["col1"]**. Pokus o buď sloupců jako odkaz na **myTable.Columns["COL1"]** by generovat výjimku.  
  
 Pravidlo rozlišování neplatí, pokud jen jeden sloupec, relaci nebo omezení s konkrétním názvem existuje. To znamená pokud žádný sloupec, relace nebo objektů omezení v tabulce odpovídá názvu této konkrétní sloupec, relace nebo objektů omezení, může odkaz na objekt podle názvu pomocí jakékoli případ a nedojde k výjimce. Například, pokud tabulka obsahuje pouze **Sloupec1**, můžete odkazovat pomocí **Moje. Sloupce ["Sloupec1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataTable.CaseSensitive%2A> Vlastnost **DataTable** nemá vliv na toto chování. **CaseSensitive** vlastnost se vztahuje na data v tabulce a ovlivňuje řazení, vyhledávání a filtrování, vynucení omezení a tak dále, ale ne na odkazy na sloupce, vztahy a omezení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přidání sloupců do datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 Popisuje, jak definovat sloupce tabulky pomocí **DataColumn** objekty.  
  
 [Vytváření sloupců výrazů](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 Vysvětluje, jak **výraz** vlastnost sloupce lze použít k výpočtu hodnot na základě hodnot z ostatních sloupců v řádku.  
  
 [Vytváření sloupců s automatickým navyšováním](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 Popisuje, jak lze nastavit sloupec se automaticky zvýší číselné hodnoty zajistit jedinečný sloupec hodnotu na řádek.  
  
 [Definování primárních klíčů](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 Popisuje, jak určit primární klíč tabulky z jedné nebo více **DataColumn** objekty.  
  
 [Omezení datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 Popisuje, jak definovat cizí klíč a jedinečná omezení pro sloupce v tabulce.  
  
## <a name="see-also"></a>Viz také  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
