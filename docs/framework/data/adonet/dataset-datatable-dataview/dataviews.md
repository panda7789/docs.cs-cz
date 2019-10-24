---
title: Zobrazení dat
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 1b202af052c05ed9dc671fa20c9c366f280ec5c7
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774168"
---
# <a name="dataviews"></a>Zobrazení dat
@No__t_0 umožňuje vytvářet různá zobrazení dat uložených v <xref:System.Data.DataTable>, což je funkce, která se často používá v aplikacích pro datovou vazbu. Pomocí objektu **DataView**můžete vystavit data v tabulce s různými objednávkami řazení a data můžete filtrovat podle stavu řádku nebo podle výrazu filtru.

 Zobrazení **DataView** poskytuje dynamický pohled na data v podkladovém **objektu DataTable**: obsah, řazení a členství odrážejí změny při jejich výskytu. Toto chování se liší od metody **Select** **objektu DataTable**, která vrací <xref:System.Data.DataRow> pole z tabulky na základě konkrétního filtru nebo pořadí řazení: Tento obsah odráží změny v podkladové tabulce, ale její členství a řazení. zůstat statické. Dynamické možnosti zobrazení dat usnadňují použití datových **vazeb v aplikacích** .

 Zobrazení **DataView** poskytuje dynamické zobrazení jedné sady dat, podobně jako zobrazení databáze, na které můžete použít různá kritéria řazení a filtrování. Na rozdíl od zobrazení databáze však nelze **objekt DataView** zpracovat jako tabulku a nemůže poskytnout zobrazení spojených tabulek. Nemůžete také vyloučit sloupce, které existují ve zdrojové tabulce, nebo přidat sloupce, které neexistují ve zdrojové tabulce, například výpočetní sloupce.

 Pomocí <xref:System.Data.DataView.DataViewManager%2A> můžete spravovat nastavení zobrazení pro všechny tabulky v **datové sadě**. Objekt **DataViewManager** poskytuje pohodlný způsob, jak spravovat výchozí nastavení zobrazení pro každou tabulku. Při vázání ovládacího prvku na více než jednu tabulku **datové sady**je ideální volbou vazba na objekt **DataViewManager** .

## <a name="in-this-section"></a>V tomto oddílu
 [Vytvoření zobrazení dat](creating-a-dataview.md) Popisuje, jak vytvořit **DataView** pro **DataTable**.

 [Řazení a filtrování dat](sorting-and-filtering-data.md) Popisuje, jak nastavit vlastnosti objektu **DataView** tak, aby vracely podmnožiny datových řádků splňujících konkrétní kritéria filtru, nebo aby vracela data v konkrétním pořadí řazení.

 [DataRows a DataRowViews](datarows-and-datarowviews.md) Popisuje, jak získat přístup k datům vystaveným **objektem DataView**.

 [Hledání řádků](finding-rows.md) Popisuje, jak najít konkrétní řádek v zobrazení **DataView**.

 [ChildViews a vztahy](childviews-and-relations.md) Popisuje, jak vytvořit zobrazení dat z vztahu nadřazená-podřízená pomocí objektu **DataView**.

 [Úpravy zobrazení](modifying-dataviews.md) Popisuje, jak upravit data v podkladovém **objektu DataTable** prostřednictvím objektu **DataView**, včetně povolení nebo zakázání aktualizací.

 [Zpracování událostí zobrazení dat](handling-dataview-events.md) Popisuje, jak používat událost **ListChanged** k získání oznámení při aktualizaci obsahu nebo objednávky zobrazení **dat** .

 [Správa zobrazení](managing-dataviews.md) Popisuje, jak používat objekt **DataViewManager** **ke správě nastavení** zobrazení pro každou tabulku v **datové sadě**.

## <a name="related-sections"></a>Související oddíly
 [Webové aplikace v ASP.NET](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100)) Poskytuje přehledy a podrobné postupy pro vytváření aplikací ASP.NET, webových formulářů a webových služeb.

 [Aplikace systému Windows](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100)) Poskytuje podrobné informace o práci s aplikacemi model Windows Forms a konzolových aplikací.

 [Datové sady, datové tabulky a Datazobrazení](index.md) Popisuje objekt **DataSet** a způsob, jak jej můžete použít ke správě aplikačních dat.

 [DataTables](datatables.md) Popisuje objekt **DataTable** a způsob, jak jej můžete použít ke správě dat aplikace samostatně nebo jako součást **datové sady**.

 [ADO.NET](../index.md) Popisuje architekturu a komponenty ADO.NET a způsob použití ADO.NET pro přístup k existujícím zdrojům dat a správě dat aplikací.

## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../ado-net-overview.md)
