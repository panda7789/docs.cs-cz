---
title: Přidání možností webového prohlížeče do aplikace
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
ms.openlocfilehash: 5feecd975700745541103e81fd09bfc5e788c729
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747223"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="1d54f-102">Postupy: Přidání schopností webového prohlížeče do aplikace Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d54f-102">How to: Add Web Browser Capabilities to a Windows Forms Application</span></span>
<span data-ttu-id="1d54f-103">Pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser> můžete do aplikace přidat funkce webového prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="1d54f-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="1d54f-104">Ve výchozím nastavení funguje ovládací prvek jako webový prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="1d54f-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="1d54f-105">Po načtení počáteční adresy URL nastavením vlastnosti <xref:System.Windows.Forms.WebBrowser.Url%2A> můžete přejít kliknutím na hypertextové odkazy nebo pomocí klávesových zkratek pro přechod zpět a vpřed v historii navigace.</span><span class="sxs-lookup"><span data-stu-id="1d54f-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="1d54f-106">Ve výchozím nastavení máte přístup k dalším funkcím prohlížeče pomocí místní nabídky klikněte pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="1d54f-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="1d54f-107">Nové dokumenty můžete otevřít také tak, že je vyřadíte do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1d54f-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="1d54f-108">Ovládací prvek <xref:System.Windows.Forms.WebBrowser> také obsahuje několik vlastností, metod a událostí, které lze použít k implementaci funkcí uživatelského rozhraní, které jsou podobné těm, které jsou k dispozici v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="1d54f-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>  
  
 <span data-ttu-id="1d54f-109">Následující příklad kódu implementuje panel Adresa, typické tlačítka prohlížeče, nabídku **soubor** , stavový řádek a záhlaví, které zobrazuje název aktuální stránky.</span><span class="sxs-lookup"><span data-stu-id="1d54f-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d54f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d54f-110">Example</span></span>  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d54f-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1d54f-111">Compiling the Code</span></span>  
 <span data-ttu-id="1d54f-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1d54f-112">This example requires:</span></span>  
  
- <span data-ttu-id="1d54f-113">Odkazy na sestavení `System`, `System.Drawing`a `System.Windows.Forms`.</span><span class="sxs-lookup"><span data-stu-id="1d54f-113">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d54f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d54f-114">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="1d54f-115">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="1d54f-115">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
