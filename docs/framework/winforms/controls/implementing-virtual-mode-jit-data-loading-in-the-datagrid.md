---
title: Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku DataGridView
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
ms.openlocfilehash: 85c6877a9fc6a92752eb039da9d36e34811f8b77
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745065"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView
Jedním z důvodů implementace virtuálního režimu v ovládacím prvku <xref:System.Windows.Forms.DataGridView> je načíst data pouze tak, jak je potřeba. Tato metoda se označuje jako *načítání dat za běhu*.  
  
 Pokud pracujete s velmi velkou tabulkou ve vzdálené databázi, například můžete chtít zabránit prodlevám při spouštění, a to tak, že načtete jenom data potřebná pro zobrazení a načítání dalších dat, jenom když uživatel posune nové řádky do zobrazení. Pokud klientské počítače, na kterých běží vaše aplikace, mají k dispozici omezené množství paměti pro ukládání dat, možná budete chtít při načítání nových hodnot z databáze zrušit nepoužívaná data.  
  
 Následující části popisují způsob použití <xref:System.Windows.Forms.DataGridView>ho ovládacího prvku s mezipamětí za běhu.  
  
 Chcete-li zkopírovat kód v tomto tématu jako jediný výpis, přečtěte si téma [How to: implementovat virtuální režim s daty za běhu v ovládacím prvku DataGridView model Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="the-form"></a>Formulář  
 Následující příklad kódu definuje formulář obsahující ovládací prvek <xref:System.Windows.Forms.DataGridView> jen pro čtení, který komunikuje s objektem `Cache` prostřednictvím obslužné rutiny události <xref:System.Windows.Forms.DataGridView.CellValueNeeded>. Objekt `Cache` spravuje místně uložené hodnoty a pomocí objektu `DataRetriever` načítá hodnoty z tabulky Orders ukázkové databáze Northwind. Objekt `DataRetriever`, který implementuje rozhraní `IDataPageRetriever` vyžadované třídou `Cache`, se používá také k inicializaci řádků a sloupců ovládacího prvku <xref:System.Windows.Forms.DataGridView>.  
  
 Typy `IDataPageRetriever`, `DataRetriever`a `Cache` jsou popsány dále v tomto tématu.  
  
> [!NOTE]
> Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>Rozhraní IDataPageRetriever  
 Následující příklad kódu definuje rozhraní `IDataPageRetriever`, které je implementováno třídou `DataRetriever`. Jedinou metodou deklarovanou v tomto rozhraní je `SupplyPageOfData` metoda, která vyžaduje počáteční index řádku a počet řádků na jedné stránce dat. Tyto hodnoty používá implementátor k načtení podmnožiny dat ze zdroje dat.  
  
 Objekt `Cache` používá implementaci tohoto rozhraní během konstrukce pro načtení dvou počátečních stránek dat. Pokaždé, když je potřebná hodnota bez mezipaměti, mezipaměť odhodí jednu z těchto stránek a požádá o novou stránku obsahující hodnotu z `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>Třída  
 Následující příklad kódu definuje třídu `DataRetriever`, která implementuje rozhraní `IDataPageRetriever`, aby načetla stránky dat ze serveru. Třída `DataRetriever` také poskytuje `Columns` a `RowCount` vlastnosti, které ovládací prvek <xref:System.Windows.Forms.DataGridView> používá k vytvoření nezbytných sloupců a k přidání příslušného počtu prázdných řádků do kolekce <xref:System.Windows.Forms.DataGridView.Rows%2A>. Přidání prázdných řádků je nezbytné, aby se ovládací prvek choval, jako by obsahoval všechna data v tabulce. To znamená, že okno posuvníku v posuvníku bude mít odpovídající velikost a uživatel bude mít přístup k jakémukoli řádku v tabulce. Řádky jsou vyplněny <xref:System.Windows.Forms.DataGridView.CellValueNeeded> obslužné rutiny události pouze v případě, že jsou posunuty do zobrazení.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Třída cache  
 Následující příklad kódu definuje třídu `Cache`, která spravuje dvě stránky dat vyplněné pomocí `IDataPageRetriever` implementace. Třída `Cache` definuje vnitřní `DataPage` strukturu, která obsahuje <xref:System.Data.DataTable> pro uložení hodnot na jednu stránku mezipaměti a která vypočítá indexy řádků reprezentující horní a dolní hranice stránky.  
  
 Třída `Cache` načte dvě stránky dat v době konstrukce. Kdykoli událost <xref:System.Windows.Forms.DataGridView.CellValueNeeded> požádá o hodnotu, objekt `Cache` určuje, zda je hodnota k dispozici na jedné z jejích dvou stránek, a pokud ano, vrátí ji. Pokud tato hodnota není k dispozici místně, objekt `Cache` určuje, který z jeho dvou stránek je nejvzdálenější z aktuálně zobrazených řádků, a nahradí stránku novým, který obsahuje požadovanou hodnotu, kterou pak vrátí.  
  
 Za předpokladu, že počet řádků na datové stránce je stejný jako počet řádků, které je možné na obrazovce zobrazit najednou, umožňuje tento model stránkování přes tabulku a efektivně se vracet na naposledy prohlíženou stránku.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Další požadavky  
 Předchozí příklady kódu jsou k dispozici jako ukázka načítání dat za běhu. Abyste dosáhli maximální efektivity, budete muset změnit kód tak, aby vyhovoval. V případě potřeby budete muset vybrat odpovídající hodnotu pro počet řádků na stránku dat v mezipaměti. Tato hodnota je předána do konstruktoru `Cache`. Počet řádků na stránku by neměl být menší než počet řádků, které lze zobrazit současně v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.  
  
 Pro dosažení nejlepších výsledků budete muset provést testování výkonu a testování použitelnosti, abyste zjistili požadavky vašeho systému i uživatelů. Mezi faktory, které budete muset vzít v úvahu, patří množství paměti v klientských počítačích, na kterých běží vaše aplikace, dostupná šířka pásma síťového připojení a latence používaného serveru. Šířka pásma a latence by měly být stanoveny v době špičky využití.  
  
 Chcete-li zlepšit výkon při posouvání aplikace, můžete zvýšit množství uložených dat v místním prostředí. Pokud ale chcete zlepšit čas spuštění, musíte se nejdřív vyhnout načtení příliš velkého množství dat. Možná budete chtít upravit třídu `Cache`, aby se zvýšil počet datových stránek, které může uložit. Použití více datových stránek může zlepšit efektivitu posouvání, ale v závislosti na dostupné šířce pásma a latenci serveru je třeba určit ideální počet řádků na datové stránce. S menšími stránkami bude k serveru k dispozici častěji, ale bude trvat kratší dobu, než budou požadovaná data vrácena. Pokud je latence větší než šířka pásma, možná budete chtít použít stránky s větším množstvím dat.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Virtuální režim v ovládacím prvku Windows Forms DataGridView](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-wf-datagridview-control.md)
- [Postupy: Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
