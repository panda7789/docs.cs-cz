---
title: 'Postupy: Změna stylů v elementu v modelu spravovaného objektu dokumentu HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 804041991199dd2722e3a0f38800bafd8933bbab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608395"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="0cb21-102">Postupy: Změna stylů v elementu v modelu spravovaného objektu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="0cb21-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>

<span data-ttu-id="0cb21-103">Styly ve formátu HTML můžete řídit vzhled dokument a jeho elementy.</span><span class="sxs-lookup"><span data-stu-id="0cb21-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <span data-ttu-id="0cb21-104"><xref:System.Windows.Forms.HtmlDocument> a <xref:System.Windows.Forms.HtmlElement> podporují <xref:System.Windows.Forms.HtmlElement.Style%2A> vlastnosti, které přijímají řetězce styl v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="0cb21-104"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>

`name1:value1;...;nameN:valueN;`

<span data-ttu-id="0cb21-105">Tady je `DIV` řetězcem styl, který nastaví na Arial a veškerý text tučné písmo:</span><span class="sxs-lookup"><span data-stu-id="0cb21-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>

`<DIV style="font-face:arial;font-weight:bold;">`

`Hello, world!`

`</DIV>`

<span data-ttu-id="0cb21-106">Problém s manipulace s použitím stylů <xref:System.Windows.Forms.HtmlElement.Style%2A> vlastnost je, že může být velmi náročná na přidání a odebrání nastavení jednotlivých stylu z řetězce.</span><span class="sxs-lookup"><span data-stu-id="0cb21-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="0cb21-107">Například jej by se mohla stát složité postup vykreslit předchozí text kurzívou pokaždé, když se uživatel se umístí kurzor nad `DIV`a využijte kurzíva vypnout, když ukazatel opustí `DIV`.</span><span class="sxs-lookup"><span data-stu-id="0cb21-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="0cb21-108">Čas by stát problémem, pokud potřebujete pracovat s velký počet styly tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="0cb21-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>

<span data-ttu-id="0cb21-109">Následující postup obsahuje kód, který vám umožní snadno pracovat s styly u dokumentů HTML a prvky.</span><span class="sxs-lookup"><span data-stu-id="0cb21-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="0cb21-110">Postup vyžaduje, že víte, jak provádět základní úlohy ve Windows Forms, jako je například vytvoření nového projektu a přidání ovládacího prvku na formulář.</span><span class="sxs-lookup"><span data-stu-id="0cb21-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>

### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="0cb21-111">Ke zpracování změn stylů v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0cb21-111">To process style changes in a Windows Forms application</span></span>

1. <span data-ttu-id="0cb21-112">Vytvoření nového projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0cb21-112">Create a new Windows Forms project.</span></span>

2. <span data-ttu-id="0cb21-113">Vytvořte nový soubor třídy končící na rozšíření, které jsou vhodné pro vaše programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="0cb21-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>

3. <span data-ttu-id="0cb21-114">Kopírovat `StyleGenerator` třídy do souboru třídy kód v oddíle Příklad tohoto tématu a uložit kód.</span><span class="sxs-lookup"><span data-stu-id="0cb21-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>

4. <span data-ttu-id="0cb21-115">Následující kód HTML uložte do souboru s názvem Test.htm.</span><span class="sxs-lookup"><span data-stu-id="0cb21-115">Save the following HTML to a file named Test.htm.</span></span>

    ```html
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

5. <span data-ttu-id="0cb21-116">Přidat <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1` hlavního formuláře do projektu.</span><span class="sxs-lookup"><span data-stu-id="0cb21-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>

6. <span data-ttu-id="0cb21-117">Přidejte následující kód do souboru kódu projektu.</span><span class="sxs-lookup"><span data-stu-id="0cb21-117">Add the following code to your project's code file.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="0cb21-118">Ujistěte se, že `webBrowser1_DocumentCompleted` obslužnou rutinu události je nakonfigurovaný jako naslouchací proces pro <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="0cb21-118">Ensure that the `webBrowser1_DocumentCompleted` event hander is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="0cb21-119">V sadě Visual Studio, poklepejte na <xref:System.Windows.Forms.WebBrowser> ovládací prvek; v textovém editoru, nakonfigurujte naslouchací proces prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="0cb21-119">In Visual Studio, double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>  
  
     [!code-csharp[ManagedDOMStyles#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7. <span data-ttu-id="0cb21-120">Spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="0cb21-120">Run the project.</span></span> <span data-ttu-id="0cb21-121">Spustit ukazatel myši nad první `DIV` chcete sledovat účinky kód.</span><span class="sxs-lookup"><span data-stu-id="0cb21-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cb21-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="0cb21-122">Example</span></span>  
 <span data-ttu-id="0cb21-123">Následující příklad kódu ukazuje celý kód pro `StyleGenerator` třídu, která analyzuje existující hodnotu stylu, podporuje přidání, změně a odebrání styly a vrátí novou hodnotu stylu s požadované změny.</span><span class="sxs-lookup"><span data-stu-id="0cb21-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>  
  
 [!code-csharp[ManagedDOMStyles#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0cb21-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0cb21-124">See also</span></span>

- <xref:System.Windows.Forms.HtmlElement>
