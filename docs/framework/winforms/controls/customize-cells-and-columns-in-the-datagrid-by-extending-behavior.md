---
title: "Postupy: Přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView rozšířením jeho chování a vzhledu"
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
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 358b5ed2ad201b2dfb0fef7bb960a88234939bf1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Postupy: Přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView rozšířením jeho chování a vzhledu
<xref:System.Windows.Forms.DataGridView> Řízení poskytuje několik způsobů, jak přizpůsobit její vzhled a chování pomocí vlastností události a doprovodné třídy. V některých případech mohou mít požadavky pro vaše buněk, které překračují co může poskytnout tyto funkce. Můžete vytvořit vlastní vlastní <xref:System.Windows.Forms.DataGridViewCell> třída poskytovat rozšířené funkce.  
  
 Vytvoření vlastní <xref:System.Windows.Forms.DataGridViewCell> třídy odvozené z <xref:System.Windows.Forms.DataGridViewCell> základní třídu nebo jeden z jejich odvozené třídy. I když můžete zobrazit libovolného typu buňky v jakýkoli typ sloupce, obvykle vytvoříte vlastní <xref:System.Windows.Forms.DataGridViewColumn> třída specializované pro zobrazení vašeho typu buňky. Sloupec třídy jsou odvozeny od <xref:System.Windows.Forms.DataGridViewColumn> nebo jednoho z jeho odvozených typů.  
  
 V následujícím příkladu kódu vytvoříte vlastní buňky třídy s názvem `DataGridViewRolloverCell` , zjistí, že myš zadá a opustí hranice buněk. Při přesunutí myši v rámci hranice na buňku obdélníku inset vykreslením. Tento nový typ je odvozena z <xref:System.Windows.Forms.DataGridViewTextBoxCell> a v ostatních ohledech se chová jako svou základní třídu. Je volána třída sloupec doprovodné `DataGridViewRolloverColumn`.  
  
 K použití těchto tříd, vytvořit formulář obsahující <xref:System.Windows.Forms.DataGridView> řídit, přidejte jeden nebo více `DataGridViewRolloverColumn` objekty ke <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce a naplnit ovládací prvek s řádky obsahující hodnoty.  
  
> [!NOTE]
>  Tento příklad nebude pracovat správně, pokud přidáte prázdné řádky. Prázdné řádky se vytvoření, například při přidání řádků pro ovládací prvek nastavením <xref:System.Windows.Forms.DataGridView.RowCount%2A> vlastnost. Toto je vzhledem k tomu, že řádky přidat v tomto případě jsou automaticky sdíleny, to znamená, že `DataGridViewRolloverCell` objektů nejsou vytvořena, dokud nekliknete na jednotlivých buněk a způsobuje související řádky se nesdílené.  
  
 Protože tento typ přizpůsobení buněk vyžaduje nesdílené řádky, není vhodné používat s velkých datových sad. Další informace o sdílení řádků najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
>  Pokud odvozujete od <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy, je nutné přepsat `Clone` metoda kopírování nové vlastnosti během operací klonování. Měli byste také zavolat základní třídy `Clone` metoda tak, aby vlastnosti základní třídy jsou zkopírovány do nového buňky nebo sloupec.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Přizpůsobení buněk a sloupců v ovládacím prvku DataGridView  
  
1.  Odvození novou třídu buňky, s názvem `DataGridViewRolloverCell`, z <xref:System.Windows.Forms.DataGridViewTextBoxCell> typu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2.  Přepsání <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> metoda v `DataGridViewRolloverCell` třídy. V přepsání nejdřív voláním implementace základní třídu, která zpracovává funkci hostované textové pole. Potom pomocí ovládacího prvku <xref:System.Windows.Forms.Control.PointToClient%2A> metoda pro transformaci pozice kurzoru (v souřadnice obrazovky) do <xref:System.Windows.Forms.DataGridView> souřadnice klientské oblasti. Pokud souřadnic myši spadal do hranice buňky, kreslení inset rámeček.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3.  Přepsání <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> a <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> metody v `DataGridViewRolloverCell` třída vynutit buněk překreslit sami, když ukazatel myši vstoupí do nebo je opustí.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4.  Odvození novou třídu, s názvem `DataGridViewRolloverCellColumn`, z <xref:System.Windows.Forms.DataGridViewColumn> typu. V konstruktoru, přiřadit nový `DataGridViewRolloverCell` do objektu jeho <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Příklad  
 Úplný příklad kódu obsahuje formulář malý test, který ukazuje chování typu vlastní buňky.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Windows.Forms a System.Drawing.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [Architektura ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)
