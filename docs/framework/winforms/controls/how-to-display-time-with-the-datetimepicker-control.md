---
title: 'Postupy: Zobrazení času pomocí ovládacího prvku DateTimePicker'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: c65a1102ccb8b05602d813831745dbcefed8c17d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879234"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="f12b1-102">Postupy: Zobrazení času pomocí ovládacího prvku DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="f12b1-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="f12b1-103">Pokud chcete, aby vaše aplikace umožňuje uživatelům vybrat datum a čas a k zobrazení tohoto data a času v zadaném formátu, použijte <xref:System.Windows.Forms.DateTimePicker> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f12b1-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="f12b1-104">Následující postup ukazuje, jak používat <xref:System.Windows.Forms.DateTimePicker> ovládací prvek pro zobrazení času.</span><span class="sxs-lookup"><span data-stu-id="f12b1-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="f12b1-105">K zobrazení času pomocí ovládacího prvku DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="f12b1-105">To display the time with the DateTimePicker control</span></span>  
  
1.  <span data-ttu-id="f12b1-106">Nastavte <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="f12b1-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="f12b1-107">Nastavte <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> vlastnost <xref:System.Windows.Forms.DateTimePicker> k `true`.</span><span class="sxs-lookup"><span data-stu-id="f12b1-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="f12b1-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f12b1-108">Example</span></span>  
 <span data-ttu-id="f12b1-109">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Forms.DateTimePicker> , která umožňuje uživatelům zvolit pouze čas.</span><span class="sxs-lookup"><span data-stu-id="f12b1-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f12b1-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f12b1-110">Compiling the Code</span></span>  
 <span data-ttu-id="f12b1-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f12b1-111">This example requires:</span></span>  
  
-   <span data-ttu-id="f12b1-112">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="f12b1-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="f12b1-113">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f12b1-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f12b1-114">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="f12b1-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f12b1-115">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f12b1-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12b1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f12b1-116">See Also</span></span>  
 [<span data-ttu-id="f12b1-117">Ovládací prvek DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="f12b1-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)
