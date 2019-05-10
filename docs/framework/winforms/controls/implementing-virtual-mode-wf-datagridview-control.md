---
title: 'Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 9e7fb3a42b56c40f713d73e3734142f4aab335f4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649997"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView
Pokud chcete zobrazit velmi velké množství tabulková data v <xref:System.Windows.Forms.DataGridView> ovládacího prvku, lze nastavit <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true` a explicitně spravovat ovládacího prvku interakce s jeho data store. To umožňuje optimalizovat výkon ovládacího prvku v této situaci.  
  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje několik událostí, které dokáže zpracovat pro interakci s vlastním úložišti. Tento názorný postup vás provede procesem implementace těchto obslužných rutin událostí. Příklad kódu v tomto tématu používá velmi jednoduchý datový zdroj pro ilustraci. V produkčním prostředí, bude obvykle načíst pouze řádky, které potřebujete k zobrazení do mezipaměti a zpracování <xref:System.Windows.Forms.DataGridView> události komunikovat a aktualizujte mezipaměť. Další informace najdete v tématu [implementace virtuálního režimu s načítáním dat k za běhu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Implementace virtuálního režimu v Windows Forms DataGridView – ovládací prvek](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-implement-virtual-mode"></a>Implementace virtuálního režimu  
  
1. Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
     Následující kód obsahuje některé základní inicializace. Deklaruje několik proměnných, které se použijí v dalších krocích, poskytuje `Main` metoda a poskytuje jednoduchý formulář rozložení v konstruktoru třídy.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. Implementujte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Load> událost, která inicializuje <xref:System.Windows.Forms.DataGridView> řídit a naplní úložiště dat pomocí ukázkové hodnoty.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellValueNeeded> událost, která načte požadované její hodnotu z úložiště dat nebo `Customer` objekt aktuálně v režimu úpravy.  
  
     Vždy, když dojde k této události <xref:System.Windows.Forms.DataGridView> ovládací prvek musí Vymalovat buňky.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellValuePushed> událost, která ukládá hodnotu upravených buňky v `Customer` objekt představující upravený řádku. K této události dojde pokaždé, když se uživatel potvrdí změnu hodnoty buňky.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.NewRowNeeded> událost, která vytvoří nový `Customer` objekt představující nově vytvořený řádek.  
  
     Pokaždé, když uživatel zadá řádek pro nové záznamy, dojde k této události.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.RowValidated> událost, která se uloží do úložiště dat nové nebo upravené řádky.  
  
     K této události dojde pokaždé, když uživatel změní na aktuálním řádku.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> událost, která označuje, zda <xref:System.Windows.Forms.DataGridView.CancelRowEdit> dojde k události, když uživatel signály řádek reverzi stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režim úprav.  
  
     Ve výchozím nastavení <xref:System.Windows.Forms.DataGridView.CancelRowEdit> nastane všechny buňky v aktuálním řádku se změnilo, není-li na řádku reverzi <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> je nastavena na `true` v <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obslužné rutiny události. Tato událost je užitečná při potvrzení oboru je stanovena v době běhu.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CancelRowEdit> událost, která zruší hodnoty `Customer` objekt představující aktuální řádek.  
  
     Tato událost nastane, pokud uživatel signály řádek reverzi stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režim úprav. Tato událost nedojde, pokud byly změněny žádné buňky v aktuálním řádku, nebo pokud hodnota <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> je nastavená vlastnost `false` v <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obslužné rutiny události.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.UserDeletingRow> událost, která odstraní existující `Customer` objektu z úložiště dat nebo zruší neuloženými `Customer` objekt představující nově vytvořený řádek.  
  
     K této události dojde pokaždé, když uživatel odstraní řádek kliknutím na záhlaví řádku a stisknutím klávesy DELETE.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Implementujte jednoduchou `Customers` pro reprezentaci datových položek, které používá tento příklad kódu.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>K otestování formuláře  
  
- Kompilace a spuštění aplikace.  
  
     Zobrazí se <xref:System.Windows.Forms.DataGridView> ovládací prvek vyplní tři záznamy o zákaznících. Můžete změnit hodnoty několika buňkami v řádku a stisknutím klávesy ESC dvakrát v režimu úprav a jednou mimo režim úprav, vrátí se celý řádek na jeho původní hodnoty. Když upravíte, přidání nebo odstranění řádků v ovládacím prvku `Customer` úpravou, přidány nebo odstraněny také objekty v úložišti dat.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace získáte základní znalosti o události, je třeba ošetřit implementace virtuálního režimu v <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Můžete vylepšit tuto základní aplikaci v několika způsoby:  
  
- Implementace úložiště dat, která ukládá do mezipaměti hodnoty z externí databáze. Mezipaměti by měla načíst a zahodit hodnoty podle potřeby tak, aby obsahoval pouze co je třeba pro zobrazení při spotřebě malé množství paměti v klientském počítači.  
  
- Optimalizovat výkon úložiště dat podle vašich potřeb. Můžete například chtít kompenzovat pomalé síťové připojení, spíše než omezení paměti klientského počítače pomocí větší velikost mezipaměti a současně minimalizuje počet databázových dotazů.  
  
 Další informace o ukládání do mezipaměti hodnoty z externí databáze najdete v tématu [jak: Implementace virtuálního režimu s načítáním dat za běhu v Windows Forms DataGridView – ovládací prvek](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="see-also"></a>Viz také:

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
