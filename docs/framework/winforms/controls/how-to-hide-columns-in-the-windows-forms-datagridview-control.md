---
title: Skrýt sloupce v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
ms.openlocfilehash: 7ac6ccac5c02f014d5aa629956e51675cc60fddc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736557"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ca10c-102">Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ca10c-102">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ca10c-103">Někdy budete chtít zobrazit pouze některé sloupce, které jsou k dispozici v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="ca10c-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="ca10c-104">Například můžete chtít zobrazit mzdový sloupec zaměstnanců uživatelům s přihlašovacími údaji pro správu při jejich skrývání od jiných uživatelů.</span><span class="sxs-lookup"><span data-stu-id="ca10c-104">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="ca10c-105">Alternativně můžete chtít navazovat ovládací prvek na zdroj dat, který obsahuje mnoho sloupců, pouze některé z nich chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="ca10c-105">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="ca10c-106">V takovém případě obvykle odeberete sloupce, které nemají zájem o zobrazení, a ne jejich skrytí.</span><span class="sxs-lookup"><span data-stu-id="ca10c-106">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="ca10c-107">V ovládacím prvku <xref:System.Windows.Forms.DataGridView> určuje hodnota vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> sloupce, zda je tento sloupec zobrazen.</span><span class="sxs-lookup"><span data-stu-id="ca10c-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="ca10c-108">Pro tuto úlohu se v aplikaci Visual Studio podporuje.</span><span class="sxs-lookup"><span data-stu-id="ca10c-108">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="ca10c-109">Viz také [Postupy: skrytí sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](hide-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="ca10c-109">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](hide-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="ca10c-110">Postup pro skrytí sloupce prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="ca10c-110">To hide a column programmatically</span></span>  
  
- <span data-ttu-id="ca10c-111">Vlastnost <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> nastavte na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="ca10c-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="ca10c-112">Chcete-li skrýt `CustomerID` sloupec, který je automaticky generován během vytváření datové vazby, umístěte následující příklad kódu do obslužné rutiny události <xref:System.Windows.Forms.DataGridView.DataBindingComplete>.</span><span class="sxs-lookup"><span data-stu-id="ca10c-112">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca10c-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ca10c-113">Compiling the Code</span></span>  
 <span data-ttu-id="ca10c-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ca10c-114">This example requires:</span></span>  
  
- <span data-ttu-id="ca10c-115"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`, který obsahuje sloupec s názvem `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="ca10c-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
- <span data-ttu-id="ca10c-116">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="ca10c-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca10c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca10c-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ca10c-118">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ca10c-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="ca10c-119">Postupy: Odebrání automaticky vygenerovaných sloupců z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ca10c-119">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
- [<span data-ttu-id="ca10c-120">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ca10c-120">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
