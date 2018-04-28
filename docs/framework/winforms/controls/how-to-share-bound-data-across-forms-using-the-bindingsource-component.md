---
title: 'Postupy: Sdílení připojených dat mezi formuláři pomocí součásti BindingSource'
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
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1907f25e2d9bfe5fc6e93020add47d8a52379e87
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="62149-102">Postupy: Sdílení připojených dat mezi formuláři pomocí součásti BindingSource</span><span class="sxs-lookup"><span data-stu-id="62149-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="62149-103">Můžete snadno sdílet data mezi formuláři pomocí <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="62149-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="62149-104">Můžete například zobrazit jednu jen pro čtení formulář, který je souhrn dat zdroje dat a jiné upravovat formulář, který obsahuje podrobné informace o aktuálně vybrané položky ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="62149-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="62149-105">Tento příklad ukazuje tento scénář.</span><span class="sxs-lookup"><span data-stu-id="62149-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62149-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="62149-106">Example</span></span>  
 <span data-ttu-id="62149-107">Následující příklad kódu ukazuje, jak sdílet <xref:System.Windows.Forms.BindingSource> a vázaných dat mezi formuláři.</span><span class="sxs-lookup"><span data-stu-id="62149-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="62149-108">V tomto příkladu sdílený <xref:System.Windows.Forms.BindingSource> předaný do konstruktoru objektu podřízené formuláře.</span><span class="sxs-lookup"><span data-stu-id="62149-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="62149-109">Podřízené formuláře umožňuje uživateli upravit data pro aktuálně vybrané položky na hlavní formulář.</span><span class="sxs-lookup"><span data-stu-id="62149-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62149-110"><xref:System.Windows.Forms.BindingSource.BindingComplete> Událost pro <xref:System.Windows.Forms.BindingSource> součást zpracovává v příkladu zajistit, aby zůstaly synchronizované dva formuláře.</span><span class="sxs-lookup"><span data-stu-id="62149-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="62149-111">Další informace o tom, proč je to provést, najdete v části [postupy: Zajistěte více ovládací prvky vázané stejné Data zdroje zůstávají synchronizovat](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="62149-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62149-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="62149-112">Compiling the Code</span></span>  
 <span data-ttu-id="62149-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="62149-113">This example requires:</span></span>  
  
-   <span data-ttu-id="62149-114">Odkazy na systém, System.Windows.Forms, System.Drawing, System.Data a System.Xml sestavení.</span><span class="sxs-lookup"><span data-stu-id="62149-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="62149-115">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="62149-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="62149-116">Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="62149-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="62149-117">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="62149-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62149-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="62149-118">See Also</span></span>  
 [<span data-ttu-id="62149-119">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="62149-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="62149-120">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="62149-120">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="62149-121">Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="62149-121">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
