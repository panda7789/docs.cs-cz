---
title: Definice schématu datové tabulky
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: 20fee4316ad95c0f8716a0f374410009ea129222
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952349"
---
# <a name="datatable-schema-definition"></a>Definice schématu datové tabulky
Schéma, neboli struktura tabulky, je reprezentována sloupci a omezeními. Definujete schéma <xref:System.Data.DataTable> s použitím <xref:System.Data.DataColumn> objektů <xref:System.Data.ForeignKeyConstraint> i objektů a <xref:System.Data.UniqueConstraint> . Sloupce v tabulce lze namapovat na sloupce ve zdroji dat, obsahovat počítané hodnoty z výrazů, automaticky zvyšovat jejich hodnoty nebo obsahovat hodnoty primárního klíče.  
  
 Odkazy podle názvu na sloupce, relace a omezení v tabulce rozlišují velká a malá písmena. V tabulce, která má stejný název, mohou být proto dva nebo více sloupců, vztahů nebo omezení, které se liší v případě velkých a malých písmen. Můžete mít například **Sloupec1** a **Sloupec1**. V takovém případě musí být odkaz na jeden ze sloupců podle názvu přesně shodný s názvem sloupce. v opačném případě je vyvolána výjimka. Pokud například tabulka **myTable** obsahuje sloupce **Sloupec1** a **Sloupec1**, měli byste odkazovat na **sloupec** název jako **myTable. Columns ["Sloupec1"]** a **Sloupec1** jako **myTable. Columns ["Sloupec1"]** . Došlo k pokusu o odkaz na jeden ze sloupců jako **myTable. Columns ["Sloupec1"]** vygeneroval výjimku.  
  
 Pravidlo rozlišování velkých a malých písmen neplatí, pokud existuje pouze jeden sloupec, vztah nebo omezení s určitým názvem. To znamená, že pokud žádný jiný sloupec, vztah nebo objekt omezení v tabulce neodpovídá názvu konkrétního objektu sloupce, vztahu nebo omezení, můžete odkazovat na objekt podle názvu pomocí jakéhokoli případu a není vyvolána žádná výjimka. Například pokud má tabulka pouze **Sloupec1**, můžete na ni odkazovat pomocí **My. Sloupce ["SLOUPEC1"]** .  
  
> [!NOTE]
> Vlastnost objektu DataTable nemá vliv na toto chování. <xref:System.Data.DataTable.CaseSensitive%2A> Vlastnost **CaseSensitive** se vztahuje na data v tabulce a ovlivňuje řazení, vyhledávání, filtrování, vynucování omezení atd., ale nikoli odkazy na sloupce, relace a omezení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přidání sloupců do datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 Popisuje, jak definovat sloupce tabulky pomocí objektů DataColumn .  
  
 [Vytváření sloupců výrazů](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 Vysvětluje, jak lze vlastnost **Expression** sloupce použít k výpočtu hodnot na základě hodnot z jiných sloupců na řádku.  
  
 [Vytváření sloupců s automatickým navyšováním](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 Popisuje, jak lze nastavit sloupec tak, aby automaticky zvyšován číselné hodnoty, aby se zajistila jedinečná hodnota sloupce na řádek.  
  
 [Definování primárních klíčů](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 Popisuje, jak zadat primární klíč tabulky z jednoho nebo více objektů DataColumn .  
  
 [Omezení datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 Popisuje, jak definovat cizí klíč a jedinečná omezení pro sloupce v tabulce.  
  
## <a name="see-also"></a>Viz také:

- [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
