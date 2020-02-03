---
title: Zakázání tlačítek ve sloupci tlačítka v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 691781a43005d66e13029ab8110eb7f9daacc35f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745945"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7c74f-102">Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7c74f-102">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7c74f-103">Ovládací prvek <xref:System.Windows.Forms.DataGridView> obsahuje třídu <xref:System.Windows.Forms.DataGridViewButtonCell> pro zobrazení buněk s uživatelským rozhraním (UI) jako tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7c74f-103">The <xref:System.Windows.Forms.DataGridView> control includes the <xref:System.Windows.Forms.DataGridViewButtonCell> class for displaying cells with a user interface (UI) like a button.</span></span> <span data-ttu-id="7c74f-104"><xref:System.Windows.Forms.DataGridViewButtonCell> ale neposkytuje způsob, jak zakázat vzhled tlačítka zobrazovaného buňkou.</span><span class="sxs-lookup"><span data-stu-id="7c74f-104">However, <xref:System.Windows.Forms.DataGridViewButtonCell> does not provide a way to disable the appearance of the button displayed by the cell.</span></span>  
  
 <span data-ttu-id="7c74f-105">Následující příklad kódu ukazuje, jak přizpůsobit třídu <xref:System.Windows.Forms.DataGridViewButtonCell> pro zobrazení tlačítek, která se mohou zobrazit zakázané.</span><span class="sxs-lookup"><span data-stu-id="7c74f-105">The following code example demonstrates how to customize the <xref:System.Windows.Forms.DataGridViewButtonCell> class to display buttons that can appear disabled.</span></span> <span data-ttu-id="7c74f-106">Příklad definuje nový typ buňky `DataGridViewDisableButtonCell`, který je odvozen z <xref:System.Windows.Forms.DataGridViewButtonCell>.</span><span class="sxs-lookup"><span data-stu-id="7c74f-106">The example defines a new cell type, `DataGridViewDisableButtonCell`, that derives from <xref:System.Windows.Forms.DataGridViewButtonCell>.</span></span> <span data-ttu-id="7c74f-107">Tento typ buňky poskytuje novou vlastnost `Enabled`, kterou lze nastavit tak, aby `false` vykreslila zakázané tlačítko v buňce.</span><span class="sxs-lookup"><span data-stu-id="7c74f-107">This cell type provides a new `Enabled` property that can be set to `false` to draw a disabled button in the cell.</span></span> <span data-ttu-id="7c74f-108">V příkladu je také definován nový typ sloupce `DataGridViewDisableButtonColumn`, který zobrazí `DataGridViewDisableButtonCell` objekty.</span><span class="sxs-lookup"><span data-stu-id="7c74f-108">The example also defines a new column type, `DataGridViewDisableButtonColumn`, that displays `DataGridViewDisableButtonCell` objects.</span></span> <span data-ttu-id="7c74f-109">Chcete-li Ukázat tento nový typ buňky a sloupce, aktuální hodnota každé <xref:System.Windows.Forms.DataGridViewCheckBoxCell> v nadřazené <xref:System.Windows.Forms.DataGridView> určuje, zda je vlastnost `Enabled` `DataGridViewDisableButtonCell` na stejném řádku `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="7c74f-109">To demonstrate this new cell and column type, the current value of each <xref:System.Windows.Forms.DataGridViewCheckBoxCell> in the parent <xref:System.Windows.Forms.DataGridView> determines whether the `Enabled` property of the `DataGridViewDisableButtonCell` in the same row is `true` or `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c74f-110">Při odvozování z <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností do odvozené třídy nezapomeňte přepsat metodu `Clone` pro kopírování nových vlastností během operací klonování.</span><span class="sxs-lookup"><span data-stu-id="7c74f-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="7c74f-111">Měli byste také zavolat metodu `Clone` základní třídy tak, aby byly vlastnosti základní třídy zkopírovány do nové buňky nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="7c74f-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c74f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c74f-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c74f-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7c74f-113">Compiling the Code</span></span>  
 <span data-ttu-id="7c74f-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7c74f-114">This example requires:</span></span>  
  
- <span data-ttu-id="7c74f-115">Odkazy na sestavení System, System. Drawing, System. Windows. Forms a System. Windows. Forms. VisualStyles.</span><span class="sxs-lookup"><span data-stu-id="7c74f-115">References to the System, System.Drawing, System.Windows.Forms and System.Windows.Forms.VisualStyles assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c74f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c74f-116">See also</span></span>

- [<span data-ttu-id="7c74f-117">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7c74f-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7c74f-118">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="7c74f-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="7c74f-119">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="7c74f-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
