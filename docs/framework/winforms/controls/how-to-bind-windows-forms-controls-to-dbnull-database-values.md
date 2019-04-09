---
title: 'Postupy: Vytvoření vazby ovládacích prvků Windows Forms k hodnotám databáze DBNull'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: cc3dde0db3dad6faff548951ff06a39d23248d53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137758"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="cf621-102">Postupy: Vytvoření vazby ovládacích prvků Windows Forms k hodnotám databáze DBNull</span><span class="sxs-lookup"><span data-stu-id="cf621-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="cf621-103">Při připojení ovládacích prvků Windows Forms ke zdroji dat a zdroj dat vrátí <xref:System.DBNull> hodnotu, můžete nahradit odpovídající hodnotu bez zpracování, formátování a analýzu událostí.</span><span class="sxs-lookup"><span data-stu-id="cf621-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="cf621-104"><xref:System.Windows.Forms.Binding.NullValue%2A> Vlastnost převede <xref:System.DBNull> zadanému objektu při formátování nebo analýzy dat zdrojové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cf621-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf621-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf621-105">Example</span></span>  
 <span data-ttu-id="cf621-106">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.DBNull> hodnoty ve dvou různých situacích.</span><span class="sxs-lookup"><span data-stu-id="cf621-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="cf621-107">První ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> pro vlastnosti typu string, druhý ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> vlastnosti bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="cf621-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="cf621-108">Typy vázané vlastnosti a <xref:System.Windows.Forms.Binding.NullValue%2A> vlastnost musí být stejná nebo dojde k chybě a žádné další <xref:System.Windows.Forms.Binding.NullValue%2A> hodnoty bude zpracována.</span><span class="sxs-lookup"><span data-stu-id="cf621-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="cf621-109">V takovém případě nebude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="cf621-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cf621-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cf621-110">Compiling the Code</span></span>  
 <span data-ttu-id="cf621-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="cf621-111">This example requires:</span></span>  
  
-   <span data-ttu-id="cf621-112">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="cf621-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="cf621-113">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cf621-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="cf621-114">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="cf621-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf621-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf621-115">See also</span></span>

- [<span data-ttu-id="cf621-116">BindingSource – komponenta</span><span class="sxs-lookup"><span data-stu-id="cf621-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="cf621-117">Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="cf621-117">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="cf621-118">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="cf621-118">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
