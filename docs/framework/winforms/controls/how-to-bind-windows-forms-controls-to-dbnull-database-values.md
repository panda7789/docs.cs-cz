---
title: "Postupy: Připojení ovládacích prvků Windows Forms k hodnotám databáze DBNull"
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
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c96fd6d09b2ddefce4c682976fcff86c9b562a3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="2e54a-102">Postupy: Připojení ovládacích prvků Windows Forms k hodnotám databáze DBNull</span><span class="sxs-lookup"><span data-stu-id="2e54a-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="2e54a-103">Při vytvoření vazby ovládacích prvků Windows Forms ke zdroji dat a zdroj dat vrátí <xref:System.DBNull> hodnotu, můžete nahradit odpovídající hodnotu bez zpracování, formátování a analýzu událostí.</span><span class="sxs-lookup"><span data-stu-id="2e54a-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="2e54a-104"><xref:System.Windows.Forms.Binding.NullValue%2A> Vlastnost převede <xref:System.DBNull> na zadaný objekt při formátování nebo analýza dat zdrojové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2e54a-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e54a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e54a-105">Example</span></span>  
 <span data-ttu-id="2e54a-106">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.DBNull> hodnotu ve dvou různých situacích.</span><span class="sxs-lookup"><span data-stu-id="2e54a-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="2e54a-107">První ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> u vlastnosti řetězce; druhý ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> vlastnosti bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="2e54a-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="2e54a-108">Typy vázané vlastnosti a <xref:System.Windows.Forms.Binding.NullValue%2A> vlastnost musí být stejná nebo dojde k chybě a ne další <xref:System.Windows.Forms.Binding.NullValue%2A> hodnoty budou zpracovány.</span><span class="sxs-lookup"><span data-stu-id="2e54a-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="2e54a-109">V takovém případě nebude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2e54a-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2e54a-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2e54a-110">Compiling the Code</span></span>  
 <span data-ttu-id="2e54a-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2e54a-111">This example requires:</span></span>  
  
-   <span data-ttu-id="2e54a-112">Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="2e54a-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2e54a-113">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2e54a-113">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2e54a-114">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="2e54a-114">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="2e54a-115">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="2e54a-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e54a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e54a-116">See Also</span></span>  
 [<span data-ttu-id="2e54a-117">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="2e54a-117">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="2e54a-118">Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="2e54a-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 [<span data-ttu-id="2e54a-119">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="2e54a-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
