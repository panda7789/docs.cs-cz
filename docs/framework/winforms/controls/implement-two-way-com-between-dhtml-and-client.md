---
title: 'Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
ms.openlocfilehash: 26cbc995a749c4c129729be700dee588d1033a05
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953440"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="feda4-102">Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="feda4-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>

<span data-ttu-id="feda4-103">Pomocí <xref:System.Windows.Forms.WebBrowser> ovládacího prvku lze přidat existující kód webové aplikace DHTML (Dynamic HTML) do klientských aplikací model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="feda4-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="feda4-104">To je užitečné, když jste investovali významnou dobu vývoje při vytváření ovládacích prvků založených na technologii DHTML a chcete využít výhod bohatých funkcí uživatelského rozhraní model Windows Forms bez nutnosti přepsat stávající kód.</span><span class="sxs-lookup"><span data-stu-id="feda4-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>

<span data-ttu-id="feda4-105">Ovládací prvek umožňuje implementovat obousměrnou komunikaci mezi kódem klientské aplikace a kódem skriptu webové stránky <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> prostřednictvím vlastností a <xref:System.Windows.Forms.WebBrowser.Document%2A>. <xref:System.Windows.Forms.WebBrowser></span><span class="sxs-lookup"><span data-stu-id="feda4-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="feda4-106">Kromě toho můžete nakonfigurovat <xref:System.Windows.Forms.WebBrowser> ovládací prvek tak, aby vaše webové ovládací prvky byly plynule s dalšími ovládacími prvky ve formuláři aplikace, a tím se skryje jejich implementace DHTML.</span><span class="sxs-lookup"><span data-stu-id="feda4-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="feda4-107">Chcete-li plynule prolnout ovládací prvky, naformátujte stránku jako zobrazenou tak, aby barva pozadí a vizuální styl odpovídaly zbývající části <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>formuláře <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, a <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> pomocí vlastností, a můžete zakázat standardní funkce prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="feda4-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>

## <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="feda4-108">Vložení DHTML do aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="feda4-108">To embed DHTML in your Windows Forms application</span></span>

1. <span data-ttu-id="feda4-109"><xref:System.Windows.Forms.WebBrowser> Nastavte <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> vlastnostovládacího`false` prvku na, chcete-li zabránit ovládacímuprvkuvotevíránísouborů,kteréjsounaněj<xref:System.Windows.Forms.WebBrowser> přetaženy.</span><span class="sxs-lookup"><span data-stu-id="feda4-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]

2. <span data-ttu-id="feda4-110">Nastavte <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> vlastnost ovládacího prvku na `false` hodnotu, chcete- <xref:System.Windows.Forms.WebBrowser> li zabránit ovládacímu prvku v zobrazení místní nabídky, když na něj uživatel klikne pravým tlačítkem myši.</span><span class="sxs-lookup"><span data-stu-id="feda4-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]

3. <span data-ttu-id="feda4-111">Nastavte <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vlastnost ovládacího prvku na `false` hodnotu, chcete- <xref:System.Windows.Forms.WebBrowser> li zabránit ovládacímu prvku v reakci na klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="feda4-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]

4. <span data-ttu-id="feda4-112">Nastavte vlastnost v konstruktoru formuláře <xref:System.Windows.Forms.Form.Load> nebo obslužné rutině události. <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A></span><span class="sxs-lookup"><span data-stu-id="feda4-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>

     <span data-ttu-id="feda4-113">Následující kód používá pro objekt skriptování vlastní třídu Form.</span><span class="sxs-lookup"><span data-stu-id="feda4-113">The following code uses the form class itself for the scripting object.</span></span>

    > [!NOTE]
    > <span data-ttu-id="feda4-114">Objekt modelu COM musí být schopný přistupovat ke skriptovacímu objektu.</span><span class="sxs-lookup"><span data-stu-id="feda4-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="feda4-115">Chcete-li, aby byl <xref:System.Runtime.InteropServices.ComVisibleAttribute> formulář viditelný pro model COM, přidejte atribut do třídy Form.</span><span class="sxs-lookup"><span data-stu-id="feda4-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]

5. <span data-ttu-id="feda4-116">Implementujte veřejné vlastnosti nebo metody v kódu aplikace, který bude používat váš kód skriptu.</span><span class="sxs-lookup"><span data-stu-id="feda4-116">Implement public properties or methods in your application code that your script code will use.</span></span>

     <span data-ttu-id="feda4-117">Například pokud použijete třídu Form objektu Script, přidejte do třídy formu následující kód.</span><span class="sxs-lookup"><span data-stu-id="feda4-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]

6. <span data-ttu-id="feda4-118">`window.external` Použijte objekt v kódu skriptu pro přístup k veřejným vlastnostem a metodám zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="feda4-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>

     <span data-ttu-id="feda4-119">Následující kód jazyka HTML ukazuje, jak zavolat metodu na objekt skriptování z kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="feda4-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="feda4-120">Zkopírujte tento kód do prvku tělo dokumentu HTML, který jste načetli pomocí <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody ovládacího prvku nebo přiřadíte <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="feda4-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>

    ```html
    <button onclick="window.external.Test('called from script code')">
        call client code from script code
    </button>
    ```

7. <span data-ttu-id="feda4-121">Implementujte funkce v kódu skriptu, který bude používat váš kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="feda4-121">Implement functions in your script code that your application code will use.</span></span>

     <span data-ttu-id="feda4-122">Následující prvek skriptu HTML poskytuje ukázkovou funkci.</span><span class="sxs-lookup"><span data-stu-id="feda4-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="feda4-123">Zkopírujte tento kód do prvku head dokumentu HTML, který jste načetli pomocí <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody ovládacího prvku nebo přiřadíte <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="feda4-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>

    ```html
    <script>
    function test(message) {
        alert(message);
    }
    </script>
    ```

8. <span data-ttu-id="feda4-124"><xref:System.Windows.Forms.WebBrowser.Document%2A> Použijte vlastnost pro přístup ke kódu skriptu z kódu klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="feda4-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>

     <span data-ttu-id="feda4-125">Přidejte například následující kód do obslužné rutiny události Button <xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="feda4-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]

9. <span data-ttu-id="feda4-126">Po dokončení ladění rozšíření DHTML nastavte <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> vlastnost ovládacího prvku na `true` hodnotu, chcete-li zabránit <xref:System.Windows.Forms.WebBrowser> ovládacímu prvku zobrazit chybové zprávy pro problémy s kódem skriptu.</span><span class="sxs-lookup"><span data-stu-id="feda4-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]

## <a name="example"></a><span data-ttu-id="feda4-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="feda4-127">Example</span></span>

<span data-ttu-id="feda4-128">Následující příklad kompletního kódu poskytuje ukázkovou aplikaci, kterou můžete použít k pochopení této funkce.</span><span class="sxs-lookup"><span data-stu-id="feda4-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="feda4-129">Kód HTML je načten do <xref:System.Windows.Forms.WebBrowser> ovládacího prvku <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> prostřednictvím vlastnosti namísto načítání z samostatného souboru HTML.</span><span class="sxs-lookup"><span data-stu-id="feda4-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>

[!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="feda4-130">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="feda4-130">Compiling the Code</span></span>

<span data-ttu-id="feda4-131">Tento kód vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="feda4-131">This code requires:</span></span>

- <span data-ttu-id="feda4-132">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="feda4-132">References to the System and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="feda4-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="feda4-133">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [<span data-ttu-id="feda4-134">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="feda4-134">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
