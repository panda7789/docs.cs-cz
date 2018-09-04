---
title: Zobrazení dat
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 75719e91daba189c1d93491a1db26acc80100bea
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514749"
---
# <a name="dataviews"></a>Zobrazení dat
A <xref:System.Data.DataView> vám umožní vytvářet různá zobrazení dat uložených v <xref:System.Data.DataTable>, funkce, která se často používá v aplikacích datové vazby. Použití **DataView**, můžete zpřístupnit data v tabulce s jiné pořadí řazení a data lze filtrovat podle stavu nebo podle výraz filtru řádků.  
  
 A **DataView** zajišťuje dynamické zobrazení dat v základním **DataTable**: obsah, řazení a členství odrážejí změny při jejich výskytu. Toto chování se liší od **vyberte** metodu **DataTable**, který vrátí hodnotu <xref:System.Data.DataRow> pole z tabulky podle určitého pořadí filtr nebo řazení: thiscontent odráží změny Základní tabulka, ale jeho členství a pořadí zůstat statický. Dynamické schopnosti **DataView** ideální pro vázání dat aplikací.  
  
 A **DataView** vám poskytne dynamický náhled na jednu sadu dat, podobně jako na zobrazení databáze, do které můžete použít různé řazení a filtrování kritéria. Na rozdíl od zobrazení databáze, ale **DataView** nemůže být zpracován jako tabulku a nemůžete zviditelňují spojené tabulky. Také nelze vyloučit sloupce, které existují ve zdrojové tabulce, ani připojit sloupců, jako jsou výpočetní sloupce, které neexistují ve zdrojové tabulce.  
  
 Můžete použít <xref:System.Data.DataView.DataViewManager%2A> ke správě nastavení zobrazení pro všechny tabulky v **datovou sadu**. **Objekt DataViewManager** vám poskytuje pohodlný způsob, jak spravovat výchozí nastavení zobrazení pro každou tabulku. Při vytváření vazby ovládacího prvku do více než jednu tabulku **datovou sadu**, připojení k **objekt DataViewManager** je ideální volbou.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 Popisuje, jak vytvořit **DataView** pro **DataTable**.  
  
 [Řazení a filtrování dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 Popisuje, jak nastavit vlastnosti **DataView** vrátit konkrétní kritéria schůzky podmnožiny řádky dat, nebo vrátit data v konkrétním pořadí.  
  
 [DataRows a DataRowViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 Popisuje, jak získat přístup k datům vystavené **DataView**.  
  
 [Hledání řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 Popisuje, jak k vyhledání konkrétního řádku **DataView**.  
  
 [ChildViews a relace](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 Popisuje postup vytvoření zobrazení dat pomocí vztahu nadřazenosti a podřízenosti **DataView**.  
  
 [Úpravy zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 Popisuje, jak upravovat data v základním **DataTable** prostřednictvím **DataView**, včetně povolení nebo zakázání aktualizací.  
  
 [Zpracování událostí zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 Popisuje způsob použití **ListChanged** událostí, na které přijde upozornění při obsah nebo pořadí **DataView** se aktualizuje.  
  
 [Správa zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 Popisuje způsob použití **objekt DataViewManager** ke správě **DataView** nastavení pro každou tabulku v **datovou sadu**.  
  
## <a name="related-sections"></a>Související oddíly  
 [ASP.NET – webové aplikace](https://msdn.microsoft.com/library/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 Poskytuje přehled a podrobné postupy pro vytváření aplikací ASP.NET, webových formulářů a webových služeb.  
  
 [Aplikace Windows](https://msdn.microsoft.com/library/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 Poskytuje podrobné informace o práci s Windows Forms a konzolové aplikace.  
  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Popisuje **datovou sadu** objekt a jak ho použít ke správě dat aplikací.  
  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Popisuje **DataTable** objekt a jak ho použít ke správě dat aplikací, samostatně nebo jako součást **datovou sadu**.  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Popisuje ADO.NET architektura a komponenty a jak pomocí ADO.NET pro přístup k existujícím zdrojům dat a spravovat data aplikací.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
