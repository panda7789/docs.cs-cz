---
title: Přidání možností webového prohlížeče do aplikace
description: Naučte se, jak přidat funkce webového prohlížeče do model Windows Forms aplikace s ovládacím prvkem WebBrowser.
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
ms.openlocfilehash: a5a33961ac8301bda86bb5f34e65ac159308987f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174546"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="3a37a-103">Postup přidání možností webového prohlížeče do aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3a37a-103">How to add web browser capabilities to a Windows Forms application</span></span>

<span data-ttu-id="3a37a-104">Pomocí <xref:System.Windows.Forms.WebBrowser> ovládacího prvku můžete do aplikace přidat funkce webového prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="3a37a-104">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="3a37a-105">Ve výchozím nastavení funguje ovládací prvek jako webový prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="3a37a-105">The control works like a Web browser by default.</span></span> <span data-ttu-id="3a37a-106">Po načtení počáteční adresy URL nastavením <xref:System.Windows.Forms.WebBrowser.Url%2A> vlastnosti můžete přejít kliknutím na hypertextové odkazy nebo pomocí klávesových zkratek pro přechod zpět a vpřed v historii navigace.</span><span class="sxs-lookup"><span data-stu-id="3a37a-106">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="3a37a-107">Ve výchozím nastavení máte přístup k dalším funkcím prohlížeče pomocí místní nabídky klikněte pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="3a37a-107">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="3a37a-108">Nové dokumenty můžete otevřít také tak, že je vyřadíte do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3a37a-108">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="3a37a-109"><xref:System.Windows.Forms.WebBrowser>Ovládací prvek má také několik vlastností, metod a událostí, které lze použít k implementaci funkcí uživatelského rozhraní, které jsou podobné těm, které se nachází v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="3a37a-109">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>

<span data-ttu-id="3a37a-110">Následující příklad kódu implementuje panel Adresa, typické tlačítka prohlížeče, nabídku **soubor** , stavový řádek a záhlaví, které zobrazuje název aktuální stránky.</span><span class="sxs-lookup"><span data-stu-id="3a37a-110">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>

## <a name="example"></a><span data-ttu-id="3a37a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a37a-111">Example</span></span>

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a><span data-ttu-id="3a37a-112">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="3a37a-112">Compile the code</span></span>

<span data-ttu-id="3a37a-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="3a37a-113">This example requires:</span></span>

- <span data-ttu-id="3a37a-114">Odkazy na `System` sestavení, `System.Drawing` a `System.Windows.Forms` .</span><span class="sxs-lookup"><span data-stu-id="3a37a-114">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a37a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a37a-115">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="3a37a-116">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="3a37a-116">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
