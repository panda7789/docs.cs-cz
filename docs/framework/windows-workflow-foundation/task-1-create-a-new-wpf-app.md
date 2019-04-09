---
title: 'Úkol 1: Vytvoření nové aplikace Windows Presentation Foundation'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: dae523714862ed36d36e65b51be62acff9b17f51
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193393"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="37164-102">Úkol 1: Vytvoření nové aplikace Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="37164-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="37164-103">Při plnění tohoto úkolu Vytvoření prázdné aplikace Windows Presentation Foundation (WPF) pomocí šablony WPF aplikace Visual Studio a přidejte odkazy na příslušné [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] sestavení pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="37164-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="37164-104">Vytvoření projektu aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="37164-104">To create the WPF Application project</span></span>  
  
1.  <span data-ttu-id="37164-105">Otevřete sadu Visual Studio a na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="37164-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="37164-106">V **nový projekt** dialogové okno Vyberte buď **Visual C#**  nebo **jazyka Visual Basic** z **nainstalované šablony** podokna na levé straně na straně pole.</span><span class="sxs-lookup"><span data-stu-id="37164-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="37164-107">Pokud jazyk podle vašeho výběru se nezobrazí, podívejte se do části **jiné jazyky**.</span><span class="sxs-lookup"><span data-stu-id="37164-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3.  <span data-ttu-id="37164-108">Vyberte **Windows** v **nainstalované šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="37164-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="37164-109">V horním podokně, ujistěte se, že (výchozí hodnota) **rozhraní .NET Framework 4** vybrané v rozevíracím seznamu a pak vyberte **aplikace WPF**.</span><span class="sxs-lookup"><span data-stu-id="37164-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="37164-110">Nastavte název projekt tak, aby **HostingApplication** v dolní části okna.</span><span class="sxs-lookup"><span data-stu-id="37164-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6.  <span data-ttu-id="37164-111">Nastavte název řešení **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="37164-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7.  <span data-ttu-id="37164-112">Klikněte na tlačítko **OK** vytvoření projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="37164-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="37164-113">Visual Studio vytvoří základní rozhraní WPF pro vaši aplikaci a obsahuje odpovídající XAML a soubory kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="37164-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8.  <span data-ttu-id="37164-114">Přidání odkazů na **WorkflowModel** sestavení.</span><span class="sxs-lookup"><span data-stu-id="37164-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="37164-115">Chcete-li to provést, v **Průzkumníka řešení**, klikněte pravým tlačítkem myši **HostingApplication** projektu a vyberte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="37164-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="37164-116">V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET** kartu, podržte stisknutou klávesu CTRL, vyberte následující sestavení a pak klikněte na tlačítko **OK**:</span><span class="sxs-lookup"><span data-stu-id="37164-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="37164-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="37164-117">System.Activities</span></span>  
  
    -   <span data-ttu-id="37164-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="37164-118">System.Activities.Presentation</span></span>  
  
    -   <span data-ttu-id="37164-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="37164-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="37164-120">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="37164-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="37164-121">Zobrazit [úloha 2: Hostování návrháře postupu provádění](task-2-host-the-workflow-designer.md) informace o hostování pracovního postupu návrháře návrhové plátno.</span><span class="sxs-lookup"><span data-stu-id="37164-121">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37164-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37164-122">See also</span></span>

- [<span data-ttu-id="37164-123">Změna hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="37164-123">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="37164-124">Úkol 2: Hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="37164-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
