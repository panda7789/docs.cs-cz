---
title: 'Postupy: Vytvoření formuláře Windows Forms s možností změny velikosti pro zadávání dat'
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
ms.openlocfilehash: ebccad248927d8a201bd5758e5ddf2d5414455f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189663"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="e5a14-102">Postupy: Vytvoření formuláře Windows Forms s možností změny velikosti pro zadávání dat</span><span class="sxs-lookup"><span data-stu-id="e5a14-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="e5a14-103">Dobré rozložení odpovídá změny v dimenzích jeho nadřazený formulář.</span><span class="sxs-lookup"><span data-stu-id="e5a14-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="e5a14-104">Můžete použít <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na upravte si rozložení formuláře pro změnit velikost a umístění ovládacích prvků běžely jako změnu rozměrů formuláře.</span><span class="sxs-lookup"><span data-stu-id="e5a14-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="e5a14-105"><xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek je také užitečné v případě změny v obsahu své ovládací prvky příčina změny v rozložení.</span><span class="sxs-lookup"><span data-stu-id="e5a14-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="e5a14-106">Proces popsané v tomto postupu můžete provést v rámci prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5a14-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="e5a14-107">Viz také [názorný postup: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e5a14-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5a14-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5a14-108">Example</span></span>  
 <span data-ttu-id="e5a14-109">Následující příklad ukazuje, jak používat <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku k vytvoření rozložení, které dobře reaguje, když uživatel změní velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="e5a14-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="e5a14-110">Ukazuje také rozložení, jež odpovídá lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="e5a14-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e5a14-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e5a14-111">Compiling the Code</span></span>  
 <span data-ttu-id="e5a14-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e5a14-112">This example requires:</span></span>  
  
-   <span data-ttu-id="e5a14-113">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e5a14-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e5a14-114">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e5a14-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e5a14-115">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="e5a14-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a14-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5a14-116">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="e5a14-117">Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e5a14-117">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="e5a14-118">Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci</span><span class="sxs-lookup"><span data-stu-id="e5a14-118">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="e5a14-119">Microsoft Windows uživatelské prostředí, oficiální pokyny pro uživatelské rozhraní vývojářů a návrhářů. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="e5a14-119">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
