---
title: "Postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3add191250a10d1d6016263ada0ba53fc8082717
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="fa08e-102">Postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fa08e-102">How to: Create a LINQ to DataSet Project In Visual Studio</span></span>
<span data-ttu-id="fa08e-103">Různé typy [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projekty vyžadovat určité importovaných oborů názvů (Visual Basic) nebo `using` direktivy (C#) a odkazy.</span><span class="sxs-lookup"><span data-stu-id="fa08e-103">The different types of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projects require certain imported namespaces (Visual Basic) or `using` directives (C#) and references.</span></span> <span data-ttu-id="fa08e-104">Minimální požadavek je odkaz na System.Core.dll a `using` direktivy pro <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="fa08e-104">The minimum requirement is a reference to System.Core.dll and a `using` directive for <xref:System.Linq>.</span></span> <span data-ttu-id="fa08e-105">Ve výchozím nastavení, tyto se zadávají v případě, že vytvoříte novou [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="fa08e-105">By default, these are supplied if you create a new [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] project.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="fa08e-106">také vyžaduje odkaz na System.Data.dll a System.Data.DataSetExtensions.dll a `Imports` (Visual Basic) nebo `using` – direktiva (C#).</span><span class="sxs-lookup"><span data-stu-id="fa08e-106"> also requires a reference to System.Data.dll and System.Data.DataSetExtensions.dll and an `Imports` (Visual Basic) or `using` (C#) directive.</span></span>  
  
 <span data-ttu-id="fa08e-107">Pokud provádíte upgrade projektu ze starší verze sady Visual Studio, můžete chtít zadat tyto odkazy na související LINQ ručně.</span><span class="sxs-lookup"><span data-stu-id="fa08e-107">If you are upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span> <span data-ttu-id="fa08e-108">Budete také muset ručně nastavte projekt, který má cílové rozhraní .NET Framework verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="fa08e-108">You might also have to manually set the project to target the .NET Framework version 3.5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa08e-109">Pokud vytváříte z příkazového řádku, je nutné ručně odkazovat související LINQ knihovny DLL v `drive` **:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.</span><span class="sxs-lookup"><span data-stu-id="fa08e-109">If you are building from a command prompt, you must manually reference the LINQ-related DLLs in `drive`**:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.</span></span>  
  
### <a name="to-target-the-net-framework-35"></a><span data-ttu-id="fa08e-110">Cíl pro rozhraní .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="fa08e-110">To target the .NET Framework 3.5</span></span>  
  
1.  <span data-ttu-id="fa08e-111">V [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], vytvořte nový projekt Visual Basic a C#.</span><span class="sxs-lookup"><span data-stu-id="fa08e-111">In [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], create a new Visual Basic or C# project.</span></span> <span data-ttu-id="fa08e-112">Alternativně můžete otevřít projekt Visual Basic a C#, která byla vytvořena v sadě Visual Studio 2005 a postupujte podle pokynů a převeďte ho na [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="fa08e-112">Alternatively, you can open a Visual Basic or C# project that was created in Visual Studio 2005 and follow the prompts to convert it to a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="fa08e-113">Pro projekt C#, klikněte na tlačítko **projektu** nabídce a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fa08e-113">For a C# project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="fa08e-114">V **aplikace** stránka vlastností, vyberte rozhraní .NET Framework 3.5 v **cílové rozhraní** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="fa08e-114">In the **Application** property page, select .NET Framework 3.5 in the **Target Framework** drop-down list.</span></span>  
  
3.  <span data-ttu-id="fa08e-115">Projektu jazyka Visual Basic, klikněte na tlačítko **projektu** nabídce a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fa08e-115">For a Visual Basic project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="fa08e-116">V **zkompilovat** stránce vlastností, klikněte na tlačítko **Upřesnit možnosti kompilace** a pak vyberte rozhraní .NET Framework 3.5 v **cílové rozhraní (všechny konfigurace)** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="fa08e-116">In the **Compile** property page, click **Advanced Compile Options** and then select .NET Framework 3.5 in the **Target Framework (all configurations)** drop-down list.</span></span>  
  
4.  <span data-ttu-id="fa08e-117">Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz na**, klikněte na tlačítko **rozhraní .NET** kartě, přejděte dolů k položce **System.Core**, klikněte na něj a potom klikněte na tlačítko  **OK**.</span><span class="sxs-lookup"><span data-stu-id="fa08e-117">On the **Project** menu, click **Add Reference**, click the **.NET** tab, scroll down to **System.Core**, click it, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="fa08e-118">Přidat `using` direktivy nebo importované obor názvů pro <xref:System.Linq> k souboru zdrojového kódu nebo projektu.</span><span class="sxs-lookup"><span data-stu-id="fa08e-118">Add a `using` directive or imported namespace for <xref:System.Linq> to your source code file or project.</span></span>  
  
     <span data-ttu-id="fa08e-119">Další informace najdete v tématu [using – direktiva](~/docs/csharp/language-reference/keywords/using-directive.md) nebo [postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fa08e-119">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
### <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="fa08e-120">Chcete-li povolit LINQ na datovou sadu funkcí</span><span class="sxs-lookup"><span data-stu-id="fa08e-120">To enable LINQ to DataSet functionality</span></span>  
  
1.  <span data-ttu-id="fa08e-121">V případě potřeby, postupujte podle kroků výše v tomto tématu se přidat odkaz na System.Core.dll a `using` direktivy nebo importované obor názvů pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="fa08e-121">If necessary, follow the steps earlier in this topic to add a reference to System.Core.dll and a `using` directive or imported namespace for System.Linq.</span></span>  
  
2.  <span data-ttu-id="fa08e-122">V C# nebo Visual Basic, klikněte **projektu** nabídky a pak klikněte na **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="fa08e-122">In C# or Visual Basic, click the **Project** menu, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="fa08e-123">V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET** kartě, pokud není v horní části.</span><span class="sxs-lookup"><span data-stu-id="fa08e-123">In the **Add Reference** dialog box, click the **.NET** tab if it is not on top.</span></span> <span data-ttu-id="fa08e-124">Přejděte dolů k položce **System.Data** a **System.Data.DataSetExtensions** a klikněte na ně.</span><span class="sxs-lookup"><span data-stu-id="fa08e-124">Scroll down to **System.Data** and **System.Data.DataSetExtensions** and click on them.</span></span> <span data-ttu-id="fa08e-125">Klikněte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fa08e-125">Click the **OK** button.</span></span>  
  
4.  <span data-ttu-id="fa08e-126">Přidat `using` direktivy nebo importované obor názvů pro <xref:System.Data> k souboru zdrojového kódu nebo projektu.</span><span class="sxs-lookup"><span data-stu-id="fa08e-126">Add a `using` directive or imported namespace for <xref:System.Data> to your source code file or project.</span></span> <span data-ttu-id="fa08e-127">Další informace najdete v tématu [using – direktiva](~/docs/csharp/language-reference/keywords/using-directive.md) nebo [postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fa08e-127">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
5.  <span data-ttu-id="fa08e-128">Přidáte odkaz na System.Data.DataSetExtensions.dll pro LINQ na datovou sadu funkcí.</span><span class="sxs-lookup"><span data-stu-id="fa08e-128">Add a reference to System.Data.DataSetExtensions.dll for LINQ to Dataset functionality.</span></span> <span data-ttu-id="fa08e-129">Přidáte odkaz na System.Data.dll, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="fa08e-129">Add a reference to System.Data.dll if it does not already exist.</span></span>  
  
6.  <span data-ttu-id="fa08e-130">Volitelně lze přidat `using` direktivy nebo importované obor názvů pro `System.Data.Common` nebo `System.Data.SqlClient`, v závislosti na tom, jak připojit k databázi.</span><span class="sxs-lookup"><span data-stu-id="fa08e-130">Optionally, add a `using` directive or imported namespace for `System.Data.Common` or `System.Data.SqlClient`, depending on how you connect to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa08e-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa08e-131">See Also</span></span>  
 [<span data-ttu-id="fa08e-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="fa08e-132">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [<span data-ttu-id="fa08e-133">Začínáme s jazykem LINQ</span><span class="sxs-lookup"><span data-stu-id="fa08e-133">Getting Started with LINQ</span></span>](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
