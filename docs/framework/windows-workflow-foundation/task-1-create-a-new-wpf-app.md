---
title: 'Úloha 1: Vytvořte novou aplikaci Windows Presentation Foundation'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd21013331e19fa9e18ad7cbee0a7bb07abaf3d2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="392f2-102">Úloha 1: Vytvořte novou aplikaci Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="392f2-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="392f2-103">V této úloze, vytvoříte prázdnou aplikaci Windows Presentation Foundation (WPF) pomocí šablony sady Visual Studio aplikace WPF a přidáte odkazy na příslušné [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] sestavení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="392f2-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="392f2-104">Chcete-li vytvořit projekt aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="392f2-104">To create the WPF Application project</span></span>  
  
1.  <span data-ttu-id="392f2-105">Otevřete Visual Studio a na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="392f2-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="392f2-106">V **nový projekt** dialogovém okně vyberte buď **Visual C#** nebo **jazyka Visual Basic** z **nainstalovaných šablonách** podokna na levé straně do pole.</span><span class="sxs-lookup"><span data-stu-id="392f2-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="392f2-107">Pokud jazyk podle vašeho výběru nezobrazí, podívejte se do části **jiné jazyky**.</span><span class="sxs-lookup"><span data-stu-id="392f2-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3.  <span data-ttu-id="392f2-108">Vyberte **Windows** v **nainstalovaných šablonách** podokně.</span><span class="sxs-lookup"><span data-stu-id="392f2-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="392f2-109">V tomto horním podokně, potvrďte, že (výchozí hodnota) **rozhraní .NET Framework 4** byl vybraný v rozevíracím seznamu a pak vyberte **aplikaci WPF**.</span><span class="sxs-lookup"><span data-stu-id="392f2-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="392f2-110">Nastavte na název projektu do **HostingApplication** v dolní části okna.</span><span class="sxs-lookup"><span data-stu-id="392f2-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6.  <span data-ttu-id="392f2-111">Název řešení nastavte **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="392f2-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7.  <span data-ttu-id="392f2-112">Klikněte na tlačítko **OK** vytvořit projekt aplikace.</span><span class="sxs-lookup"><span data-stu-id="392f2-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="392f2-113">Visual Studio vytvoří základní uživatelské rozhraní WPF pro vaši aplikaci a obsahuje odpovídající XAML a soubory kódu.</span><span class="sxs-lookup"><span data-stu-id="392f2-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8.  <span data-ttu-id="392f2-114">Přidejte odkazy na **WorkflowModel** sestavení.</span><span class="sxs-lookup"><span data-stu-id="392f2-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="392f2-115">Chcete-li to provést, v **Průzkumníku řešení**, klikněte pravým tlačítkem myši **HostingApplication** projektu a vyberte **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="392f2-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="392f2-116">V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET** podržte stisknutou klávesu CTRL, vyberte následující sestavení a pak klikněte na tlačítko **OK**:</span><span class="sxs-lookup"><span data-stu-id="392f2-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="392f2-117">Systém.</span><span class="sxs-lookup"><span data-stu-id="392f2-117">System.Activities</span></span>  
  
    -   <span data-ttu-id="392f2-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="392f2-118">System.Activities.Presentation</span></span>  
  
    -   <span data-ttu-id="392f2-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="392f2-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="392f2-120">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="392f2-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="392f2-121">V tématu [úloha 2: hostování návrháře pracovních postupů](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) se dozvíte, jak k hostování plátna návrháře návrhu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="392f2-121">See [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="392f2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="392f2-122">See Also</span></span>  
 [<span data-ttu-id="392f2-123">Změna hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="392f2-123">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="392f2-124">Úkol 2: Hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="392f2-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
