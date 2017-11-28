---
title: "Postupy: Přidání schopností webového prohlížeče do formulářové aplikace Windows"
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
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4bc8592dd821fdef68c2b77242d9d3f2f2b776bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="85ffb-102">Postupy: Přidání schopností webového prohlížeče do formulářové aplikace Windows</span><span class="sxs-lookup"><span data-stu-id="85ffb-102">How to: Add Web Browser Capabilities to a Windows Forms Application</span></span>
<span data-ttu-id="85ffb-103">Pomocí <xref:System.Windows.Forms.WebBrowser> ovládací prvek, můžete přidat funkce webového prohlížeče do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="85ffb-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="85ffb-104">Ve výchozím nastavení funguje jako webový prohlížeč ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="85ffb-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="85ffb-105">Po načtení počáteční adresa URL nastavením <xref:System.Windows.Forms.WebBrowser.Url%2A> vlastnost, můžete přejít kliknutím hypertextových odkazů nebo pomocí klávesové zkratky přesunout zpátky a předávání prostřednictvím historie navigace.</span><span class="sxs-lookup"><span data-stu-id="85ffb-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="85ffb-106">Ve výchozím nastavení můžete přístup k funkcím Další prohlížeče prostřednictvím místní nabídce klikněte pravým tlačítkem.</span><span class="sxs-lookup"><span data-stu-id="85ffb-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="85ffb-107">Můžete také otevřít nové dokumenty umístěním do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="85ffb-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="85ffb-108"><xref:System.Windows.Forms.WebBrowser> Ovládací prvek také obsahuje několik vlastností, metod a události, které můžete použít k implementaci podobné těm, které jsou součástí aplikace Internet Explorer funkce uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="85ffb-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>  
  
 <span data-ttu-id="85ffb-109">Následující příklad kódu implementuje panelu Adresa, tlačítka typické prohlížeče, **souboru** nabídky, stavového řádku a záhlaví, která zobrazuje název aktuální stránky.</span><span class="sxs-lookup"><span data-stu-id="85ffb-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85ffb-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="85ffb-110">Example</span></span>  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85ffb-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="85ffb-111">Compiling the Code</span></span>  
 <span data-ttu-id="85ffb-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="85ffb-112">This example requires:</span></span>  
  
-   <span data-ttu-id="85ffb-113">Odkazuje na `System,``System.Drawing`, a `System.Windows.Forms` sestavení.</span><span class="sxs-lookup"><span data-stu-id="85ffb-113">References to the `System,``System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>  
  
 <span data-ttu-id="85ffb-114">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="85ffb-114">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="85ffb-115">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="85ffb-115">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="85ffb-116">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="85ffb-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ffb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="85ffb-117">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 [<span data-ttu-id="85ffb-118">WebBrowser – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="85ffb-118">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
