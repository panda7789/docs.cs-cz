---
title: 'Postupy: Přidání schopností webového prohlížeče do formulářové aplikaci Windows'
ms.date: 03/30/2017
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
ms.openlocfilehash: 0bbfff139d1ba93bc87bf174c1d20dfae65009ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685149"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="15bda-102">Postupy: Přidání schopností webového prohlížeče do formulářové aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="15bda-102">How to: Add Web Browser Capabilities to a Windows Forms Application</span></span>
<span data-ttu-id="15bda-103">S <xref:System.Windows.Forms.WebBrowser> ovládacího prvku, můžete přidat funkce webového prohlížeče do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="15bda-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="15bda-104">Ovládací prvek funguje jako webového prohlížeče ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="15bda-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="15bda-105">Po načtení počáteční adresu URL tak, že nastavíte <xref:System.Windows.Forms.WebBrowser.Url%2A> vlastností, můžete přejít klepnutím na hypertextové odkazy nebo pomocí klávesové zkratky přejít zpět a vpřed mezi historii navigace.</span><span class="sxs-lookup"><span data-stu-id="15bda-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="15bda-106">Ve výchozím nastavení můžete přístup k funkcím Další prohlížeče prostřednictvím klikněte pravým tlačítkem na nabídku.</span><span class="sxs-lookup"><span data-stu-id="15bda-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="15bda-107">Můžete také otevřít nové dokumenty přetažením na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="15bda-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="15bda-108"><xref:System.Windows.Forms.WebBrowser> Ovládací prvek má také několik vlastnosti, metody a události, které můžete použít k implementaci funkce uživatelského rozhraní, podobné těm v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="15bda-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>  
  
 <span data-ttu-id="15bda-109">Následující příklad kódu se implementuje adresním řádku, typické prohlížeče tlačítka, **souboru** nabídka stavového řádku a záhlaví okna, která zobrazí aktuální název stránky.</span><span class="sxs-lookup"><span data-stu-id="15bda-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15bda-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="15bda-110">Example</span></span>  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="15bda-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="15bda-111">Compiling the Code</span></span>  
 <span data-ttu-id="15bda-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="15bda-112">This example requires:</span></span>  
  
-   <span data-ttu-id="15bda-113">Odkazy `System,``System.Drawing`, a `System.Windows.Forms` sestavení.</span><span class="sxs-lookup"><span data-stu-id="15bda-113">References to the `System,``System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>  
  
 <span data-ttu-id="15bda-114">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="15bda-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="15bda-115">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="15bda-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="15bda-116">Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="15bda-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15bda-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15bda-117">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="15bda-118">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="15bda-118">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
