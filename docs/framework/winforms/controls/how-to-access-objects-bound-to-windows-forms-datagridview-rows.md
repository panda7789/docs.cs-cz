---
title: Přístup k objektům připojeným k řádkům DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743164"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="4c02f-102">Postupy: Přístup k objektům připojeným k řádkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="4c02f-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="4c02f-103">Někdy je užitečné zobrazit tabulku informací uložených v kolekci obchodních objektů.</span><span class="sxs-lookup"><span data-stu-id="4c02f-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="4c02f-104">Když svážete <xref:System.Windows.Forms.DataGridView> ovládací prvek s takovou kolekcí, každá veřejná vlastnost se zobrazí ve vlastním sloupci, pokud vlastnost není označena jako průchozí pomocí <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4c02f-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="4c02f-105">Například kolekce objektů `Customer` by měla obsahovat sloupce jako **jméno** a **adresa**.</span><span class="sxs-lookup"><span data-stu-id="4c02f-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="4c02f-106">Pokud tyto objekty obsahují další informace a kód, ke kterému chcete získat přístup, můžete k ní přistupovat prostřednictvím objektů řádků.</span><span class="sxs-lookup"><span data-stu-id="4c02f-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="4c02f-107">V následujícím příkladu kódu mohou uživatelé vybrat více řádků a kliknutím na tlačítko odeslat fakturu každému z odpovídajících zákazníků.</span><span class="sxs-lookup"><span data-stu-id="4c02f-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="4c02f-108">Přístup k objektům vázaným na řádek</span><span class="sxs-lookup"><span data-stu-id="4c02f-108">To access row-bound objects</span></span>  
  
- <span data-ttu-id="4c02f-109">Použijte vlastnost <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c02f-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="4c02f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c02f-110">Example</span></span>  
 <span data-ttu-id="4c02f-111">Úplný příklad kódu zahrnuje jednoduchou implementaci `Customer` a váže <xref:System.Windows.Forms.DataGridView> na <xref:System.Collections.ArrayList> obsahující několik objektů `Customer`.</span><span class="sxs-lookup"><span data-stu-id="4c02f-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="4c02f-112">Obslužná rutina události <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.Button?displayProperty=nameWithType> musí přistupovat k objektům `Customer` prostřednictvím řádků, protože kolekce zákazníků není přístupná vně <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="4c02f-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4c02f-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4c02f-113">Compiling the Code</span></span>  
 <span data-ttu-id="4c02f-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="4c02f-114">This example requires:</span></span>  
  
- <span data-ttu-id="4c02f-115">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="4c02f-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c02f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c02f-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4c02f-117">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="4c02f-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="4c02f-118">Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="4c02f-118">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
