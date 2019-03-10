---
title: 'Postupy: Zpracování chyb a výjimek, ke kterým dochází s datovou vazbou'
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
ms.openlocfilehash: 8400ce602d15c195aea43f9e5a162fddb1783830
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703149"
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a><span data-ttu-id="1aa85-102">Postupy: Zpracování chyb a výjimek, ke kterým dochází s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="1aa85-102">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>
<span data-ttu-id="1aa85-103">Často výjimky a chyby dojde u podkladových objektů obchodní svázat s ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="1aa85-103">Oftentimes exceptions and errors occur on the underlying business objects when you bind them to controls.</span></span> <span data-ttu-id="1aa85-104">Můžete zachytit tyto chyby a výjimky a potom obnovit nebo předat informace o chybě pro uživatele pomocí manipulace <xref:System.Windows.Forms.Binding.BindingComplete> události pro konkrétní <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, nebo <xref:System.Windows.Forms.CurrencyManager> komponenty.</span><span class="sxs-lookup"><span data-stu-id="1aa85-104">You can intercept these errors and exceptions and then either recover or pass the error information to the user by handling the <xref:System.Windows.Forms.Binding.BindingComplete> event for a particular <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, or <xref:System.Windows.Forms.CurrencyManager> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1aa85-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1aa85-105">Example</span></span>  
 <span data-ttu-id="1aa85-106">Tento příklad kódu ukazuje, jak zpracování chyb a výjimek, ke kterým dochází při operaci datové vazby.</span><span class="sxs-lookup"><span data-stu-id="1aa85-106">This code example demonstrates how to handle errors and exceptions that occur during a data-binding operation.</span></span> <span data-ttu-id="1aa85-107">Ukazuje, jak zachytávat chyby pomocí manipulace <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> událost <xref:System.Windows.Forms.Binding> objekty.</span><span class="sxs-lookup"><span data-stu-id="1aa85-107">It demonstrates how to intercept errors by handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event of the <xref:System.Windows.Forms.Binding> objects.</span></span> <span data-ttu-id="1aa85-108">Pokud chcete zachytávat chyby a výjimky ve zpracování této události, je nutné povolit formátování pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="1aa85-108">In order to intercept errors and exceptions by handling this event, you must enable formatting for the binding.</span></span> <span data-ttu-id="1aa85-109">Můžete povolit formátování, pokud vazba je vytvořen nebo přidat do kolekce vazby nebo nastavením <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="1aa85-109">You can enable formatting when the binding is constructed or added to the binding collection, or by setting the <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> property to `true`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 <span data-ttu-id="1aa85-110">Když je kód spuštěn a prázdný řetězec je zadána pro název součásti nebo hodnotu nižší než 100 je zadána pro výrobní číslo se zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="1aa85-110">When the code is running and an empty string is entered for the part name or a value less than 100 is entered for the part number, a message box appears.</span></span> <span data-ttu-id="1aa85-111">To je výsledkem zpracování <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> událost pro tyto vazby textové pole.</span><span class="sxs-lookup"><span data-stu-id="1aa85-111">This is a result of handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event for these textbox bindings.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1aa85-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1aa85-112">Compiling the Code</span></span>  
 <span data-ttu-id="1aa85-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1aa85-113">This example requires:</span></span>  
  
-   <span data-ttu-id="1aa85-114">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1aa85-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1aa85-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1aa85-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1aa85-116">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="1aa85-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa85-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1aa85-117">See also</span></span>
- <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>
- [<span data-ttu-id="1aa85-118">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="1aa85-118">BindingSource Component</span></span>](bindingsource-component.md)
