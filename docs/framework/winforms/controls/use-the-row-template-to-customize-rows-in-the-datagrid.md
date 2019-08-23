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
ms.openlocfilehash: 0dba318e6aa35761f4e9471fdb13b65644747b57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966493"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="de1a0-102">Postupy: Použití šablony řádku k přizpůsobení řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="de1a0-102">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="de1a0-103">Ovládací prvek používá šablonu řádku jako základ pro všechny řádky, které přidá do ovládacího prvku buď prostřednictvím vazby dat, nebo při <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> volání metody bez určení stávajícího řádku, který má být použit. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="de1a0-103">The <xref:System.Windows.Forms.DataGridView> control uses the row template as a basis for all rows that it adds to the control either through data binding or when you call the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method without specifying an existing row to use.</span></span>  
  
 <span data-ttu-id="de1a0-104">Šablona řádku nabízí větší kontrolu nad tím, jak vzhled a chování řádků, než <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> poskytuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="de1a0-104">The row template gives you greater control over the appearance and behavior of rows than the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property provides.</span></span> <span data-ttu-id="de1a0-105">Pomocí šablony řádku můžete nastavit jakékoli <xref:System.Windows.Forms.DataGridViewRow> vlastnosti, včetně. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A></span><span class="sxs-lookup"><span data-stu-id="de1a0-105">With the row template, you can set any <xref:System.Windows.Forms.DataGridViewRow> properties, including <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span></span>  
  
 <span data-ttu-id="de1a0-106">Existují situace, kdy je nutné použít šablonu řádku k dosažení konkrétního efektu.</span><span class="sxs-lookup"><span data-stu-id="de1a0-106">There are some situations where you must use the row template to achieve a particular effect.</span></span> <span data-ttu-id="de1a0-107">Například informace o výšce řádku nelze uložit do <xref:System.Windows.Forms.DataGridViewCellStyle>, takže je nutné použít šablonu řádku, chcete-li změnit výchozí výšku použitou ve všech řádcích.</span><span class="sxs-lookup"><span data-stu-id="de1a0-107">For example, row height information cannot be stored in a <xref:System.Windows.Forms.DataGridViewCellStyle>, so you must use a row template to change the default height used by all rows.</span></span> <span data-ttu-id="de1a0-108">Šablona řádku je užitečná také v případě, že vytvoříte vlastní třídy odvozené z <xref:System.Windows.Forms.DataGridViewRow> a chcete použít vlastní typ, když jsou do ovládacího prvku přidány nové řádky.</span><span class="sxs-lookup"><span data-stu-id="de1a0-108">The row template is also useful when you create your own classes derived from <xref:System.Windows.Forms.DataGridViewRow> and you want your custom type used when new rows are added to the control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de1a0-109">Šablona řádku se používá pouze v případě, že jsou přidány řádky.</span><span class="sxs-lookup"><span data-stu-id="de1a0-109">The row template is used only when rows are added.</span></span> <span data-ttu-id="de1a0-110">Existující řádky nemůžete změnit změnou šablony řádku.</span><span class="sxs-lookup"><span data-stu-id="de1a0-110">You cannot change existing rows by changing the row template.</span></span>  
  
### <a name="to-use-the-row-template"></a><span data-ttu-id="de1a0-111">Použití šablony řádku</span><span class="sxs-lookup"><span data-stu-id="de1a0-111">To use the row template</span></span>  
  
- <span data-ttu-id="de1a0-112">Nastavte vlastnosti objektu načteného z <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="de1a0-112">Set properties on the object retrieved from the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de1a0-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="de1a0-113">Compiling the Code</span></span>  
 <span data-ttu-id="de1a0-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="de1a0-114">This example requires:</span></span>  
  
- <span data-ttu-id="de1a0-115">Ovládací prvek s `dataGridView1`názvem. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="de1a0-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="de1a0-116">Odkazy na <xref:System?displayProperty=nameWithType>sestavení, <xref:System.Drawing?displayProperty=nameWithType>a. <xref:System.Windows.Forms?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="de1a0-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de1a0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de1a0-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="de1a0-118">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="de1a0-118">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="de1a0-119">Styly buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="de1a0-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
