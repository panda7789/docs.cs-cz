---
title: 'Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
ms.openlocfilehash: c7c05eb8d858c1f911e148def1c714e3caf74c95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532259"
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a><span data-ttu-id="dcd97-102">Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="dcd97-102">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>
<span data-ttu-id="dcd97-103">Často výjimek a chyb dojde na základní objekty obchodní vazby na ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="dcd97-103">Oftentimes exceptions and errors occur on the underlying business objects when you bind them to controls.</span></span> <span data-ttu-id="dcd97-104">Tyto chyby a výjimky zachytit a potom můžete buď obnovit nebo předávat informace o chybě pro uživatele ve zpracování <xref:System.Windows.Forms.Binding.BindingComplete> událostí pro konkrétní <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, nebo <xref:System.Windows.Forms.CurrencyManager> součásti.</span><span class="sxs-lookup"><span data-stu-id="dcd97-104">You can intercept these errors and exceptions and then either recover or pass the error information to the user by handling the <xref:System.Windows.Forms.Binding.BindingComplete> event for a particular <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, or <xref:System.Windows.Forms.CurrencyManager> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcd97-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="dcd97-105">Example</span></span>  
 <span data-ttu-id="dcd97-106">Tento příklad kódu ukazuje, jak zpracování chyb a výjimek, ke kterým došlo během vazby dat operace.</span><span class="sxs-lookup"><span data-stu-id="dcd97-106">This code example demonstrates how to handle errors and exceptions that occur during a data-binding operation.</span></span> <span data-ttu-id="dcd97-107">Ukazuje, jak zachytávat chyby ve zpracování <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> události <xref:System.Windows.Forms.Binding> objekty.</span><span class="sxs-lookup"><span data-stu-id="dcd97-107">It demonstrates how to intercept errors by handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event of the <xref:System.Windows.Forms.Binding> objects.</span></span> <span data-ttu-id="dcd97-108">Při zpracování této událost zachytávat chyby a výjimky, je nutné aktivovat formátování pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="dcd97-108">In order to intercept errors and exceptions by handling this event, you must enable formatting for the binding.</span></span> <span data-ttu-id="dcd97-109">Můžete povolit formátování, pokud vazba je vytvořená nebo přidat do kolekce vazby, nebo nastavením <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="dcd97-109">You can enable formatting when the binding is constructed or added to the binding collection, or by setting the <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> property to `true`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 <span data-ttu-id="dcd97-110">Kdy kód běží a je prázdný řetězec zadaný pro název součásti nebo hodnotu menší než 100 je zadán pro výrobní číslo, zobrazí se okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="dcd97-110">When the code is running and an empty string is entered for the part name or a value less than 100 is entered for the part number, a message box appears.</span></span> <span data-ttu-id="dcd97-111">To je způsobeno tím, zpracování <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> událost pro tyto vazby textové pole.</span><span class="sxs-lookup"><span data-stu-id="dcd97-111">This is a result of handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event for these textbox bindings.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dcd97-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="dcd97-112">Compiling the Code</span></span>  
 <span data-ttu-id="dcd97-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="dcd97-113">This example requires:</span></span>  
  
-   <span data-ttu-id="dcd97-114">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="dcd97-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="dcd97-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="dcd97-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="dcd97-116">Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="dcd97-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="dcd97-117">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="dcd97-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd97-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcd97-118">See Also</span></span>  
 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>  
 [<span data-ttu-id="dcd97-119">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="dcd97-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
