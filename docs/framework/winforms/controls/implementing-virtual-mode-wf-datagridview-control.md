---
title: "Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31806d3ed13776e26634914b48bc887297ea4dab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView
Pokud chcete zobrazit velmi velké množství tabulková data v <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete nastavit <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true` a explicitně správě ovládacího prvku interakce s své datové úložiště. Díky tomu můžete vyladit výkon ovládacího prvku v této situaci.  
  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek obsahuje několik událostí, které může zpracovat komunikovat s úložištěm vlastní data. Tento postup vás provede procesem implementace těchto obslužných rutin událostí. Příklad kódu v tomto tématu používá velmi jednoduché datové zdroje pro účely obrázku. V produkčním prostředí, bude obvykle načíst jenom na řádky, které je třeba zobrazit do mezipaměti a zpracování <xref:System.Windows.Forms.DataGridView> události a interakci s aktualizace mezipaměti. Další informace najdete v tématu [implementace virtuálního režimu s JIT načítání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Vytvoření formuláře  
  
#### <a name="to-implement-virtual-mode"></a>Implementace virtuálního režimu  
  
1.  Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
     Následující kód obsahuje některé základní inicializace. Ho deklaruje některé proměnné, které se použijí v dalších krocích, poskytuje `Main` metoda a poskytuje základní rozložení v konstruktoru třídy.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  Implementujte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Form.Load> událost, která inicializuje <xref:System.Windows.Forms.DataGridView> řízení a naplní úložiště dat s ukázkové hodnoty.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellValueNeeded> událost, která načte hodnoty požadované buněk z úložiště dat nebo `Customer` objekt právě upravit.  
  
     Vždy, když dojde k této události <xref:System.Windows.Forms.DataGridView> ovládací prvek vyžaduje k vyplnění buňku.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellValuePushed> událost, která ukládá hodnotu upravená buňky v `Customer` objekt reprezentující upravená řádek. K této události dojde vždy, když uživatel provede změnu hodnoty buňky.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.NewRowNeeded> událost, která vytvoří novou `Customer` objekt reprezentující nově vytvořený řádek.  
  
     K této události dojde vždy, když uživatel zadá řádek pro nové záznamy.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.RowValidated> událost, která se uloží do úložiště dat nové nebo upravené řádky.  
  
     K této události dojde vždy, když uživatel změní na aktuálním řádku.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> událost, která určuje, zda <xref:System.Windows.Forms.DataGridView.CancelRowEdit> událostí se stane, když uživatel signály řádek reverzním stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režimu úprav.  
  
     Ve výchozím nastavení <xref:System.Windows.Forms.DataGridView.CancelRowEdit> nastane při reverzním řádek, když byly změněny žádné buňky na aktuálním řádku, pokud <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> je nastavena na `true` v <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obslužné rutiny události. Tato událost je užitečné, když v době běhu je určen oboru potvrzení.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CancelRowEdit> událost, která zruší hodnoty `Customer` objektu, který představuje aktuální řádek.  
  
     K této události dojde, když uživatel signály řádek reverzním stisknutím klávesy ESC dvakrát v režimu úprav nebo jednou mimo režimu úprav. Tato událost nedojde, pokud byly změněny žádné buněk na aktuálním řádku nebo pokud hodnota <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> vlastnost byla nastavena na `false` v <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> obslužné rutiny události.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Implementujte obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.UserDeletingRow> událostí, které odstraní existující `Customer` objekt z úložiště dat nebo zahodí neuložené `Customer` objekt reprezentující nově vytvořený řádek.  
  
     K této události dojde vždy, když uživatel odstraní řádek kliknutím na záhlaví řádku a stisknutím klávesy odstranit.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Implementace jednoduchou `Customers` třída představující datové položky používá tento příklad kódu.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Nyní můžete otestovat formuláře a ujistěte se, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>Postup testování formuláře  
  
-   Zkompilování a spuštění aplikace.  
  
     Zobrazí se <xref:System.Windows.Forms.DataGridView> řízení naplní tři záznamy o zákaznících. Můžete upravit hodnoty několika buňkami v řádku a stisknutím klávesy ESC dvakrát v režimu úprav a jednou mimo režimu úprav se obnovit celý řádek na jeho původní hodnoty. Když změníte, přidat nebo odstranit řádky v ovládacím prvku `Customer` upravit, přidány nebo odstraněny také objekty v úložišti dat.  
  
## <a name="next-steps"></a>Další kroky  
 Tato aplikace získáte základní znalosti o události, je nutné zpracovat implementace virtuálního režimu v <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Můžete zvýšit tuto základní aplikaci v mnoha různými způsoby:  
  
-   Implementace úložiště dat, který ukládá do mezipaměti hodnoty z externí databáze. Mezipaměť musí načíst a zahodit hodnoty podle potřeby tak, aby obsahoval pouze co je nezbytné pro zobrazení při spotřebě malé množství paměti na klientském počítači.  
  
-   Optimalizovat výkon úložiště dat v závislosti na vaše požadavky. Například můžete chtít kompenzovat pomalé síťové připojení spíš než omezení paměti klientského počítače pomocí větší velikost mezipaměti a současně minimalizuje počet databázové dotazy.  
  
 Další informace o ukládání do mezipaměti hodnoty z externí databáze najdete v tématu [postupy: Implementace virtuálního režimu s JIT načítání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [Ladění výkonu v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Implementace virtuálního režimu s načítáním v ovládacím prvku Windows Forms DataGridView dat za běhu](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [Postupy: Implementace virtuálního režimu v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
