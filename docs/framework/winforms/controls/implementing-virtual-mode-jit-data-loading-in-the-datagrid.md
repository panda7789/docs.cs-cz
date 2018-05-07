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
ms.openlocfilehash: ad3ec7fb2e0012459bcf597ac9abee76c20b767e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView
Jedním z důvodů implementace virtuálního režimu v <xref:System.Windows.Forms.DataGridView> ovládací prvek je k načtení dat pouze dle potřeby. To se označuje jako *načítání dat za běhu*.  
  
 Pokud pracujete s velmi velké tabulky v vzdálenou databázi, například můžete chtít vyhnout zpoždění spuštění načítání jenom data, která je potřebná pro zobrazení a načítání další data jenom v případě, že uživatel posune nové řádky do zobrazení. Pokud klientské počítače se systémem aplikaci máte omezené množství paměti k dispozici pro ukládání dat, můžete také chtít zahodit nepoužívané data při získávání nových hodnot z databáze.  
  
 Následující části popisují způsob použití <xref:System.Windows.Forms.DataGridView> ovládacího prvku s mezipamětí za běhu.  
  
 Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: Implementace virtuálního režimu s JIT načítání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="the-form"></a>Formulář  
 Následující příklad kódu definuje formulář obsahující jen pro čtení <xref:System.Windows.Forms.DataGridView> ovládací prvek, který komunikuje se službou `Cache` objektu prostřednictvím <xref:System.Windows.Forms.DataGridView.CellValueNeeded> obslužné rutiny události. `Cache` Objekt spravuje místně uložené hodnoty a používá `DataRetriever` objekt, který chcete načíst hodnoty v tabulce ukázková databáze Northwind. `DataRetriever` Objekt, který implementuje `IDataPageRetriever` rozhraní vyžaduje `Cache` třídy, se používá i k inicializaci <xref:System.Windows.Forms.DataGridView> řízení řádků a sloupců.  
  
 `IDataPageRetriever`, `DataRetriever`, A `Cache` typy jsou popsány dále v tomto tématu.  
  
> [!NOTE]
>  Ukládání citlivé informace, jako jsou hesla, v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>Rozhraní IDataPageRetriever  
 Následující příklad kódu definuje `IDataPageRetriever` rozhraní, které je implementované `DataRetriever` třídy. Jedinou metodou deklarované v toto rozhraní je `SupplyPageOfData` metodu, která vyžaduje počáteční řádek indexu a počet řádků v jediné stránce data. Tyto hodnoty jsou používány implementátor k získání podmnožiny dat z datového zdroje.  
  
 A `Cache` objekt používá implementace tohoto rozhraní během vytváření k načtení dat dvě počáteční stránek. Vždy, když je potřeba hodnotou bez vyrovnávací paměti, mezipaměti zruší jednu z těchto stránek a požaduje novou stránku obsahující hodnotu z `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>DataRetriever – třída  
 Následující příklad kódu definuje `DataRetriever` třídy, které implementuje `IDataPageRetriever` rozhraní k načtení stránky dat ze serveru. `DataRetriever` Třída rovněž poskytuje `Columns` a `RowCount` vlastnosti, které <xref:System.Windows.Forms.DataGridView> řízení používá k vytvoření nezbytných sloupců a přidat odpovídající počet prázdné řádky, které <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce. Přidání prázdné řádky je nutné, aby ovládacího prvku se bude chovat, jako kdyby obsahuje všechna data v tabulce. To znamená, že posouvací políčko posuvníku budou mít správnou velikost, a uživatel bude mít přístup k žádné řádek v tabulce. Řádky jsou vyplněny <xref:System.Windows.Forms.DataGridView.CellValueNeeded> obslužné rutiny události jenom v případě, že jsou přesunut do zobrazení oblasti.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Třída mezipaměti  
 Následující příklad kódu definuje `Cache` třída, která spravuje dvě stránky dat naplněno prostřednictvím `IDataPageRetriever` implementace. `Cache` Třída definuje vnitřní `DataPage` struktura, která obsahuje <xref:System.Data.DataTable> pro uložení hodnot v jednom mezipaměti stránky a která vypočítá indexovat řádek, který představuje horní a dolní hranice stránky.  
  
 `Cache` Třída načte dvě stránky dat v době konstrukce. Vždy, když <xref:System.Windows.Forms.DataGridView.CellValueNeeded> událostí vyžádá hodnotu, `Cache` objektu určuje, jestli je k dispozici v hodnotě jeden z jeho dvě stránky a, pokud ano, vrátí. Pokud hodnota není k dispozici místně, `Cache` objektu určuje, které z jeho dvě stránky je zcela dole aktuálně zobrazených řádků a nahradí stránce novou obsahující požadovanou hodnotu, kterou pak vrátí.  
  
 Za předpokladu, že počet řádků na stránce dat je stejný jako počet řádků, které lze zobrazit na obrazovce najednou, tento model umožňuje uživatelům stránkování prostřednictvím tabulky efektivně návrat naposledy zobrazenou stránku.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Další informace  
 Předchozí příklady kódu jsou uvedeny jako ukázka načítání dat za běhu. Potřebujete změnit kód vlastní potřebujete k dosažení maximální efektivity. Minimálně musíte vybrat odpovídající hodnotu pro počet řádků na stránce dat v mezipaměti. Tato hodnota je předán do `Cache` konstruktor. Počet řádků na stránce by měl být již menší než počet řádků, které lze zobrazit současně ve vaší <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 Nejlepších výsledků dosáhnete musíte provést testování výkonu a testování použitelnosti určit požadavky na systém a vaši uživatelé. Několik různých faktorů, které je potřeba vzít v úvahu zahrnout množství paměti do klientských počítačů, spouštění aplikace, dostupnou šířku pásma síťového připojení používá a latence serveru použít. Šířka pásma a latence se určí v některých případech využití ve špičce.  
  
 Chcete-li zlepšit výkon posouvání vaší aplikace, můžete zvýšit množství dat uložených místně. Pro zlepšení spuštění, ale musí neměli načítání příliš mnoho dat původně. Můžete chtít změnit `Cache` třída zvyšte počet datových stránek můžete uložit. Použití více stránek dat může zlepšit efektivitu posouvání, ale budete muset určit ideální počet řádků na stránce dat, v závislosti na dostupnou šířku pásma a dobu serveru. S menší stránky serveru bude přistupovat častěji, ale bude trvat méně času k vrátit požadovaná data. Pokud je latence více problém než šířky pásma, můžete použít větší datových stránek.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Virtuální režim v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [Postupy: Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
