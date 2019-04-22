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
ms.openlocfilehash: 641db19cc6493a20c9f9a34622f466e3623c32ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088649"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView
Jedním z důvodů implementace virtuálního režimu v <xref:System.Windows.Forms.DataGridView> je ovládací prvek k načtení dat pouze dle potřeby. Tento postup se nazývá *načítání dat just-in-time*.  
  
 Pokud pracujete s velmi velké tabulky do vzdálené databáze, například můžete chtít vyhnuli prodlevám při spuštění načítá pouze data, která je nezbytná pro zobrazení a načítají se další data pouze v případě, že uživatel posune nových řádků do zobrazení. Pokud klientské počítače se systémem vaší aplikace máte omezené množství paměti k ukládání dat, můžete také zrušit nepoužívaná data při načtení nové hodnoty z databáze.  
  
 Následující části popisují způsob použití <xref:System.Windows.Forms.DataGridView> ovládacího prvku s mezipamětí just-in-time.  
  
 Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Implementace virtuálního režimu s načítáním dat za běhu v Windows Forms DataGridView – ovládací prvek](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="the-form"></a>Formulář  
 Následující příklad kódu definuje formulář obsahující jen pro čtení <xref:System.Windows.Forms.DataGridView> ovládací prvek, který komunikuje `Cache` objektu <xref:System.Windows.Forms.DataGridView.CellValueNeeded> obslužné rutiny události. `Cache` Objekt spravuje místně uložené hodnoty a používá `DataRetriever` objektu k načtení hodnoty v tabulce objednávky v ukázkové databázi Northwind. `DataRetriever` Objektu, který implementuje `IDataPageRetriever` rozhraní vyžadované `Cache` třídy, slouží k inicializaci <xref:System.Windows.Forms.DataGridView> řídit řádků a sloupců.  
  
 `IDataPageRetriever`, `DataRetriever`, A `Cache` typy jsou popsány dále v tomto tématu.  
  
> [!NOTE]
>  Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>Rozhraní IDataPageRetriever  
 Následující příklad kódu definuje `IDataPageRetriever` rozhraní, které je implementované `DataRetriever` třídy. Pouze metody deklarované v tomto rozhraní je `SupplyPageOfData` metodu, která vyžaduje počáteční řádek indexu a počet řádků v jediné stránce data. Tyto hodnoty jsou používány implementátora načíst podmnožinu dat z datového zdroje.  
  
 A `Cache` objektu používá k načtení dat dvě počáteční stránky implementace tohoto rozhraní během konstrukce. Pokaždé, když se potřeby bez vyrovnávací paměti hodnotu mezipaměti odstraní jednu z těchto stránek a požádá o novou stránku obsahující hodnotu z `IDataPageRetriever`.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>Třída DataRetriever  
 Následující příklad kódu definuje `DataRetriever` třídy, která implementuje `IDataPageRetriever` rozhraní pro načtení stránek ze serveru. `DataRetriever` Třída rovněž poskytuje `Columns` a `RowCount` vlastnosti, které <xref:System.Windows.Forms.DataGridView> ovládací prvek používá k vytvoření potřebných sloupců a přidejte odpovídající počet prázdných řádků do <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce. Přidání prázdných řádků je nezbytné, aby ovládací prvek se bude chovat, jako by šlo obsahuje všechna data v tabulce. To znamená, že jezdce do oblasti posuvníku bude mít odpovídající velikost, a uživatel bude mít přístup všechny řádky v tabulce. Řádky jsou vyplněny <xref:System.Windows.Forms.DataGridView.CellValueNeeded> obslužné rutiny události pouze v případě, že jsou přešli do zobrazení.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Třída Cache  
 Následující příklad kódu definuje `Cache` třídu, která spravuje dvě stránky vyplní pomocí dat `IDataPageRetriever` implementace. `Cache` Třída definuje vnitřního `DataPage` struktura, která obsahuje <xref:System.Data.DataTable> pro uložení hodnot v jedné mezipaměti stránky a která vypočítá řádku indexy, které představují horní a dolní hranice stránky.  
  
 `Cache` Třídy načte dvě stránky dat v době konstrukce. Pokaždé, když <xref:System.Windows.Forms.DataGridView.CellValueNeeded> události vyžádá hodnotu, `Cache` objekt určuje, zda hodnota je k dispozici v jednu jeho dvou stránky a, pokud ano, vrátí jej. Pokud hodnota není k dispozici místně, `Cache` objekt určuje jeho dvě stránky nejvzdálenější aktuálně zobrazené řádky a nahradí obsahující požadovanou hodnotu, která pak vrátí novou stránku.  
  
 Za předpokladu, že počet řádků na stránce dat je stejný jako počet řádků, které se dají zobrazit na obrazovce najednou, tento model umožňuje uživatelům procházení tabulky efektivně vrátit k naposledy zobrazené stránky.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Další informace  
 Předchozí příklady kódu slouží jako ukázka načítání dat just-in-time. Je potřeba upravit kód pro vaše konkrétní potřeby k dosažení maximální efektivity. Minimálně je potřeba vybrat odpovídající hodnotu pro počet řádků na stránce dat v mezipaměti. Tato hodnota je předána do `Cache` konstruktoru. Počet řádků na stránce by měl být méně než počet řádků, které se dají zobrazit najednou v vaše <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 Nejlepších výsledků dosáhnete je potřeba provést testování výkonu a testování k určení požadavků na systém a vaši uživatelé. Několik faktorů, které je potřeba vzít v úvahu zahrnují množství paměti v počítačích klienta aplikace, dostupnou šířku pásma připojení k síti použít a latence serveru použít. Na šířku pásma a čekací doba byste měli určit čas od času využití ve špičce.  
  
 Kvůli zvýšení výkonu posunování prvku vaše aplikace se může zvýšit množství dat uložených místně. K vylepšení doby spouštění, ale je třeba se vyvarovat načítání příliš mnoho dat původně. Můžete chtít změnit `Cache` třídy zvýšit počet stránek data můžete ukládat. Použití více stránek data může zlepšit efektivitu posouvání, ale budete muset zjistit ideální počet řádků na stránce dat, v závislosti na dostupnou šířku pásma a latence serveru. S menší stránky serveru budete přistupovat častěji, ale bude trvat kratší dobu vrací požadovaná data. Pokud je latence větší potíže než šířka pásma, můžete chtít použít větší data stránky.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Virtuální režim v ovládacím prvku Windows Forms DataGridView](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-wf-datagridview-control.md)
- [Postupy: Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
