---
title: "Postupy: Zobrazení času pomocí ovládacího prvku DateTimePicker"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 528147539d278e8592ca17fb3371365a360abace
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="a1bd3-102">Postupy: Zobrazení času pomocí ovládacího prvku DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="a1bd3-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="a1bd3-103">Pokud chcete, aby vaše aplikace umožňuje uživatelům vyberte datum a čas a k zobrazení tohoto datum a čas v zadaném formátu, použijte <xref:System.Windows.Forms.DateTimePicker> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a1bd3-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="a1bd3-104">Následující postup ukazuje, jak používat <xref:System.Windows.Forms.DateTimePicker> řízení k zobrazení času.</span><span class="sxs-lookup"><span data-stu-id="a1bd3-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="a1bd3-105">K zobrazení času pomocí ovládacího prvku DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="a1bd3-105">To display the time with the DateTimePicker control</span></span>  
  
1.  <span data-ttu-id="a1bd3-106">Nastavte <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnosti<xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="a1bd3-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="a1bd3-107">Nastavte <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> vlastnost <xref:System.Windows.Forms.DateTimePicker> k `true`.</span><span class="sxs-lookup"><span data-stu-id="a1bd3-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a1bd3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1bd3-108">Example</span></span>  
 <span data-ttu-id="a1bd3-109">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Forms.DateTimePicker> umožňující uživatelům zvolit pouze po dobu.</span><span class="sxs-lookup"><span data-stu-id="a1bd3-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a1bd3-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a1bd3-110">Compiling the Code</span></span>  
 <span data-ttu-id="a1bd3-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a1bd3-111">This example requires:</span></span>  
  
-   <span data-ttu-id="a1bd3-112">Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="a1bd3-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="a1bd3-113">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a1bd3-113">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="a1bd3-114">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="a1bd3-114">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="a1bd3-115">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="a1bd3-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1bd3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1bd3-116">See Also</span></span>  
 [<span data-ttu-id="a1bd3-117">DateTimePicker – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a1bd3-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)
