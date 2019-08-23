---
title: 'Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: b8bb503186e41c682b0685e4c9c4bf0bb3adcbe8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967387"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="eafea-102">Postupy: Zákaz tlačítek ve sloupci tlačítek v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="eafea-102">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="eafea-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek <xref:System.Windows.Forms.DataGridViewButtonCell> obsahuje třídu pro zobrazení buněk s uživatelským rozhraním (UI) jako tlačítko.</span><span class="sxs-lookup"><span data-stu-id="eafea-103">The <xref:System.Windows.Forms.DataGridView> control includes the <xref:System.Windows.Forms.DataGridViewButtonCell> class for displaying cells with a user interface (UI) like a button.</span></span> <span data-ttu-id="eafea-104"><xref:System.Windows.Forms.DataGridViewButtonCell> Ale neposkytuje způsob, jak zakázat vzhled tlačítka zobrazovaného buňkou.</span><span class="sxs-lookup"><span data-stu-id="eafea-104">However, <xref:System.Windows.Forms.DataGridViewButtonCell> does not provide a way to disable the appearance of the button displayed by the cell.</span></span>  
  
 <span data-ttu-id="eafea-105">Následující příklad kódu ukazuje, jak přizpůsobit <xref:System.Windows.Forms.DataGridViewButtonCell> třídu pro zobrazení tlačítek, která se mohou zobrazit zakázané.</span><span class="sxs-lookup"><span data-stu-id="eafea-105">The following code example demonstrates how to customize the <xref:System.Windows.Forms.DataGridViewButtonCell> class to display buttons that can appear disabled.</span></span> <span data-ttu-id="eafea-106">Příklad definuje nový typ `DataGridViewDisableButtonCell`buňky,, který je odvozen z. <xref:System.Windows.Forms.DataGridViewButtonCell></span><span class="sxs-lookup"><span data-stu-id="eafea-106">The example defines a new cell type, `DataGridViewDisableButtonCell`, that derives from <xref:System.Windows.Forms.DataGridViewButtonCell>.</span></span> <span data-ttu-id="eafea-107">Tento typ buňky poskytuje novou `Enabled` vlastnost, kterou lze `false` nastavit na vykreslení zakázaného tlačítka v buňce.</span><span class="sxs-lookup"><span data-stu-id="eafea-107">This cell type provides a new `Enabled` property that can be set to `false` to draw a disabled button in the cell.</span></span> <span data-ttu-id="eafea-108">V příkladu je také definován nový typ `DataGridViewDisableButtonColumn`sloupce, který zobrazuje `DataGridViewDisableButtonCell` objekty.</span><span class="sxs-lookup"><span data-stu-id="eafea-108">The example also defines a new column type, `DataGridViewDisableButtonColumn`, that displays `DataGridViewDisableButtonCell` objects.</span></span> <span data-ttu-id="eafea-109">Pro ukázku tohoto nového typu buňky a sloupce určuje aktuální <xref:System.Windows.Forms.DataGridViewCheckBoxCell> hodnota každého v nadřazeném objektu <xref:System.Windows.Forms.DataGridView> , `DataGridViewDisableButtonCell` zda `Enabled` je `true` vlastnost ve stejném řádku nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="eafea-109">To demonstrate this new cell and column type, the current value of each <xref:System.Windows.Forms.DataGridViewCheckBoxCell> in the parent <xref:System.Windows.Forms.DataGridView> determines whether the `Enabled` property of the `DataGridViewDisableButtonCell` in the same row is `true` or `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eafea-110">Při odvozování z <xref:System.Windows.Forms.DataGridViewCell> nebo <xref:System.Windows.Forms.DataGridViewColumn> a přidání nových vlastností na odvozenou třídu nezapomeňte přepsat `Clone` metodu pro kopírování nových vlastností během operací klonování.</span><span class="sxs-lookup"><span data-stu-id="eafea-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="eafea-111">Měli byste také zavolat `Clone` metodu základní třídy tak, aby byly vlastnosti základní třídy zkopírovány do nové buňky nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="eafea-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eafea-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="eafea-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eafea-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="eafea-113">Compiling the Code</span></span>  
 <span data-ttu-id="eafea-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="eafea-114">This example requires:</span></span>  
  
- <span data-ttu-id="eafea-115">Odkazy na sestavení System, System. Drawing, System. Windows. Forms a System. Windows. Forms. VisualStyles.</span><span class="sxs-lookup"><span data-stu-id="eafea-115">References to the System, System.Drawing, System.Windows.Forms and System.Windows.Forms.VisualStyles assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eafea-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eafea-116">See also</span></span>

- [<span data-ttu-id="eafea-117">Přizpůsobení ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="eafea-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="eafea-118">Architektura ovládacího prvku DataGridView</span><span class="sxs-lookup"><span data-stu-id="eafea-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="eafea-119">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="eafea-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
