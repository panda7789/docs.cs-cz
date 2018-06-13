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
ms.openlocfilehash: 90f4f4500514e2e3d7a231861c0cf4b3d453a4c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540615"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="c326d-102">Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="c326d-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>
<span data-ttu-id="c326d-103">Můžete použít <xref:System.Windows.Forms.WebBrowser> řízení přidat existující dynamické kódu HTML (DHTML) webové aplikace do aplikace Windows Forms klienta.</span><span class="sxs-lookup"><span data-stu-id="c326d-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="c326d-104">To je užitečné, když investovaly významné vývoj čas při vytváření ovládacích prvků na základě DHTML a chcete využít výhod možnosti bohaté uživatelské rozhraní Windows Forms bez přepsání existujícího kódu.</span><span class="sxs-lookup"><span data-stu-id="c326d-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>  
  
 <span data-ttu-id="c326d-105"><xref:System.Windows.Forms.WebBrowser> Řízení umožňuje implementace obousměrné komunikace mezi kódem vaší klientské aplikace a webové stránky skriptovací kód prostřednictvím <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> a <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c326d-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="c326d-106">Kromě toho můžete nakonfigurovat <xref:System.Windows.Forms.WebBrowser> řídit tak, aby vaše ovládací prvky webového bezproblémově s další ovládací prvky ve formuláři aplikace, skrytí DHTML implementace.</span><span class="sxs-lookup"><span data-stu-id="c326d-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="c326d-107">A bezproblémově přizpůsobte ovládací prvky, formátu stránka zobrazená tak, aby jeho barvu pozadí a vizuální styl odpovídat zbytek formuláře a používat <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, a <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vlastnosti, které chcete zakázat funkce standardním prohlížečem.</span><span class="sxs-lookup"><span data-stu-id="c326d-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="c326d-108">Chcete-li vložit DHTML v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c326d-108">To embed DHTML in your Windows Forms application</span></span>  
  
1.  <span data-ttu-id="c326d-109">Nastavit <xref:System.Windows.Forms.WebBrowser> ovládacího prvku <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> vlastnost, která má `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládací prvek v otevírání souborů, které jsou umístěny na ho.</span><span class="sxs-lookup"><span data-stu-id="c326d-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  <span data-ttu-id="c326d-110">Nastavte ovládacího prvku <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> řízení zobrazit jeho místní nabídky po kliknutí pravým tlačítkem ji.</span><span class="sxs-lookup"><span data-stu-id="c326d-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  <span data-ttu-id="c326d-111">Nastavte ovládacího prvku <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládací prvek z neodpovídá na požadavky klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="c326d-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  <span data-ttu-id="c326d-112">Nastavte <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> vlastnost v konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c326d-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
     <span data-ttu-id="c326d-113">Následující kód používá vlastní třídy formuláře pro objekt skriptování.</span><span class="sxs-lookup"><span data-stu-id="c326d-113">The following code uses the form class itself for the scripting object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c326d-114">Component Object (Model COM) musí být schopni přistupovat objekt skriptování.</span><span class="sxs-lookup"><span data-stu-id="c326d-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="c326d-115">Ke zviditelnění svého formuláře do modelu COM, přidejte <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributu do vaší třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="c326d-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  <span data-ttu-id="c326d-116">Veřejné vlastnosti nebo metody implementujte v kódu aplikace, který bude používat váš kód skriptu.</span><span class="sxs-lookup"><span data-stu-id="c326d-116">Implement public properties or methods in your application code that your script code will use.</span></span>  
  
     <span data-ttu-id="c326d-117">Například pokud použijete třídy formuláře pro objekt skriptování, přidejte následující kód do vaší třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="c326d-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  <span data-ttu-id="c326d-118">Použití `window.external` objekt kódu skriptu pro přístup k veřejné vlastnosti a metody zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="c326d-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>  
  
     <span data-ttu-id="c326d-119">Následující kód HTML ukazuje, jak volat metodu pro skriptovací objekt z klikněte na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c326d-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="c326d-120">Zkopírujte tento kód do elementu těla dokumentu HTML, který můžete načíst pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metoda nebo přiřadit ovládacího prvku <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c326d-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  <span data-ttu-id="c326d-121">Implementace funkce ve vašem kódu skript, který bude používat kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="c326d-121">Implement functions in your script code that your application code will use.</span></span>  
  
     <span data-ttu-id="c326d-122">Následující element HTML skriptu poskytuje příklad funkce.</span><span class="sxs-lookup"><span data-stu-id="c326d-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="c326d-123">Zkopírujte tento kód do elementu HEAD dokumentu HTML, který můžete načíst pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metoda nebo přiřadit ovládacího prvku <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c326d-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  <span data-ttu-id="c326d-124">Použití <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnost, která má přístup k kód skriptu z kódu aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="c326d-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>  
  
     <span data-ttu-id="c326d-125">Například přidejte následující kód do tlačítko <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c326d-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. <span data-ttu-id="c326d-126">Po skončení vaší DHTML ladění, nastavte ovládacího prvku <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> vlastnost `true` zabránit <xref:System.Windows.Forms.WebBrowser> řízení ze zobrazení chybové zprávy problémů kód skriptu.</span><span class="sxs-lookup"><span data-stu-id="c326d-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="c326d-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="c326d-127">Example</span></span>  
 <span data-ttu-id="c326d-128">Následující příklad kódu dokončení poskytuje ukázkový aplikace, která můžete použít k pochopení tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="c326d-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="c326d-129">Kód HTML je načten do <xref:System.Windows.Forms.WebBrowser> ovládat prostřednictvím <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnost místo načítá ze samostatného souboru HTML.</span><span class="sxs-lookup"><span data-stu-id="c326d-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c326d-130">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c326d-130">Compiling the Code</span></span>  
 <span data-ttu-id="c326d-131">Tento kód vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c326d-131">This code requires:</span></span>  
  
-   <span data-ttu-id="c326d-132">Odkazy na systém a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="c326d-132">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="c326d-133">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c326d-133">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="c326d-134">Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="c326d-134">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="c326d-135">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="c326d-135">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c326d-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="c326d-136">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="c326d-137">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="c326d-137">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
