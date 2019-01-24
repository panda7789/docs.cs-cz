---
title: 'Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 215b04ce47a393a0ec3ad01957a311bc5508d24f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580236"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7e4b1-102">Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7e4b1-102">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7e4b1-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek používá šablony řádku jako základ pro všechny řádky, které se přidá do ovládacího prvku prostřednictvím datové vazby nebo při volání <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> metoda bez zadání používat stávající řádek.</span><span class="sxs-lookup"><span data-stu-id="7e4b1-103">The <xref:System.Windows.Forms.DataGridView> control uses the row template as a basis for all rows that it adds to the control either through data binding or when you call the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method without specifying an existing row to use.</span></span>  
  
 <span data-ttu-id="7e4b1-104">Šablony řádku vám dává větší kontrolu nad vzhled a chování řádků, než <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> poskytuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7e4b1-104">The row template gives you greater control over the appearance and behavior of rows than the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property provides.</span></span> <span data-ttu-id="7e4b1-105">Pomocí šablony řádek, můžete nastavit některé <xref:System.Windows.Forms.DataGridViewRow> vlastnosti, včetně <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e4b1-105">With the row template, you can set any <xref:System.Windows.Forms.DataGridViewRow> properties, including <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span></span>  
  
 <span data-ttu-id="7e4b1-106">Existují určité situace, kdy je nutné použít šablony řádku k dosažení určitého efektu.</span><span class="sxs-lookup"><span data-stu-id="7e4b1-106">There are some situations where you must use the row template to achieve a particular effect.</span></span> <span data-ttu-id="7e4b1-107">Například nelze uložit informace výšky řádku v <xref:System.Windows.Forms.DataGridViewCellStyle>, takže musíte použít šablonu řádku Chcete-li změnit výchozí výška používají všechny řádky.</span><span class="sxs-lookup"><span data-stu-id="7e4b1-107">For example, row height information cannot be stored in a <xref:System.Windows.Forms.DataGridViewCellStyle>, so you must use a row template to change the default height used by all rows.</span></span> <span data-ttu-id="7e4b1-108">Šablony řádku je užitečné také při vytváření vlastní třídy odvozené od <xref:System.Windows.Forms.DataGridViewRow> a chcete, aby vaše vlastní typ použitý při přidání nových řádků do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7e4b1-108">The row template is also useful when you create your own classes derived from <xref:System.Windows.Forms.DataGridViewRow> and you want your custom type used when new rows are added to the control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e4b1-109">Řádek šablona se používá, pouze když jsou řádky přidány.</span><span class="sxs-lookup"><span data-stu-id="7e4b1-109">The row template is used only when rows are added.</span></span> <span data-ttu-id="7e4b1-110">Existující řádky nelze změnit tak, že změníte šablony řádku.</span><span class="sxs-lookup"><span data-stu-id="7e4b1-110">You cannot change existing rows by changing the row template.</span></span>  
  
### <a name="to-use-the-row-template"></a><span data-ttu-id="7e4b1-111">Použití šablony řádku</span><span class="sxs-lookup"><span data-stu-id="7e4b1-111">To use the row template</span></span>  
  
-   <span data-ttu-id="7e4b1-112">Nastavit vlastnosti v objektu načtený ze <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7e4b1-112">Set properties on the object retrieved from the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e4b1-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7e4b1-113">Compiling the Code</span></span>  
 <span data-ttu-id="7e4b1-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7e4b1-114">This example requires:</span></span>  
  
-   <span data-ttu-id="7e4b1-115">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="7e4b1-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="7e4b1-116">Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="7e4b1-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e4b1-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e4b1-117">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7e4b1-118">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7e4b1-118">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7e4b1-119">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7e4b1-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
