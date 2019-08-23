---
title: Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
ms.openlocfilehash: fa40f1657a433f5f4ade3de25648ca04c37dfa67
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962605"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView
Jedním z důvodů implementace virtuálního režimu v <xref:System.Windows.Forms.DataGridView> ovládacím prvku je načíst data pouze tak, jak je potřeba. Tato metoda se označuje jako *načítání dat za běhu*.  
  
 Pokud pracujete s velmi velkou tabulkou ve vzdálené databázi, například můžete chtít zabránit prodlevám při spouštění, a to tak, že načtete jenom data potřebná pro zobrazení a načítání dalších dat, jenom když uživatel posune nové řádky do zobrazení. Pokud klientské počítače, na kterých běží vaše aplikace, mají k dispozici omezené množství paměti pro ukládání dat, možná budete chtít při načítání nových hodnot z databáze zrušit nepoužívaná data.  
  
 Následující části popisují, jak používat <xref:System.Windows.Forms.DataGridView> ovládací prvek s mezipamětí cache (just-in-time).  
  
 Postup kopírování kódu v tomto tématu jako jediného výpisu naleznete v [tématu How to: Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)DataGridView model Windows Forms.  
  
## <a name="the-form"></a>Formulář  
 Následující příklad kódu definuje formulář obsahující ovládací prvek jen <xref:System.Windows.Forms.DataGridView> pro čtení, který komunikuje `Cache` s objektem prostřednictvím <xref:System.Windows.Forms.DataGridView.CellValueNeeded> obslužné rutiny události. Objekt spravuje místně uložené hodnoty a `DataRetriever` pomocí objektu načítá hodnoty z tabulky Orders ukázkové databáze Northwind. `Cache` Objekt, který `IDataPageRetriever` implementuje rozhraní `Cache` požadované<xref:System.Windows.Forms.DataGridView> třídou, je také použit k inicializaci řádků a sloupců ovládacího prvku. `DataRetriever`  
  
 Typy `IDataPageRetriever`, `DataRetriever` a`Cache` jsou popsány dále v tomto tématu.  
  
> [!NOTE]
> Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>Rozhraní IDataPageRetriever  
 Následující příklad kódu definuje `IDataPageRetriever` rozhraní, které je implementováno `DataRetriever` třídou. Jedinou metodou deklarovanou v tomto rozhraní je `SupplyPageOfData` metoda, která vyžaduje počáteční index řádku a počet řádků na jedné stránce dat. Tyto hodnoty používá implementátor k načtení podmnožiny dat ze zdroje dat.  
  
 `Cache` Objekt používá implementaci tohoto rozhraní během konstrukce pro načtení dvou počátečních stránek dat. Pokaždé, když je potřebná hodnota bez mezipaměti, mezipaměť odhodí jednu z těchto stránek a požádá o novou stránku obsahující hodnotu z `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>Třída  
 Následující příklad kódu definuje `DataRetriever` třídu, která `IDataPageRetriever` implementuje rozhraní pro načtení stránek dat ze serveru. `Columns` <xref:System.Windows.Forms.DataGridView.Rows%2A> Třída také poskytuje<xref:System.Windows.Forms.DataGridView> a `RowCount` vlastnosti, které ovládací prvek používá k vytvoření nezbytných sloupců a k přidání příslušného počtu prázdných řádků do kolekce. `DataRetriever` Přidání prázdných řádků je nezbytné, aby se ovládací prvek choval, jako by obsahoval všechna data v tabulce. To znamená, že okno posuvníku v posuvníku bude mít odpovídající velikost a uživatel bude mít přístup k jakémukoli řádku v tabulce. Řádky jsou vyplněny <xref:System.Windows.Forms.DataGridView.CellValueNeeded> obslužnou rutinou události pouze v případě, že jsou posunuty do zobrazení.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Třída cache  
 Následující příklad kódu definuje `Cache` třídu, která spravuje dvě stránky dat vyplněné `IDataPageRetriever` implementací. Třída definuje vnitřní `DataPage` strukturu, která obsahuje a <xref:System.Data.DataTable> , aby ukládala hodnoty na jednu stránku mezipaměti a které vypočítávají indexy řádků, které reprezentují horní a dolní hranice stránky. `Cache`  
  
 `Cache` Třída načte dvě stránky dat v době konstrukce. Kdykoli událost požádá o hodnotu `Cache` , objekt určí, zda je hodnota k dispozici na jedné z jejích dvou stránek, a pokud ano, vrátí ji. <xref:System.Windows.Forms.DataGridView.CellValueNeeded> Pokud tato hodnota není k dispozici místně, `Cache` objekt určuje, který z jeho dvou stránek je nejvzdálenější z aktuálně zobrazených řádků, a nahradí stránku novým, který obsahuje požadovanou hodnotu, kterou pak vrátí.  
  
 Za předpokladu, že počet řádků na datové stránce je stejný jako počet řádků, které je možné na obrazovce zobrazit najednou, umožňuje tento model stránkování přes tabulku a efektivně se vracet na naposledy prohlíženou stránku.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Další požadavky  
 Předchozí příklady kódu jsou k dispozici jako ukázka načítání dat za běhu. Abyste dosáhli maximální efektivity, budete muset změnit kód tak, aby vyhovoval. V případě potřeby budete muset vybrat odpovídající hodnotu pro počet řádků na stránku dat v mezipaměti. Tato hodnota je předána do `Cache` konstruktoru. Počet řádků na stránku by neměl být menší než počet řádků, které lze v <xref:System.Windows.Forms.DataGridView> ovládacím prvku současně zobrazit.  
  
 Pro dosažení nejlepších výsledků budete muset provést testování výkonu a testování použitelnosti, abyste zjistili požadavky vašeho systému i uživatelů. Mezi faktory, které budete muset vzít v úvahu, patří množství paměti v klientských počítačích, na kterých běží vaše aplikace, dostupná šířka pásma síťového připojení a latence používaného serveru. Šířka pásma a latence by měly být stanoveny v době špičky využití.  
  
 Chcete-li zlepšit výkon při posouvání aplikace, můžete zvýšit množství uložených dat v místním prostředí. Pokud ale chcete zlepšit čas spuštění, musíte se nejdřív vyhnout načtení příliš velkého množství dat. Možná budete chtít změnit `Cache` třídu, aby se zvýšil počet datových stránek, které může uložit. Použití více datových stránek může zlepšit efektivitu posouvání, ale v závislosti na dostupné šířce pásma a latenci serveru je třeba určit ideální počet řádků na datové stránce. S menšími stránkami bude k serveru k dispozici častěji, ale bude trvat kratší dobu, než budou požadovaná data vrácena. Pokud je latence větší než šířka pásma, možná budete chtít použít stránky s větším množstvím dat.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Virtuální režim v ovládacím prvku Windows Forms DataGridView](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Návod: Implementace virtuálního režimu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
- [Postupy: Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku DataGridView model Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
