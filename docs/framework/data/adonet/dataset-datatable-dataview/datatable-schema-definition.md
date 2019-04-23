---
title: Definice schématu datové tabulky
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: e8710e7d92558f525a6feaedf8d0635c5ce6e2c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163069"
---
# <a name="datatable-schema-definition"></a>Definice schématu datové tabulky
Schéma a struktura tabulky je reprezentován sloupců a omezení. Definujete schéma <xref:System.Data.DataTable> pomocí <xref:System.Data.DataColumn> objekty stejně jako <xref:System.Data.ForeignKeyConstraint> a <xref:System.Data.UniqueConstraint> objekty. Sloupce v tabulce můžete mapovat na sloupce ve zdroji dat, obsahují vypočítané hodnoty z výrazů, automaticky zvýšit jejich hodnoty nebo obsahovat hodnoty primárního klíče.  
  
 Podle názvu sloupce, relace a omezení v tabulce jsou malá a velká písmena. Minimálně dva sloupce, relace nebo omezení může proto existovat v tabulce, které mají stejný název, ale které se liší velikostí písmen. Například můžete mít **Sloupec1** a **Sloupec1**. V například případ, odkaz na jeden ze sloupců podle názvu musí shodovat s velikostí písmen názvu sloupce přesně; v opačném případě je vyvolána výjimka. Například pokud v tabulce **myTable** obsahuje sloupce **Sloupec1** a **Sloupec1**, by odkazovat **Sloupec1** podle názvu jako  **myTable.Columns["Col1"]**, a **Sloupec1** jako **myTable.Columns["col1"]**. Pokus o sloupci jako odkaz na **myTable.Columns["COL1"]** vygeneruje výjimku.  
  
 Rozlišování pravidlo neplatí, pokud pouze jeden sloupec, relaci nebo omezení s konkrétním názvem existuje. To znamená pokud žádné sloupce, relace nebo zadaných objektů omezení v tabulce odpovídá názvu tohoto konkrétního sloupce, relace nebo zadaných objektů omezení, podle názvu pomocí případ může odkazovat na objekt a není vyvolána žádná výjimka. Například, pokud tabulka obsahuje pouze **Sloupec1**, můžete na něj mohli odkazovat pomocí **Moje. Sloupce ["Sloupec1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataTable.CaseSensitive%2A> Vlastnost **DataTable** nemá vliv na toto chování. **CaseSensitive** vlastnost se vztahuje na data v tabulce a ovlivňuje řazení, hledání, filtrování, vynucuje omezení a tak dále, ale ne k odkazy na sloupce, relace a omezení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přidání sloupců do datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 Popisuje, jak definovat tabulku s využitím sloupce **DataColumn** objekty.  
  
 [Vytváření sloupců výrazů](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 Vysvětluje, jak **výraz** vlastnost sloupec slouží k výpočtu hodnot na základě hodnot od ostatních sloupců v řádku.  
  
 [Vytváření sloupců s automatickým navyšováním](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 Popisuje, jak lze nastavit sloupec se automaticky zvýší číselné hodnoty do zkontrolujte, jedinečný sloupec hodnotu na každém řádku.  
  
 [Definování primárních klíčů](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 Popisuje, jak určit primární klíč tabulky z jedné nebo více **DataColumn** objekty.  
  
 [Omezení datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 Popisuje, jak definovat cizího klíče a unikátních omezení pro sloupce v tabulce.  
  
## <a name="see-also"></a>Viz také:

- [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
