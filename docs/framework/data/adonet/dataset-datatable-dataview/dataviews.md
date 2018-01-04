---
title: DataView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 26fbae0474253dc9792a0290a36dd52044d148b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="dataviews"></a>DataView
A <xref:System.Data.DataView> umožňuje vytvářet různá zobrazení dat uložených v <xref:System.Data.DataTable>, funkci, která se často používá v aplikacích datové vazby. Použití **DataView**, můžou zpřístupnit data v tabulce s různým řazením a data lze filtrovat podle řádku stavu nebo podle výraz filtru.  
  
 A **DataView** poskytuje dynamické zobrazení dat v základní **DataTable**: obsah, řazení a členství projevily změny, kdy k nim dojde. Toto chování se liší od **vyberte** metodu **DataTable**, která vrátí <xref:System.Data.DataRow> pole z tabulky podle konkrétní pořadí filtrů a řazení: thiscontent odráží změny základní tabulku, ale jeho členství a řazení zůstat statický. Dynamické schopnosti **DataView** zkontrolujte ideální pro vazby dat aplikací.  
  
 A **DataView** poskytuje dynamické zobrazení jednu sadu dat, podobně jako zobrazení databáze, do které můžete použít jiné řazení a filtrování kritéria. Na rozdíl od zobrazení databáze, ale **DataView** nemůže být považované za tabulky a zobrazení spojené tabulky nelze zadat. Také nelze vyloučit sloupce, které existují ve zdrojové tabulce, ani připojit sloupce, např. výpočetní sloupců, které nejsou k dispozici ve zdrojové tabulce.  
  
 Můžete použít <xref:System.Data.DataView.DataViewManager%2A> ke správě nastavení zobrazení pro všechny tabulky v **datovou sadu**. **DataViewManager** vám poskytne pohodlný způsob, jak spravovat výchozí nastavení zobrazení pro každou tabulku. Při vytváření vazby ovládacího prvku k více než jednu tabulku **datovou sadu**, závazný k **DataViewManager** je ideální volbou.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 Popisuje postup vytvoření **DataView** pro **DataTable**.  
  
 [Řazení a filtrování dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 Popisuje, jak nastavit vlastnosti **DataView** vrátit podmnožiny dat řádků kritéria filtru konkrétní schůzky, nebo vrátit data v konkrétní řazení.  
  
 [DataRows a DataRowViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 Popisuje, jak získat přístup k datům vystavené **DataView**.  
  
 [Hledání řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 Popisuje, jak k vyhledání konkrétního řádku **DataView**.  
  
 [ChildViews a relace](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 Popisuje postup vytvoření zobrazení dat pomocí relaci nadřazený podřízený **DataView**.  
  
 [Úpravy zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 Popisuje, jak upravit data v podkladové **DataTable** prostřednictvím **DataView**, včetně povolení nebo zakázání aktualizací.  
  
 [Zpracování událostí zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 Popisuje způsob použití **ListChanged** událostí pro příjem oznámení při obsah nebo pořadí **DataView** se právě aktualizuje.  
  
 [Správa zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 Popisuje způsob použití **DataViewManager** ke správě **DataView** nastavení pro každou tabulku v **datovou sadu**.  
  
## <a name="related-sections"></a>Související oddíly  
 [Webových aplikací ASP.NET](http://msdn.microsoft.com/en-us/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 Poskytuje přehled a podrobné postupy pro vytváření aplikací ASP.NET, webových formulářů a webových služeb.  
  
 [Aplikace systému Windows](http://msdn.microsoft.com/en-us/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 Poskytuje podrobné informace o práci s Windows Forms a konzolové aplikace.  
  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Popisuje **datovou sadu** objekt a jak můžete použít ke správě dat aplikací.  
  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Popisuje **DataTable** objekt a jak můžete použít ke správě dat aplikace, samostatně nebo jako součást **datovou sadu**.  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 Popisuje technologie ADO.NET architektura a komponenty a jak používat technologie ADO.NET pro přístup k existující zdroje dat a spravovat data aplikací.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
