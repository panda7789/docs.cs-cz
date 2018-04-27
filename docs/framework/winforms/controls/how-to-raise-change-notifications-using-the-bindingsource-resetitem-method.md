---
title: 'Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 81acd82a1cdec41744c60e6ffb0548bd83f7b953
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a><span data-ttu-id="cb77c-102">Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem</span><span class="sxs-lookup"><span data-stu-id="cb77c-102">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>
<span data-ttu-id="cb77c-103">Některé zdroje dat pro vaše ovládací prvky nejsou vytváření oznámení o změnách při změně, přidání nebo odstranění položek.</span><span class="sxs-lookup"><span data-stu-id="cb77c-103">Some data sources for your controls do not raise change notifications when items are changed, added, or deleted.</span></span> <span data-ttu-id="cb77c-104">Pomocí <xref:System.Windows.Forms.BindingSource> součásti, můžete vytvořit vazbu na těchto zdrojů dat a vyvolat upozornění na změnu z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="cb77c-104">With the <xref:System.Windows.Forms.BindingSource> component, you can bind to such data sources and raise a change notification from your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb77c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb77c-105">Example</span></span>  
 <span data-ttu-id="cb77c-106">Tento formulář ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součásti pro vazbu seznamu <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cb77c-106">This form demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind a list to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="cb77c-107">V seznamu nevyvolá oznámení o změnách, proto <xref:System.Windows.Forms.BindingSource.ResetItem%2A> metodu <xref:System.Windows.Forms.BindingSource> je volána, když se změní na položku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="cb77c-107">The list does not raise change notifications, so the <xref:System.Windows.Forms.BindingSource.ResetItem%2A> method on the <xref:System.Windows.Forms.BindingSource> is called when an item in the list is changed.</span></span> <span data-ttu-id="cb77c-108">.</span><span class="sxs-lookup"><span data-stu-id="cb77c-108">.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cb77c-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cb77c-109">Compiling the Code</span></span>  
 <span data-ttu-id="cb77c-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="cb77c-110">This example requires:</span></span>  
  
-   <span data-ttu-id="cb77c-111">Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="cb77c-111">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="cb77c-112">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cb77c-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="cb77c-113">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="cb77c-113">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="cb77c-114">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="cb77c-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb77c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb77c-115">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="cb77c-116">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="cb77c-116">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="cb77c-117">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="cb77c-117">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
