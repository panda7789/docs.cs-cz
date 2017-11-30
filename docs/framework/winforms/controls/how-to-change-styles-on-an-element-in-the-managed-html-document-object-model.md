---
title: "Postupy: Změna stylů v elementu v modelu spravovaného objektu dokumentu HTML"
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
helpviewer_keywords: managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 968dd4210e13e301ba2f0ca24617df23706cefc0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="e0159-102">Postupy: Změna stylů v elementu v modelu spravovaného objektu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="e0159-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="e0159-103">Můžete styly řídit vzhled dokumentu a jeho elementy ve formátu HTML.</span><span class="sxs-lookup"><span data-stu-id="e0159-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <span data-ttu-id="e0159-104"><xref:System.Windows.Forms.HtmlDocument>a <xref:System.Windows.Forms.HtmlElement> podporu <xref:System.Windows.Forms.HtmlElement.Style%2A> vlastnosti, které přijímají řetězce styl následující formát:</span><span class="sxs-lookup"><span data-stu-id="e0159-104"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>  
  
 `name1:value1;...;nameN:valueN;`  
  
 <span data-ttu-id="e0159-105">Tady je `DIV` s styl řetězec, který nastaví písmo Arial a veškerý text tučně:</span><span class="sxs-lookup"><span data-stu-id="e0159-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 <span data-ttu-id="e0159-106">Problém s manipulace s styly pomocí <xref:System.Windows.Forms.HtmlElement.Style%2A> vlastnost je, že může prokázat náročná k přidání a odebrání jednotlivých styl nastavení z řetězce.</span><span class="sxs-lookup"><span data-stu-id="e0159-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="e0159-107">Například bude nastaveno komplexní postup pro vás k vykreslení předchozí text kurzívou vždy, když uživatel umisťuje kurzor přes `DIV`a proveďte italics vypnout když ukazatel opustí `DIV`.</span><span class="sxs-lookup"><span data-stu-id="e0159-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="e0159-108">Čas by stát problémem, pokud budete potřebovat k manipulaci s velký počet styly tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="e0159-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>  
  
 <span data-ttu-id="e0159-109">Následující postup obsahuje kód, který vám pomůže snadno pracovat s stylů na dokumenty HTML a elementy.</span><span class="sxs-lookup"><span data-stu-id="e0159-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="e0159-110">Postup vyžaduje, že víte, jak provádět základní úkoly ve Windows Forms, jako je vytvoření nového projektu a přidání ovládacího prvku na formulář.</span><span class="sxs-lookup"><span data-stu-id="e0159-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="e0159-111">Při zpracování změn styl v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0159-111">To process style changes in a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="e0159-112">Vytvoření nového projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e0159-112">Create a new Windows Forms project.</span></span>  
  
2.  <span data-ttu-id="e0159-113">Vytvořte nový soubor – třída končící příponou vhodné pro programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="e0159-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>  
  
3.  <span data-ttu-id="e0159-114">Kopírování `StyleGenerator` do souboru třídy třídy kódu v příkladu části tohoto tématu a uložit kód.</span><span class="sxs-lookup"><span data-stu-id="e0159-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>  
  
4.  <span data-ttu-id="e0159-115">Uložte soubor s názvem Test.htm následující HTML.</span><span class="sxs-lookup"><span data-stu-id="e0159-115">Save the following HTML to a file named Test.htm.</span></span>  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  <span data-ttu-id="e0159-116">Přidat <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1` do hlavního formuláře do projektu.</span><span class="sxs-lookup"><span data-stu-id="e0159-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>  
  
6.  <span data-ttu-id="e0159-117">Přidejte následující kód do souboru kódu vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="e0159-117">Add the following code to your project's code file.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e0159-118">Ujistěte se, že `webBrowser1_DocumentCompleted` rutinu událostí je nakonfigurovaný jako naslouchací proces pro <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="e0159-118">Ensure that the `webBrowser1_DocumentCompleted` event hander is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="e0159-119">V [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], dvakrát klikněte na <xref:System.Windows.Forms.WebBrowser> řídit, v textovém editoru, nakonfigurujte naslouchací proces prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="e0159-119">In [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  <span data-ttu-id="e0159-120">Spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="e0159-120">Run the project.</span></span> <span data-ttu-id="e0159-121">Spustit ukazatelem přes první `DIV` sledovat účinky kódu.</span><span class="sxs-lookup"><span data-stu-id="e0159-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0159-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0159-122">Example</span></span>  
 <span data-ttu-id="e0159-123">Následující příklad kódu ukazuje úplného kódu pro `StyleGenerator` třídy, která analyzuje existující hodnoty styl, podporuje přidání, změně a odebrání styly a vrátí novou hodnotu styl s požadované změny.</span><span class="sxs-lookup"><span data-stu-id="e0159-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e0159-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0159-124">See Also</span></span>  
 <xref:System.Windows.Forms.HtmlElement>
