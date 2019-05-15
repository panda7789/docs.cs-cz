---
title: 'Postupy: Přístup k objektům připojeným k řádkům Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 244047f27b0eb109aba599bd26881046eb538163
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582621"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="b570d-102">Postupy: Přístup k objektům připojeným k řádkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b570d-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="b570d-103">Někdy je užitečné zobrazit tabulku informací uložených v kolekci objektů firmy.</span><span class="sxs-lookup"><span data-stu-id="b570d-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="b570d-104">Po vytvoření vazby <xref:System.Windows.Forms.DataGridView> ovládacího prvku na takové shromažďování každé veřejné vlastnosti se zobrazí v jeho vlastní sloupec, pokud vlastnost byl označen mimo-nelze procházet s <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b570d-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="b570d-105">Například kolekce `Customer` objekty, jako má sloupce **název** a **adresu**.</span><span class="sxs-lookup"><span data-stu-id="b570d-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="b570d-106">Pokud tyto objekty obsahují další informace a kód, který chcete získat přístup, můžete k němu přistoupit pomocí objektů řádek.</span><span class="sxs-lookup"><span data-stu-id="b570d-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="b570d-107">Uživatelé v následujícím příkladu kódu, můžete vybrat více řádků a klikněte na tlačítko si pošlete faktury ke každému odpovídající zákazníků.</span><span class="sxs-lookup"><span data-stu-id="b570d-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="b570d-108">Pro přístup k objektům vázané na řádek</span><span class="sxs-lookup"><span data-stu-id="b570d-108">To access row-bound objects</span></span>  
  
- <span data-ttu-id="b570d-109">Použití <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b570d-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="b570d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b570d-110">Example</span></span>  
 <span data-ttu-id="b570d-111">Příklad úplného kódu obsahuje jednoduchý `Customer` provádění a vytvoří vazbu <xref:System.Windows.Forms.DataGridView> do <xref:System.Collections.ArrayList> obsahuje několik `Customer` objekty.</span><span class="sxs-lookup"><span data-stu-id="b570d-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="b570d-112"><xref:System.Windows.Forms.Control.Click> Obslužná rutina události <xref:System.Windows.Forms.Button?displayProperty=nameWithType> musí přejít `Customer` objekty přes řádky, protože není přístupná mimo kolekci zákazníků <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b570d-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b570d-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b570d-113">Compiling the Code</span></span>  
 <span data-ttu-id="b570d-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b570d-114">This example requires:</span></span>  
  
- <span data-ttu-id="b570d-115">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b570d-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b570d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b570d-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b570d-117">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b570d-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b570d-118">Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="b570d-118">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
