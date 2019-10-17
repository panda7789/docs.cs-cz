---
title: 'Postupy: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: aeab1b506b9ded4c3c2ab527f07a8655a44cad2b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396029"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="e4157-102">Postupy: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat</span><span class="sxs-lookup"><span data-stu-id="e4157-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="e4157-103">Dobré rozložení reaguje na změny v dimenzích svého nadřazeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="e4157-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="e4157-104">Pomocí ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> můžete uspořádat rozložení formuláře tak, aby se změnila velikost a umístění ovládacích prvků konzistentním způsobem, jakým se mění rozměry formuláře.</span><span class="sxs-lookup"><span data-stu-id="e4157-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="e4157-105">Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> je také užitečný v případě, že změny v obsahu ovládacích prvků způsobují změny v rozložení.</span><span class="sxs-lookup"><span data-stu-id="e4157-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="e4157-106">Proces popsaný v tomto postupu lze provést v prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e4157-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="e4157-107">Viz také [Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e4157-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4157-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4157-108">Example</span></span>  
 <span data-ttu-id="e4157-109">Následující příklad ukazuje, jak použít ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> k sestavení rozložení, které reaguje na to, kdy uživatel změní velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="e4157-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="e4157-110">Ukazuje také rozložení, které reaguje dobře na lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="e4157-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4157-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e4157-111">Compiling the Code</span></span>  
 <span data-ttu-id="e4157-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e4157-112">This example requires:</span></span>  
  
- <span data-ttu-id="e4157-113">Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="e4157-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4157-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4157-114">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="e4157-115">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e4157-115">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="e4157-116">Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci</span><span class="sxs-lookup"><span data-stu-id="e4157-116">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
