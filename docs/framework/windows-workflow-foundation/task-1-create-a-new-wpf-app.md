---
title: 'Úloha 1: vytvoření nové aplikace Windows Presentation Foundation'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031892"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="3f7c8-102">Úloha 1: vytvoření nové aplikace Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="3f7c8-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>

<span data-ttu-id="3f7c8-103">V této úloze vytvoříte prázdnou aplikaci Windows Presentation Foundation (WPF) pomocí šablony Visual Studio aplikace WPF a přidáte odkazy na příslušná sestavení pracovního postupu [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f7c8-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
## <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="3f7c8-104">Vytvoření projektu aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="3f7c8-104">To create the WPF Application project</span></span>

1. <span data-ttu-id="3f7c8-105">Otevřete Visual Studio a v nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.</span><span class="sxs-lookup"><span data-stu-id="3f7c8-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="3f7c8-106">V dialogovém okně **Nový projekt** vyberte v podokně **Nainstalované šablony** na levé straně pole buď  **C# vizuál** , nebo **Visual Basic** .</span><span class="sxs-lookup"><span data-stu-id="3f7c8-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="3f7c8-107">Pokud se zvolený jazyk nezobrazí, podívejte se do části **jiné jazyky**.</span><span class="sxs-lookup"><span data-stu-id="3f7c8-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>

3. <span data-ttu-id="3f7c8-108">V podokně **Nainstalované šablony** vyberte **Windows** .</span><span class="sxs-lookup"><span data-stu-id="3f7c8-108">Select **Windows** in the **Installed Templates** pane.</span></span>

4. <span data-ttu-id="3f7c8-109">V horním podokně potvrďte, že je v rozevíracím seznamu vybrána možnost (výchozí hodnota) **.NET Framework 4** , a pak vyberte **aplikace WPF**.</span><span class="sxs-lookup"><span data-stu-id="3f7c8-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>

5. <span data-ttu-id="3f7c8-110">V dolní části okna nastavte název projektu na **HostingApplication** .</span><span class="sxs-lookup"><span data-stu-id="3f7c8-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>

6. <span data-ttu-id="3f7c8-111">Nastavte název řešení na **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="3f7c8-111">Set the solution name to **RehostingTheDesigner**.</span></span>

7. <span data-ttu-id="3f7c8-112">Kliknutím na tlačítko **OK** vytvořte projekt aplikace.</span><span class="sxs-lookup"><span data-stu-id="3f7c8-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="3f7c8-113">Visual Studio vytvoří základní uživatelské rozhraní WPF pro vaši aplikaci a zahrne příslušné soubory XAML a kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="3f7c8-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>

8. <span data-ttu-id="3f7c8-114">Přidejte odkazy na **WorkflowModel** sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f7c8-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="3f7c8-115">To provedete tak, že v **Průzkumník řešení**kliknete pravým tlačítkem na projekt **HostingApplication** a vyberete **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="3f7c8-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>

9. <span data-ttu-id="3f7c8-116">V dialogovém okně **Přidat odkaz** klikněte na kartu **.NET** , podržte stisknutou klávesu CTRL, vyberte následující sestavení a klikněte na tlačítko **OK**:</span><span class="sxs-lookup"><span data-stu-id="3f7c8-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>

    - <span data-ttu-id="3f7c8-117">System. Activities</span><span class="sxs-lookup"><span data-stu-id="3f7c8-117">System.Activities</span></span>
    - <span data-ttu-id="3f7c8-118">System. Activities. Presentation</span><span class="sxs-lookup"><span data-stu-id="3f7c8-118">System.Activities.Presentation</span></span>
    - <span data-ttu-id="3f7c8-119">System. Activities. Core. Presentation</span><span class="sxs-lookup"><span data-stu-id="3f7c8-119">System.Activities.Core.Presentation</span></span>

10. <span data-ttu-id="3f7c8-120">Další informace o tom, jak hostovat plátno návrhu návrháře pracovních postupů, najdete v tématu [Úloha 2: hostování Návrhář postupu provádění](task-2-host-the-workflow-designer.md) .</span><span class="sxs-lookup"><span data-stu-id="3f7c8-120">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f7c8-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f7c8-121">See also</span></span>

- [<span data-ttu-id="3f7c8-122">Změna hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="3f7c8-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="3f7c8-123">Úkol 2: Hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="3f7c8-123">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
