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
ms.openlocfilehash: 3acc4fd200b547fc754c4151aedc8d70fd1fa0bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502153"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="cb077-102">Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="cb077-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>
<span data-ttu-id="cb077-103">Můžete použít <xref:System.Windows.Forms.WebBrowser> ovládacího prvku k přidání existujícího dynamického kódu HTML (DHTML) webové aplikace do klientských aplikací Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cb077-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="cb077-104">To je užitečné, když jste investovali významné vývoji při vytváření ovládacích prvků na základě DHTML a budete chtít využít výhod bohaté možnosti uživatelského rozhraní Windows Forms aniž byste museli přepsat existující kód.</span><span class="sxs-lookup"><span data-stu-id="cb077-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>  
  
 <span data-ttu-id="cb077-105"><xref:System.Windows.Forms.WebBrowser> Řízení umožňuje implementace obousměrné komunikace mezi kódem vaší klientské aplikace a webové stránky skriptovací kód prostřednictvím <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> a <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cb077-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="cb077-106">Kromě toho můžete nakonfigurovat <xref:System.Windows.Forms.WebBrowser> tak, aby vaše webové ovládací prvky bezproblémově prolínat s jinými ovládacími prvky na formuláři aplikace, skrytí jejich DHTML provádění.</span><span class="sxs-lookup"><span data-stu-id="cb077-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="cb077-107">Bez problémů a přizpůsobte ovládací prvky, formátování stránky zobrazí tak, aby jeho barvu pozadí a vizuální styl odpovídají zbývající části formuláře a použít <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, a <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vlastnosti, které chcete zakázat funkce standardním prohlížečem.</span><span class="sxs-lookup"><span data-stu-id="cb077-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="cb077-108">Chcete-li vložit DHTML v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cb077-108">To embed DHTML in your Windows Forms application</span></span>  
  
1.  <span data-ttu-id="cb077-109">Nastavte <xref:System.Windows.Forms.WebBrowser> ovládacího prvku <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládacího prvku z otevírání souborů vyřadit problém napravit.</span><span class="sxs-lookup"><span data-stu-id="cb077-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  <span data-ttu-id="cb077-110">Nastavit u tohoto prvku <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládací prvek zobrazoval jeho místní nabídku, když uživatel klepne pravým tlačítkem ji.</span><span class="sxs-lookup"><span data-stu-id="cb077-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  <span data-ttu-id="cb077-111">Nastavit u tohoto prvku <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládacího prvku v odpovídání na klávesových zkratek.</span><span class="sxs-lookup"><span data-stu-id="cb077-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  <span data-ttu-id="cb077-112">Nastavte <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> vlastnost v konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="cb077-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
     <span data-ttu-id="cb077-113">Následující kód používá vlastní třídy formuláře pro objekt skriptování.</span><span class="sxs-lookup"><span data-stu-id="cb077-113">The following code uses the form class itself for the scripting object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cb077-114">Modelu COM (Component Object) musí být schopen získat přístup k objektu skriptování.</span><span class="sxs-lookup"><span data-stu-id="cb077-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="cb077-115">Chcete-li zviditelnit formuláře do modelu COM, přidejte <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut do vaší třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="cb077-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  <span data-ttu-id="cb077-116">Implementujte veřejné vlastnosti nebo metody v kódu aplikace, který bude používat váš kód skriptu.</span><span class="sxs-lookup"><span data-stu-id="cb077-116">Implement public properties or methods in your application code that your script code will use.</span></span>  
  
     <span data-ttu-id="cb077-117">Například pokud používáte třídu formuláře pro objekt skriptování, přidejte následující kód do třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="cb077-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  <span data-ttu-id="cb077-118">Použití `window.external` objekt v kódu skriptu pro přístup k veřejné vlastnosti a metody zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="cb077-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>  
  
     <span data-ttu-id="cb077-119">Následující kód HTML ukazuje, jak volat metodu na objekt skriptování od kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="cb077-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="cb077-120">Zkopírujte tento kód do elementu těla dokumentu HTML, který načtete pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody nebo přiřadit ovládacího prvku <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cb077-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  <span data-ttu-id="cb077-121">Implementujte funkce ve vašem skriptovacím kódu, který bude používat váš kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="cb077-121">Implement functions in your script code that your application code will use.</span></span>  
  
     <span data-ttu-id="cb077-122">Následující prvek HTML skript obsahuje ukázkovou funkci.</span><span class="sxs-lookup"><span data-stu-id="cb077-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="cb077-123">Zkopírujte tento kód do elementu HEAD dokumentu HTML, který načtete pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody nebo přiřadit ovládacího prvku <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cb077-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  <span data-ttu-id="cb077-124">Použití <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnosti pro přístup k kód skriptu z kódu klienta aplikace.</span><span class="sxs-lookup"><span data-stu-id="cb077-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>  
  
     <span data-ttu-id="cb077-125">Například přidejte následující kód k tlačítku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="cb077-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. <span data-ttu-id="cb077-126">Po dokončení ladění vašeho DHTML nastavit u tohoto prvku <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> vlastnost `true` zabránit <xref:System.Windows.Forms.WebBrowser> ovládací prvek zobrazoval chybové zprávy problémů kód skriptu.</span><span class="sxs-lookup"><span data-stu-id="cb077-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="cb077-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb077-127">Example</span></span>  
 <span data-ttu-id="cb077-128">Následující příklad kompletní kód poskytuje ukázkové aplikaci, která vám pomůže pochopit tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="cb077-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="cb077-129">Kód HTML je načten do <xref:System.Windows.Forms.WebBrowser> řídit prostřednictvím <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnosti namísto načítané z jiného souboru ve formátu HTML.</span><span class="sxs-lookup"><span data-stu-id="cb077-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cb077-130">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cb077-130">Compiling the Code</span></span>  
 <span data-ttu-id="cb077-131">Tento kód vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="cb077-131">This code requires:</span></span>  
  
-   <span data-ttu-id="cb077-132">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="cb077-132">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="cb077-133">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cb077-133">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="cb077-134">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="cb077-134">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="cb077-135">Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="cb077-135">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb077-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb077-136">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cb077-137">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="cb077-137">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
