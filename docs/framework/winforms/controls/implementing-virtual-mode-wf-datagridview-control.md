---
title: 'Návod: implementace virtuálního režimu v ovládacím prvku DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 5db97b321238bc371c94e627a387bd83ca31b58a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746526"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView
Pokud chcete zobrazit velmi velké množství tabulkových dat v ovládacím prvku <xref:System.Windows.Forms.DataGridView>, můžete nastavit vlastnost <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> na `true` a explicitně spravovat interakci ovládacího prvku s jeho úložištěm dat. To vám umožní doladit výkon ovládacího prvku v této situaci.  
  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje několik událostí, které můžete zpracovat pro interakci s vlastním úložištěm dat. Tento návod vás provede procesem implementace těchto obslužných rutin událostí. Příklad kódu v tomto tématu používá velmi jednoduchý zdroj dat pro ilustrační účely. V produkčním nastavení obvykle nahrajete pouze ty řádky, které potřebujete k zobrazení do mezipaměti, a zpracovávat <xref:System.Windows.Forms.DataGridView> události pro interakci s mezipamětí a její aktualizaci. Další informace naleznete v tématu [implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md) .  
  
 Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [How to: Implementing Virtual Mode v ovládacím prvku DataGridView model Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-implement-virtual-mode"></a>Implementace virtuálního režimu  
  
1. Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView>.  
  
     Následující kód obsahuje základní inicializaci. Deklaruje některé proměnné, které budou použity v pozdějších krocích, poskytuje metodu `Main` a poskytuje jednoduché rozložení formuláře v konstruktoru třídy.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.Form.Load> formuláře, která inicializuje ovládací prvek <xref:System.Windows.Forms.DataGridView> a naplní úložiště dat vzorovými hodnotami.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.CellValueNeeded>, která načte požadovanou hodnotu buňky z úložiště dat nebo objekt `Customer`, který je právě v úpravách.  
  
     Tato událost nastane vždy, když ovládací prvek <xref:System.Windows.Forms.DataGridView> potřebuje vykreslit buňku.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.CellValuePushed>, která ukládá upravenou hodnotu buňky do objektu `Customer` představujícího upravený řádek. Tato událost nastane vždy, když uživatel potvrdí změnu hodnoty buňky.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.NewRowNeeded>, která vytvoří nový objekt `Customer` reprezentující nově vytvořený řádek.  
  
     Tato událost nastane vždy, když uživatel zadá řádek pro nové záznamy.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.RowValidated>, která ukládá nové nebo upravené řádky do úložiště dat.  
  
     Tato událost nastane vždy, když uživatel změní aktuální řádek.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>, která označuje, jestli k události <xref:System.Windows.Forms.DataGridView.CancelRowEdit> dojde, když uživatel signalizuje novou verzi řádku stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režim úprav.  
  
     Ve výchozím nastavení se <xref:System.Windows.Forms.DataGridView.CancelRowEdit> vyskytne při změně verze řádku, pokud jsou všechny buňky v aktuálním řádku změněny, pokud není vlastnost <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> v obslužné rutině události <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> nastavená na `true`. Tato událost je užitečná v případě, že je v době běhu určen rozsah potvrzení.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.CancelRowEdit>, která zahodí hodnoty objektu `Customer` představující aktuální řádek.  
  
     K této události dojde, když uživatel signalizuje opakovanou verzi řádku stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režim úprav. Tato událost nenastane, pokud nebyly změněny žádné buňky na aktuálním řádku nebo pokud byla hodnota vlastnosti <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> nastavena na `false` v obslužné rutině události <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.DataGridView.UserDeletingRow>, která odstraní existující objekt `Customer` z úložiště dat, nebo zahodí neuložený objekt `Customer` reprezentující nově vytvořený řádek.  
  
     Tato událost nastane vždy, když uživatel odstraní řádek kliknutím na záhlaví řádku a stisknutím klávesy DELETE.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Implementujte jednoduchou `Customers` třídu, která představuje datové položky používané v tomto příkladu kódu.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>Testování formuláře  
  
- Zkompilujte a spusťte aplikaci.  
  
     Zobrazí se ovládací prvek <xref:System.Windows.Forms.DataGridView> naplněný třemi záznamy zákazníků. Můžete upravit hodnoty více buněk v řádku a stisknout klávesu ESC dvakrát v režimu úprav a jednou mimo režim úprav a vrátit celý řádek do jeho původních hodnot. Když v ovládacím prvku upravíte, přidáte nebo odstraníte řádky, `Customer` objekty v úložišti dat se také upravují, přidávají nebo odstraňují.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace vám poskytne základní informace o událostech, které je nutné zpracovat k implementaci virtuálního režimu v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Tuto základní aplikaci můžete vylepšit několika způsoby:  
  
- Implementujte úložiště dat, které ukládá hodnoty do mezipaměti z externí databáze. Mezipaměť by měla podle potřeby načítat a zahodit hodnoty, aby obsahovala pouze to, co je potřeba k zobrazení a spotřebovávání malého množství paměti v klientském počítači.  
  
- Vyladění výkonu úložiště dat v závislosti na vašich požadavcích. Například může být vhodné kompenzovat pomalá síťová připojení místo omezení paměti klientského počítače pomocí větší velikosti mezipaměti a minimalizace počtu databázových dotazů.  
  
 Další informace o ukládání hodnot do mezipaměti z externí databáze naleznete v tématu [How to: Implementing Virtual Mode with just-in-time načítání dat v ovládacím prvku model Windows Forms DataGridView](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [Postupy: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
