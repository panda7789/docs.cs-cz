---
title: 'Postupy: vytvoření a spuštění dlouhodobého spuštění pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 2c3368bc73d54f2848cad3c1086b1d9733205d2b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425608"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="3087a-102">Postupy: vytvoření a spuštění dlouhodobého spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3087a-102">How to: Create and Run a Long Running Workflow</span></span>
<span data-ttu-id="3087a-103">Jednou z centrální funkcí Windows Workflow Foundation (WF) je modul runtime schopnost zachovat a uvolnit nečinných pracovních postupů k databázi.</span><span class="sxs-lookup"><span data-stu-id="3087a-103">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="3087a-104">Kroky v [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) jsme vám ukázali základní informace o hostování pracovního postupu pomocí konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="3087a-104">The steps in [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="3087a-105">Příklady zobrazila počáteční pracovní postupy, obslužné rutiny pracovních postupů životního cyklu a obnovení záložky.</span><span class="sxs-lookup"><span data-stu-id="3087a-105">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="3087a-106">Ukázání efektivně trvalost pracovního postupu, se vyžaduje složitější hostitele pracovního postupu, který podporuje spouštění a obnovení několika instancí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="3087a-106">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="3087a-107">Tento krok úvodního kurzu ukazuje, jak vytvořit hostitele formuláře Windows, aplikace, která podporuje spouštění a obnovení několika instancí pracovních postupů, trvalost pracovního postupu a poskytuje základ pro pokročilé funkce, jako je sledování a správy verzí, které jsou jsme vám ukázali v následných kroků v kurzu.</span><span class="sxs-lookup"><span data-stu-id="3087a-107">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3087a-108">Tento kurz – krok a všechny následné kroky použít všechny tři typy pracovních postupů z [postupy: vytvoření pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="3087a-108">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span> <span data-ttu-id="3087a-109">Pokud jste neprovedli všechny tři typy můžete stáhnout úplnou verzi kroky z [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="3087a-109">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3087a-110">Pokud chcete stáhnout dokončený verzi nebo zobrazit na video s návodem tohoto kurzu, najdete v článku [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="3087a-110">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="3087a-111">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="3087a-111">In this topic</span></span>  
  
-   [<span data-ttu-id="3087a-112">K vytvoření databáze trvalosti</span><span class="sxs-lookup"><span data-stu-id="3087a-112">To create the persistence database</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [<span data-ttu-id="3087a-113">Chcete-li přidat odkaz na sestavení DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="3087a-113">To add the reference to the DurableInstancing assemblies</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [<span data-ttu-id="3087a-114">Chcete-li vytvořit formulář hostitele pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3087a-114">To create the workflow host form</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [<span data-ttu-id="3087a-115">Chcete-li přidat vlastnosti a metody helper formuláře</span><span class="sxs-lookup"><span data-stu-id="3087a-115">To add the properties and helper methods of the form</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [<span data-ttu-id="3087a-116">Ke konfiguraci úložiště instancí, obslužné rutiny pracovních postupů životního cyklu a rozšíření</span><span class="sxs-lookup"><span data-stu-id="3087a-116">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [<span data-ttu-id="3087a-117">Povolit spuštění a obnovení více typy pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="3087a-117">To enable starting and resuming multiple workflow types</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [<span data-ttu-id="3087a-118">Spuštění nového pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3087a-118">To start a new workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [<span data-ttu-id="3087a-119">Pracovní postup obnovit</span><span class="sxs-lookup"><span data-stu-id="3087a-119">To resume a workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [<span data-ttu-id="3087a-120">K ukončení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3087a-120">To terminate a workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [<span data-ttu-id="3087a-121">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="3087a-121">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CreatePersistenceDatabase"></a> <span data-ttu-id="3087a-122">K vytvoření databáze trvalosti</span><span class="sxs-lookup"><span data-stu-id="3087a-122">To create the persistence database</span></span>  
  
1.  <span data-ttu-id="3087a-123">Otevřete SQL Server Management Studio a připojte se k místnímu serveru, třeba **. \SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="3087a-123">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="3087a-124">Klikněte pravým tlačítkem myši **databází** uzlu na místním serveru a vyberte **novou databázi**.</span><span class="sxs-lookup"><span data-stu-id="3087a-124">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="3087a-125">Název nové databáze **WF45GettingStartedTutorial**přijměte všechny ostatní hodnoty a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="3087a-125">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3087a-126">Ujistěte se, že máte **Create Database** oprávnění na místním serveru před vytvořením databáze.</span><span class="sxs-lookup"><span data-stu-id="3087a-126">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>  
  
2.  <span data-ttu-id="3087a-127">Zvolte **otevřít**, **souboru** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="3087a-127">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="3087a-128">Přejděte do následující složky: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="3087a-128">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>  
  
     <span data-ttu-id="3087a-129">Vyberte následující dva soubory a klikněte na tlačítko **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="3087a-129">Select the following two files and click **Open**.</span></span>  
  
    -   <span data-ttu-id="3087a-130">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="3087a-130">SqlWorkflowInstanceStoreLogic.sql</span></span>  
  
    -   <span data-ttu-id="3087a-131">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="3087a-131">SqlWorkflowInstanceStoreSchema.sql</span></span>  
  
3.  <span data-ttu-id="3087a-132">Zvolte **SqlWorkflowInstanceStoreSchema.sql** z **okno** nabídky.</span><span class="sxs-lookup"><span data-stu-id="3087a-132">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="3087a-133">Ujistěte se, že **WF45GettingStartedTutorial** výběru v **dostupných databází** rozevírací seznam a zvolte **Execute** z **dotazu**nabídky.</span><span class="sxs-lookup"><span data-stu-id="3087a-133">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>  
  
4.  <span data-ttu-id="3087a-134">Zvolte **SqlWorkflowInstanceStoreLogic.sql** z **okno** nabídky.</span><span class="sxs-lookup"><span data-stu-id="3087a-134">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="3087a-135">Ujistěte se, že **WF45GettingStartedTutorial** výběru v **dostupných databází** rozevírací seznam a zvolte **Execute** z **dotazu**nabídky.</span><span class="sxs-lookup"><span data-stu-id="3087a-135">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="3087a-136">Je důležité provést předchozí dva kroky ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3087a-136">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="3087a-137">Pokud dotazy provádějí mimo pořadí, dojde k chybám a databáze trvalosti není správně nakonfigurována.</span><span class="sxs-lookup"><span data-stu-id="3087a-137">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>  
  
###  <a name="BKMK_AddReference"></a> <span data-ttu-id="3087a-138">Chcete-li přidat odkaz na sestavení DurableInstancing</span><span class="sxs-lookup"><span data-stu-id="3087a-138">To add the reference to the DurableInstancing assemblies</span></span>  
  
1.  <span data-ttu-id="3087a-139">Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a vyberte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="3087a-139">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="3087a-140">Vyberte **sestavení** z **přidat odkaz** a do pole `DurableInstancing` do **hledání sestavení** pole.</span><span class="sxs-lookup"><span data-stu-id="3087a-140">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="3087a-141">Tím se filtruje sestavení a usnadňuje vyberte požadované odkazy.</span><span class="sxs-lookup"><span data-stu-id="3087a-141">This filters the assemblies and makes the desired references easier to select.</span></span>  
  
3.  <span data-ttu-id="3087a-142">Zaškrtněte políčko vedle **System.Activities.DurableInstancing** a **System.Runtime.DurableInstancing** z **výsledky hledání** seznamu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="3087a-142">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>  
  
###  <a name="BKMK_CreateForm"></a> <span data-ttu-id="3087a-143">Chcete-li vytvořit formulář hostitele pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3087a-143">To create the workflow host form</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3087a-144">Kroky v tomto postupu popisují, jak přidat a nakonfigurovat formuláře ručně.</span><span class="sxs-lookup"><span data-stu-id="3087a-144">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="3087a-145">V případě potřeby můžete stáhnout soubory řešení pro tento kurz a přidejte dokončené formuláře do projektu.</span><span class="sxs-lookup"><span data-stu-id="3087a-145">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="3087a-146">Stáhněte si kurz soubory, naleznete v tématu [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="3087a-146">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="3087a-147">Jakmile se soubory stáhnou, klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a zvolte **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="3087a-147">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="3087a-148">Přidejte odkaz na **System.Windows.Forms** a **System.Drawing**.</span><span class="sxs-lookup"><span data-stu-id="3087a-148">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="3087a-149">Tyto odkazy jsou přidány automaticky, pokud chcete přidat nového formuláře pomocí **přidat**, **nová položka** nabídky, ale musí přidat ručně, při importu formuláře.</span><span class="sxs-lookup"><span data-stu-id="3087a-149">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="3087a-150">Jakmile jsou přidány odkazy, klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **přidat**, **existující položku**.</span><span class="sxs-lookup"><span data-stu-id="3087a-150">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="3087a-151">Přejděte `Form` složky v souborech projektu, vyberte **WorkflowHostForm.cs** (nebo **WorkflowHostForm.vb**) a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="3087a-151">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="3087a-152">Pokud se rozhodnete importovat formuláři a pak dolů na další část, můžete přeskočit [přidat vlastnosti a metody helper formuláře](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span><span class="sxs-lookup"><span data-stu-id="3087a-152">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span></span>  
  
1.  <span data-ttu-id="3087a-153">Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **přidat**, **nová položka**.</span><span class="sxs-lookup"><span data-stu-id="3087a-153">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="3087a-154">V **nainstalováno** šablon klikněte na položku **formuláře Windows**, typ `WorkflowHostForm` v **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="3087a-154">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>  
  
3.  <span data-ttu-id="3087a-155">Konfigurujte následující vlastnosti ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="3087a-155">Configure the following properties on the form.</span></span>  
  
    |<span data-ttu-id="3087a-156">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="3087a-156">Property</span></span>|<span data-ttu-id="3087a-157">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3087a-157">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="3087a-158">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="3087a-158">FormBorderStyle</span></span>|<span data-ttu-id="3087a-159">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="3087a-159">FixedSingle</span></span>|  
    |<span data-ttu-id="3087a-160">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="3087a-160">MaximizeBox</span></span>|<span data-ttu-id="3087a-161">False</span><span class="sxs-lookup"><span data-stu-id="3087a-161">False</span></span>|  
    |<span data-ttu-id="3087a-162">Velikost</span><span class="sxs-lookup"><span data-stu-id="3087a-162">Size</span></span>|<span data-ttu-id="3087a-163">400, 420</span><span class="sxs-lookup"><span data-stu-id="3087a-163">400, 420</span></span>|  
  
4.  <span data-ttu-id="3087a-164">Přidejte následující ovládací prvky do formuláře v pořadí zadaný a nakonfigurujte vlastnosti, podle pokynů.</span><span class="sxs-lookup"><span data-stu-id="3087a-164">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>  
  
    |<span data-ttu-id="3087a-165">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="3087a-165">Control</span></span>|<span data-ttu-id="3087a-166">Vlastnosti: hodnota</span><span class="sxs-lookup"><span data-stu-id="3087a-166">Property: Value</span></span>|  
    |-------------|---------------------|  
    |<span data-ttu-id="3087a-167">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="3087a-167">**Button**</span></span>|<span data-ttu-id="3087a-168">Název: NewGame</span><span class="sxs-lookup"><span data-stu-id="3087a-168">Name: NewGame</span></span><br /><br /> <span data-ttu-id="3087a-169">Umístění: 13, 13</span><span class="sxs-lookup"><span data-stu-id="3087a-169">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="3087a-170">Velikost: 75, 23</span><span class="sxs-lookup"><span data-stu-id="3087a-170">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="3087a-171">Text: Novou hru</span><span class="sxs-lookup"><span data-stu-id="3087a-171">Text: New Game</span></span>|  
    |<span data-ttu-id="3087a-172">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="3087a-172">**Label**</span></span>|<span data-ttu-id="3087a-173">Umístění: 94, 18</span><span class="sxs-lookup"><span data-stu-id="3087a-173">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="3087a-174">Text: Číslo od 1 do uhodnout</span><span class="sxs-lookup"><span data-stu-id="3087a-174">Text: Guess a number from 1 to</span></span>|  
    |<span data-ttu-id="3087a-175">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="3087a-175">**ComboBox**</span></span>|<span data-ttu-id="3087a-176">Název: NumberRange</span><span class="sxs-lookup"><span data-stu-id="3087a-176">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="3087a-177">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="3087a-177">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="3087a-178">Položek: 10, 100, 1 000</span><span class="sxs-lookup"><span data-stu-id="3087a-178">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="3087a-179">Umístění: 228, 12</span><span class="sxs-lookup"><span data-stu-id="3087a-179">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="3087a-180">Velikost: 143, 21</span><span class="sxs-lookup"><span data-stu-id="3087a-180">Size: 143, 21</span></span>|  
    |<span data-ttu-id="3087a-181">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="3087a-181">**Label**</span></span>|<span data-ttu-id="3087a-182">Umístění: 13, 43</span><span class="sxs-lookup"><span data-stu-id="3087a-182">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="3087a-183">Text: Typ pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3087a-183">Text: Workflow type</span></span>|  
    |<span data-ttu-id="3087a-184">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="3087a-184">**ComboBox**</span></span>|<span data-ttu-id="3087a-185">Název: WorkflowType</span><span class="sxs-lookup"><span data-stu-id="3087a-185">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="3087a-186">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="3087a-186">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="3087a-187">Položky: SequentialNumberGuessWorkflow StateMachineNumberGuessWorkflow FlowchartNumberGuessWorkflow,</span><span class="sxs-lookup"><span data-stu-id="3087a-187">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="3087a-188">Umístění: 94, 40</span><span class="sxs-lookup"><span data-stu-id="3087a-188">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="3087a-189">Velikost: 277, 21</span><span class="sxs-lookup"><span data-stu-id="3087a-189">Size: 277, 21</span></span>|  
    |<span data-ttu-id="3087a-190">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="3087a-190">**Label**</span></span>|<span data-ttu-id="3087a-191">Název: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="3087a-191">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="3087a-192">Umístění: 13, 362</span><span class="sxs-lookup"><span data-stu-id="3087a-192">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="3087a-193">Text: Verze pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3087a-193">Text: Workflow version</span></span>|  
    |<span data-ttu-id="3087a-194">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="3087a-194">**GroupBox**</span></span>|<span data-ttu-id="3087a-195">Umístění: 13, 67</span><span class="sxs-lookup"><span data-stu-id="3087a-195">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="3087a-196">Velikost: 358, 287</span><span class="sxs-lookup"><span data-stu-id="3087a-196">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="3087a-197">Text: hra</span><span class="sxs-lookup"><span data-stu-id="3087a-197">Text: Game</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="3087a-198">Při přidávání následující ovládací prvky, vytvořte z nich skupině.</span><span class="sxs-lookup"><span data-stu-id="3087a-198">When adding the following controls, put them into the GroupBox.</span></span>  
  
    |<span data-ttu-id="3087a-199">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="3087a-199">Control</span></span>|<span data-ttu-id="3087a-200">Vlastnosti: hodnota</span><span class="sxs-lookup"><span data-stu-id="3087a-200">Property: Value</span></span>|  
    |-------------|---------------------|  
    |<span data-ttu-id="3087a-201">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="3087a-201">**Label**</span></span>|<span data-ttu-id="3087a-202">Umístění: 7, 20</span><span class="sxs-lookup"><span data-stu-id="3087a-202">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="3087a-203">Text: Id Instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3087a-203">Text: Workflow Instance Id</span></span>|  
    |<span data-ttu-id="3087a-204">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="3087a-204">**ComboBox**</span></span>|<span data-ttu-id="3087a-205">Název: InstanceId</span><span class="sxs-lookup"><span data-stu-id="3087a-205">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="3087a-206">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="3087a-206">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="3087a-207">Umístění: 121, 17</span><span class="sxs-lookup"><span data-stu-id="3087a-207">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="3087a-208">Velikost: 227, 21</span><span class="sxs-lookup"><span data-stu-id="3087a-208">Size: 227, 21</span></span>|  
    |<span data-ttu-id="3087a-209">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="3087a-209">**Label**</span></span>|<span data-ttu-id="3087a-210">Umístění: 7, 47</span><span class="sxs-lookup"><span data-stu-id="3087a-210">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="3087a-211">Text: odhad</span><span class="sxs-lookup"><span data-stu-id="3087a-211">Text: Guess</span></span>|  
    |<span data-ttu-id="3087a-212">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="3087a-212">**TextBox**</span></span>|<span data-ttu-id="3087a-213">Název: odhad</span><span class="sxs-lookup"><span data-stu-id="3087a-213">Name: Guess</span></span><br /><br /> <span data-ttu-id="3087a-214">Umístění: 50, 44</span><span class="sxs-lookup"><span data-stu-id="3087a-214">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="3087a-215">Velikost: 65, 20</span><span class="sxs-lookup"><span data-stu-id="3087a-215">Size: 65, 20</span></span>|  
    |<span data-ttu-id="3087a-216">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="3087a-216">**Button**</span></span>|<span data-ttu-id="3087a-217">Název: EnterGuess</span><span class="sxs-lookup"><span data-stu-id="3087a-217">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="3087a-218">Umístění: 121, 42</span><span class="sxs-lookup"><span data-stu-id="3087a-218">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="3087a-219">Velikost: 75, 23</span><span class="sxs-lookup"><span data-stu-id="3087a-219">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="3087a-220">Text: Zadejte odhad</span><span class="sxs-lookup"><span data-stu-id="3087a-220">Text: Enter Guess</span></span>|  
    |<span data-ttu-id="3087a-221">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="3087a-221">**Button**</span></span>|<span data-ttu-id="3087a-222">Název: QuitGame</span><span class="sxs-lookup"><span data-stu-id="3087a-222">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="3087a-223">Umístění: 274, 42</span><span class="sxs-lookup"><span data-stu-id="3087a-223">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="3087a-224">Velikost: 75, 23</span><span class="sxs-lookup"><span data-stu-id="3087a-224">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="3087a-225">Text: ukončení</span><span class="sxs-lookup"><span data-stu-id="3087a-225">Text: Quit</span></span>|  
    |<span data-ttu-id="3087a-226">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="3087a-226">**TextBox**</span></span>|<span data-ttu-id="3087a-227">Název: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="3087a-227">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="3087a-228">Umístění: 10, 73</span><span class="sxs-lookup"><span data-stu-id="3087a-228">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="3087a-229">Multiline: True</span><span class="sxs-lookup"><span data-stu-id="3087a-229">Multiline: True</span></span><br /><br /> <span data-ttu-id="3087a-230">Jen pro čtení: True</span><span class="sxs-lookup"><span data-stu-id="3087a-230">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="3087a-231">Posuvníky: svislý</span><span class="sxs-lookup"><span data-stu-id="3087a-231">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="3087a-232">Velikost: 338, 208</span><span class="sxs-lookup"><span data-stu-id="3087a-232">Size: 338, 208</span></span>|  
  
5.  <span data-ttu-id="3087a-233">Nastavte **AcceptButton** vlastnost formuláře **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="3087a-233">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>  
  
 <span data-ttu-id="3087a-234">Následující příklad ukazuje dokončený formulář.</span><span class="sxs-lookup"><span data-stu-id="3087a-234">The following example illustrates the completed form.</span></span>  
  
 <span data-ttu-id="3087a-235">![WF45 Formulář hostitele pracovního postupu kurz Začínáme se službou](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")</span><span class="sxs-lookup"><span data-stu-id="3087a-235">![WF45 Getting Started Tutorial Workflow Host Form](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")</span></span>  
  
###  <a name="BKMK_AddHelperMethods"></a> <span data-ttu-id="3087a-236">Chcete-li přidat vlastnosti a metody helper formuláře</span><span class="sxs-lookup"><span data-stu-id="3087a-236">To add the properties and helper methods of the form</span></span>  
 <span data-ttu-id="3087a-237">Kroky v této části přidejte do třídy formuláře, která konfigurace uživatelského rozhraní ve formuláři pro podporu spouštění a obnovení workflowů číslo odhad vlastnosti a metody helper.</span><span class="sxs-lookup"><span data-stu-id="3087a-237">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>  
  
1.  <span data-ttu-id="3087a-238">Klikněte pravým tlačítkem na **WorkflowHostForm** v **Průzkumníka řešení** a zvolte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="3087a-238">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="3087a-239">Přidejte následující `using` (nebo `Imports`) příkazů v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.</span><span class="sxs-lookup"><span data-stu-id="3087a-239">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Windows.Forms  
    Imports System.Activities.DurableInstancing  
    Imports System.Activities  
    Imports System.Data.SqlClient  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    using System.Activities.DurableInstancing;  
    using System.Activities;  
    using System.Data.SqlClient;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="3087a-240">Přidejte následující deklarace členů na **WorkflowHostForm** třídy.</span><span class="sxs-lookup"><span data-stu-id="3087a-240">Add the following member declarations to the **WorkflowHostForm** class.</span></span>  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    Dim store As SqlWorkflowInstanceStore  
    Dim WorkflowStarting As Boolean  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    SqlWorkflowInstanceStore store;  
    bool WorkflowStarting;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="3087a-241">Pokud váš připojovací řetězec se liší, aktualizujte `connectionString` odkázat na databázi.</span><span class="sxs-lookup"><span data-stu-id="3087a-241">If your connection string is different, update `connectionString` to refer to your database.</span></span>  
  
4.  <span data-ttu-id="3087a-242">Přidat `WorkflowInstanceId` vlastnost `WorkflowFormHost` třídy.</span><span class="sxs-lookup"><span data-stu-id="3087a-242">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>  
  
    ```vb  
    Public ReadOnly Property WorkflowInstanceId() As Guid  
        Get  
            If InstanceId.SelectedIndex = -1 Then  
                Return Guid.Empty  
            Else  
                Return New Guid(InstanceId.SelectedItem.ToString())  
            End If  
        End Get  
    End Property  
    ```  
  
    ```csharp  
    public Guid WorkflowInstanceId  
    {  
        get  
        {  
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;  
        }  
    }  
    ```  
  
     <span data-ttu-id="3087a-243">`InstanceId` – Pole se seznamem se zobrazí seznam identifikátorů instance trvalá pracovního postupu a `WorkflowInstanceId` vlastnost vrátí aktuálně vybraný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="3087a-243">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>  
  
5.  <span data-ttu-id="3087a-244">Přidání obslužné rutiny pro formulář `Load` událostí.</span><span class="sxs-lookup"><span data-stu-id="3087a-244">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="3087a-245">Chcete-li přidat obslužnou rutinu, přepněte **návrhové zobrazení** formuláře, klikněte na tlačítko **události** ikonu v horní části **vlastnosti** okno a dvakrát klikněte na **zatížení**.</span><span class="sxs-lookup"><span data-stu-id="3087a-245">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6.  <span data-ttu-id="3087a-246">Přidejte následující kód, který `WorkflowHostForm_Load`.</span><span class="sxs-lookup"><span data-stu-id="3087a-246">Add the following code to `WorkflowHostForm_Load`.</span></span>  
  
    ```vb  
    'Initialize the store and configure it so that it can be used for  
    'multiple WorkflowApplication instances.  
    store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    'Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0  
    WorkflowType.SelectedIndex = 0  
  
    ListPersistedWorkflows()  
    ```  
  
    ```csharp  
    // Initialize the store and configure it so that it can be used for  
    // multiple WorkflowApplication instances.  
    store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    // Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0;  
    WorkflowType.SelectedIndex = 0;  
  
    ListPersistedWorkflows();  
    ```  
  
     <span data-ttu-id="3087a-247">Při načtení formuláře, `SqlWorkflowInstanceStore` je nakonfigurován, rozsahu a pracovní postup polí se seznamem typ jsou nastaveny na výchozí hodnoty a instance trvalá pracovního postupu jsou přidány do `InstanceId` – pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="3087a-247">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>  
  
7.  <span data-ttu-id="3087a-248">Přidat `SelectedIndexChanged` obslužné rutiny pro `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="3087a-248">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="3087a-249">Chcete-li přidat obslužnou rutinu, přepněte **návrhové zobrazení** formuláře, vyberte `InstanceId` – pole se seznamem, klikněte na tlačítko **události** ikonu v horní části **vlastnosti** okna, a dvakrát klikněte na panel **SelectedIndexChanged**.</span><span class="sxs-lookup"><span data-stu-id="3087a-249">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8.  <span data-ttu-id="3087a-250">Přidejte následující kód, který `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="3087a-250">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="3087a-251">Pokaždé, když uživatel vybere pracovního postupu pomocí pole se seznamem touto obslužnou rutinou aktualizace stavové okno.</span><span class="sxs-lookup"><span data-stu-id="3087a-251">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>  
  
    ```vb  
    If InstanceId.SelectedIndex = -1 Then  
        Return  
    End If  
  
    'Clear the status window.  
    WorkflowStatus.Clear()  
  
    'Get the workflow version and display it.  
    'If the workflow is just starting then this info will not  
    'be available in the persistence store so do not try and retrieve it.  
    If Not WorkflowStarting Then  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        WorkflowVersion.Text = _  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
        'Unload the instance.  
        instance.Abandon()  
    End If  
    ```  
  
    ```csharp  
    if (InstanceId.SelectedIndex == -1)  
    {  
        return;  
    }  
  
    // Clear the status window.  
    WorkflowStatus.Clear();  
  
    // Get the workflow version and display it.  
    // If the workflow is just starting then this info will not  
    // be available in the persistence store so do not try and retrieve it.  
    if (!WorkflowStarting)  
    {  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
        WorkflowVersion.Text =  
            WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
        // Unload the instance.  
        instance.Abandon();  
    }  
    ```  
  
9. <span data-ttu-id="3087a-252">Přidejte následující `ListPersistedWorkflows` metodu do třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="3087a-252">Add the following `ListPersistedWorkflows` method to the form class.</span></span>  
  
    ```vb  
    Private Sub ListPersistedWorkflows()  
        Using localCon As New SqlConnection(connectionString)  
            Dim localCmd As String = _  
                "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]"  
  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
  
                While (reader.Read())  
                    'Get the InstanceId of the persisted Workflow.  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
                    InstanceId.Items.Add(id)  
                End While  
            End Using  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    using (SqlConnection localCon = new SqlConnection(connectionString))  
    {  
        string localCmd =  
            "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]";  
  
        SqlCommand cmd = localCon.CreateCommand();  
        cmd.CommandText = localCmd;  
        localCon.Open();  
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
        {  
            while (reader.Read())  
            {  
                // Get the InstanceId of the persisted Workflow  
                Guid id = Guid.Parse(reader[0].ToString());  
                InstanceId.Items.Add(id);  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="3087a-253">`ListPersistedWorkflows` dotazy v úložišti instancí pro instance trvalá pracovního postupu a přidá ID instance do `cboInstanceId` – pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="3087a-253">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>  
  
10. <span data-ttu-id="3087a-254">Přidejte následující `UpdateStatus` metoda a odpovídající delegát třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="3087a-254">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="3087a-255">Tato metoda aktualizuje stav aktuálně spuštěné pracovního postupu stavové okno, ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="3087a-255">This method updates the status window on the form with the status of the currently running workflow.</span></span>  
  
    ```vb  
    Private Delegate Sub UpdateStatusDelegate(msg As String)  
    Public Sub UpdateStatus(msg As String)  
        'We may be on a different thread so we need to  
        'make this call using BeginInvoke.  
        If InvokeRequired Then  
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)  
        Else  
            If Not msg.EndsWith(vbCrLf) Then  
                msg = msg & vbCrLf  
            End If  
  
            WorkflowStatus.AppendText(msg)  
  
            'Ensure that the newly added status is visible.  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length  
            WorkflowStatus.ScrollToCaret()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void UpdateStatusDelegate(string msg);  
    public void UpdateStatus(string msg)  
    {  
        // We may be on a different thread so we need to  
        // make this call using BeginInvoke.  
        if (InvokeRequired)  
        {  
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);  
        }  
        else  
        {  
            if (!msg.EndsWith("\r\n"))  
            {  
                msg += "\r\n";  
            }  
            WorkflowStatus.AppendText(msg);  
  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;  
            WorkflowStatus.ScrollToCaret();  
        }  
    }  
    ```  
  
11. <span data-ttu-id="3087a-256">Přidejte následující `GameOver` metoda a odpovídající delegát třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="3087a-256">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="3087a-257">Po dokončení pracovního postupu, tato metoda aktualizuje formulář, uživatelského rozhraní tak, že odeberete id instance pracovního postupu dokončená z **InstanceId** – pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="3087a-257">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>  
  
    ```vb  
    Private Delegate Sub GameOverDelegate()  
    Private Sub GameOver()  
        If InvokeRequired Then  
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))  
        Else  
            'Remove this instance from the InstanceId combo box.  
            InstanceId.Items.Remove(InstanceId.SelectedItem)  
            InstanceId.SelectedIndex = -1  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void GameOverDelegate();  
    private void GameOver()  
    {  
        if (InvokeRequired)  
        {  
            BeginInvoke(new GameOverDelegate(GameOver));  
        }  
        else  
        {  
            // Remove this instance from the combo box  
            InstanceId.Items.Remove(InstanceId.SelectedItem);  
            InstanceId.SelectedIndex = -1;  
        }  
    }  
    ```  
  
###  <a name="BKMK_ConfigureWorkflowApplication"></a> <span data-ttu-id="3087a-258">Ke konfiguraci úložiště instancí, obslužné rutiny pracovních postupů životního cyklu a rozšíření</span><span class="sxs-lookup"><span data-stu-id="3087a-258">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>  
  
1.  <span data-ttu-id="3087a-259">Přidat `ConfigureWorkflowApplication` metodu do třídy formuláře.</span><span class="sxs-lookup"><span data-stu-id="3087a-259">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     <span data-ttu-id="3087a-260">Tato metoda nakonfiguruje `WorkflowApplication`, přidá požadované rozšíření a přidá obslužné rutiny pro pracovní postup události životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="3087a-260">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>  
  
2.  <span data-ttu-id="3087a-261">V `ConfigureWorkflowApplication`, zadejte `SqlWorkflowInstanceStore` pro `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="3087a-261">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3.  <span data-ttu-id="3087a-262">Dále vytvořte `StringWriter` instance a přidejte ho do `Extensions` kolekce `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="3087a-262">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="3087a-263">Když `StringWriter` se přidá do rozšíření zachytí všechny `WriteLine` výstup aktivity.</span><span class="sxs-lookup"><span data-stu-id="3087a-263">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="3087a-264">Při pracovního postupu změní nečinnosti, `WriteLine` výstup může být extrahována z `StringWriter` a zobrazí ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="3087a-264">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>  
  
    ```vb  
    'Add a StringWriter to the extensions. This captures the output  
    'from the WriteLine activities so we can display it in the form.  
    Dim sw As New StringWriter()  
    wfApp.Extensions.Add(sw)  
    ```  
  
    ```csharp  
    // Add a StringWriter to the extensions. This captures the output  
    // from the WriteLine activities so we can display it in the form.  
    StringWriter sw = new StringWriter();  
    wfApp.Extensions.Add(sw);  
    ```  
  
4.  <span data-ttu-id="3087a-265">Přidejte následující obslužnou rutinu pro `Completed` událostí.</span><span class="sxs-lookup"><span data-stu-id="3087a-265">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="3087a-266">Po úspěšném dokončení pracovního postupu změní počet přijatých uhodnutelné číslo se zobrazí v okně Stav.</span><span class="sxs-lookup"><span data-stu-id="3087a-266">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="3087a-267">Pokud pracovní postup ukončí, zobrazí se informace o výjimce, která způsobila ukončení.</span><span class="sxs-lookup"><span data-stu-id="3087a-267">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="3087a-268">Na konci obslužné rutiny `GameOver` metoda je volána, která odebere ze seznamu pracovní postup dokončený pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="3087a-268">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>  
  
    ```vb  
    wfApp.Completed = _  
        Sub(e As WorkflowApplicationCompletedEventArgs)  
            If e.CompletionState = ActivityInstanceState.Faulted Then  
                UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                    e.TerminationException.GetType().FullName, _  
                    e.TerminationException.Message))  
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                UpdateStatus("Workflow Canceled.")  
            Else  
                Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
            End If  
            GameOver()  
        End Sub  
    ```  
  
    ```csharp  
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
    {  
        if (e.CompletionState == ActivityInstanceState.Faulted)  
        {  
            UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                e.TerminationException.GetType().FullName,  
                e.TerminationException.Message));  
        }  
        else if (e.CompletionState == ActivityInstanceState.Canceled)  
        {  
            UpdateStatus("Workflow Canceled.");  
        }  
        else  
        {  
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
            UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
        }  
        GameOver();  
    };  
    ```  
  
5.  <span data-ttu-id="3087a-269">Přidejte následující `Aborted` a `OnUnhandledException` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="3087a-269">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="3087a-270">`GameOver` Metoda není volána z `Aborted` obslužná rutina protože při instanci pracovního postupu byla přerušena, nebyl ukončen a je možné obnovit instanci později.</span><span class="sxs-lookup"><span data-stu-id="3087a-270">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>  
  
    ```vb  
    wfApp.Aborted = _  
        Sub(e As WorkflowApplicationAbortedEventArgs)  
            UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                e.Reason.GetType().FullName, _  
                e.Reason.Message))  
        End Sub  
  
    wfApp.OnUnhandledException = _  
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
            UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                e.UnhandledException.GetType().FullName, _  
                e.UnhandledException.Message))  
            GameOver()  
            Return UnhandledExceptionAction.Terminate  
        End Function  
    ```  
  
    ```csharp  
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
    {  
        UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                e.Reason.GetType().FullName,  
                e.Reason.Message));  
    };  
  
    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
    {  
        UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                e.UnhandledException.GetType().FullName,  
                e.UnhandledException.Message));  
        GameOver();  
        return UnhandledExceptionAction.Terminate;  
    };  
    ```  
  
6.  <span data-ttu-id="3087a-271">Přidejte následující `PersistableIdle` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="3087a-271">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="3087a-272">Tato obslužná rutina načte `StringWriter` rozšíření, které jste přidali, extrahuje výstup `WriteLine` aktivity a zobrazí jej v okně Stav.</span><span class="sxs-lookup"><span data-stu-id="3087a-272">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>  
  
    ```vb  
    wfApp.PersistableIdle = _  
        Function(e As WorkflowApplicationIdleEventArgs)  
            'Send the current WriteLine outputs to the status window.  
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
            For Each writer In writers  
                UpdateStatus(writer.ToString())  
            Next  
            Return PersistableIdleAction.Unload  
        End Function  
    ```  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        // Send the current WriteLine outputs to the status window.  
        var writers = e.GetInstanceExtensions<StringWriter>();  
        foreach (var writer in writers)  
        {  
            UpdateStatus(writer.ToString());  
        }  
        return PersistableIdleAction.Unload;  
    };  
    ```  
  
     <span data-ttu-id="3087a-273"><xref:System.Activities.PersistableIdleAction> Výčet má tři hodnoty: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, a <xref:System.Activities.PersistableIdleAction.Unload>.</span><span class="sxs-lookup"><span data-stu-id="3087a-273">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="3087a-274"><xref:System.Activities.PersistableIdleAction.Persist> způsobí, že pracovní postup a zachová jej ale nezpůsobí odpojení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3087a-274"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="3087a-275"><xref:System.Activities.PersistableIdleAction.Unload> způsobí, že pracovní postup zachovat a být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="3087a-275"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>  
  
     <span data-ttu-id="3087a-276">V následujícím příkladu je dokončené `ConfigureWorkflowApplication` metody.</span><span class="sxs-lookup"><span data-stu-id="3087a-276">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        wfApp.Completed = _  
            Sub(e As WorkflowApplicationCompletedEventArgs)  
                If e.CompletionState = ActivityInstanceState.Faulted Then  
                    UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                        e.TerminationException.GetType().FullName, _  
                        e.TerminationException.Message))  
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                    UpdateStatus("Workflow Canceled.")  
                Else  
                    Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                    UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
                End If  
                GameOver()  
            End Sub  
  
        wfApp.Aborted = _  
            Sub(e As WorkflowApplicationAbortedEventArgs)  
                UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                    e.Reason.GetType().FullName, _  
                    e.Reason.Message))  
            End Sub  
  
        wfApp.OnUnhandledException = _  
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
                UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                    e.UnhandledException.GetType().FullName, _  
                    e.UnhandledException.Message))  
                GameOver()  
                Return UnhandledExceptionAction.Terminate  
            End Function  
  
        wfApp.PersistableIdle = _  
            Function(e As WorkflowApplicationIdleEventArgs)  
                'Send the current WriteLine outputs to the status window.  
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
                For Each writer In writers  
                    UpdateStatus(writer.ToString())  
                Next  
                Return PersistableIdleAction.Unload  
            End Function  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
        {  
            if (e.CompletionState == ActivityInstanceState.Faulted)  
            {  
                UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                    e.TerminationException.GetType().FullName,  
                    e.TerminationException.Message));  
            }  
            else if (e.CompletionState == ActivityInstanceState.Canceled)  
            {  
                UpdateStatus("Workflow Canceled.");  
            }  
            else  
            {  
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
                UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
            }  
            GameOver();  
        };  
  
        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
        {  
            UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                    e.Reason.GetType().FullName,  
                    e.Reason.Message));  
        };  
  
        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                    e.UnhandledException.GetType().FullName,  
                    e.UnhandledException.Message));  
            GameOver();  
            return UnhandledExceptionAction.Terminate;  
        };  
  
        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
        {  
            // Send the current WriteLine outputs to the status window.  
            var writers = e.GetInstanceExtensions<StringWriter>();  
            foreach (var writer in writers)  
            {  
                UpdateStatus(writer.ToString());  
            }  
            return PersistableIdleAction.Unload;  
        };  
    }  
    ```  
  
###  <a name="BKMK_WorkflowVersionMap"></a> <span data-ttu-id="3087a-277">Povolit spuštění a obnovení více typy pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="3087a-277">To enable starting and resuming multiple workflow types</span></span>  
 <span data-ttu-id="3087a-278">Aby bylo možné obnovit do instance pracovního postupu, že hostitel má poskytnout definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3087a-278">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="3087a-279">V tomto kurzu jsou tři typy pracovních postupů a dalších kroků kurzu zavést více verzí z těchto typů.</span><span class="sxs-lookup"><span data-stu-id="3087a-279">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="3087a-280">`WorkflowIdentity` poskytuje způsob pro hostitelskou aplikaci přidružit identifikační údaje trvalé instance práce.</span><span class="sxs-lookup"><span data-stu-id="3087a-280">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="3087a-281">Kroky v této části ukazují, jak vytvořit nástroj třídu, která vám pomůže s mapování identita pracovního postupu z trvalé instance práce na odpovídající definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3087a-281">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="3087a-282">Další informace o `WorkflowIdentity` a správy verzí, naleznete v tématu [použití WorkflowIdentity a správy verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="3087a-282">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span></span>  
  
1.  <span data-ttu-id="3087a-283">Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **přidat**, **třídy**.</span><span class="sxs-lookup"><span data-stu-id="3087a-283">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="3087a-284">Typ `WorkflowVersionMap` do **název** pole a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="3087a-284">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>  
  
2.  <span data-ttu-id="3087a-285">Přidejte následující `using` nebo `Imports` příkazů v horní části souboru k ostatním `using` nebo `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="3087a-285">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3.  <span data-ttu-id="3087a-286">Nahradit `WorkflowVersionMap` deklarace s následující deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="3087a-286">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {          
            return identity.ToString();  
       }  
    }  
    ```  
  
     <span data-ttu-id="3087a-287">`WorkflowVersionMap` obsahuje tři identity pracovního postupu, které se mapují do tří definice pracovního postupu z tohoto kurzu a používá v následujících částech se při zahájení a obnovení pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="3087a-287">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>  
  
###  <a name="BKMK_StartWorkflow"></a> <span data-ttu-id="3087a-288">Spuštění nového pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3087a-288">To start a new workflow</span></span>  
  
1.  <span data-ttu-id="3087a-289">Přidat `Click` obslužné rutiny pro `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="3087a-289">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="3087a-290">Chcete-li přidat obslužnou rutinu, přepněte **návrhové zobrazení** pro formulář a dvakrát klikněte na `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="3087a-290">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="3087a-291">A `NewGame_Click` přidání obslužné rutiny a zobrazení se přepne do zobrazení kódu pro formulář.</span><span class="sxs-lookup"><span data-stu-id="3087a-291">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="3087a-292">Pokaždé, když uživatel stiskne toto tlačítko je spuštěn nový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="3087a-292">Whenever the user clicks this button a new workflow is started.</span></span>  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="3087a-293">Přidejte následující kód do obslužné rutiny kliknutí.</span><span class="sxs-lookup"><span data-stu-id="3087a-293">Add the following code to the click handler.</span></span> <span data-ttu-id="3087a-294">Tento kód vytvoří slovník vstupní argumenty pro pracovní postup, s klíči název argumentu.</span><span class="sxs-lookup"><span data-stu-id="3087a-294">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="3087a-295">Tento slovník obsahuje jednu položku, která obsahuje řadu náhodně generované číslo z rozsahu pole se seznamem načíst.</span><span class="sxs-lookup"><span data-stu-id="3087a-295">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3.  <span data-ttu-id="3087a-296">V dalším kroku přidejte následující kód, který se spustí pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="3087a-296">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="3087a-297">`WorkflowIdentity` a odpovídající typu pracovního postupu vybrali definice pracovního postupu se načítají pomocí `WorkflowVersionMap` pomocná třída.</span><span class="sxs-lookup"><span data-stu-id="3087a-297">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="3087a-298">Další, nové `WorkflowApplication` pomocí definice pracovního postupu je vytvořena instance `WorkflowIdentity`a slovníku vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="3087a-298">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>  
  
    ```vb  
    Dim identity As WorkflowIdentity = Nothing  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
    End Select  
  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
    Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
    ```  
  
    ```csharp  
    WorkflowIdentity identity = null;  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
    };  
  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
    ```  
  
4.  <span data-ttu-id="3087a-299">Dále přidejte následující kód, který přidá pracovní postup do seznamu pracovního postupu a zobrazí informace o verzi pro pracovní postupy ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="3087a-299">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>  
  
    ```vb  
    'Add the workflow to the list and display the version information.  
    WorkflowStarting = True  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
    WorkflowVersion.Text = identity.ToString()  
    WorkflowStarting = False  
    ```  
  
    ```csharp  
    // Add the workflow to the list and display the version information.  
    WorkflowStarting = true;  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
    WorkflowVersion.Text = identity.ToString();  
    WorkflowStarting = false;  
    ```  
  
5.  <span data-ttu-id="3087a-300">Volání `ConfigureWorkflowApplication` konfigurace instance úložiště, rozšíření a pracovních postupů životního cyklu obslužných rutin pro tento `WorkflowApplication` instance.</span><span class="sxs-lookup"><span data-stu-id="3087a-300">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>  
  
    ```vb  
    'Configure the instance store, extensions, and   
    'workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
    ```  
  
    ```csharp  
    // Configure the instance store, extensions, and   
    // workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp);  
    ```  
  
6.  <span data-ttu-id="3087a-301">Nakonec proveďte volání `Run`.</span><span class="sxs-lookup"><span data-stu-id="3087a-301">Finally, call `Run`.</span></span>  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     <span data-ttu-id="3087a-302">V následujícím příkladu je dokončené `NewGame_Click` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="3087a-302">The following example is the completed `NewGame_Click` handler.</span></span>  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
        'Start a new workflow.  
        Dim inputs As New Dictionary(Of String, Object)()  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
  
        Dim identity As WorkflowIdentity = Nothing  
        Select Case WorkflowType.SelectedItem.ToString()  
            Case "SequentialNumberGuessWorkflow"  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
            Case "StateMachineNumberGuessWorkflow"  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
            Case "FlowchartNumberGuessWorkflow"  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
        End Select  
  
        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
        Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
  
        'Add the workflow to the list and display the version information.  
        WorkflowStarting = True  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
        WorkflowVersion.Text = identity.ToString()  
        WorkflowStarting = False  
  
        'Configure the instance store, extensions, and   
        'workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Start the workflow.  
        wfApp.Run()  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
        var inputs = new Dictionary<string, object>();  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
  
        WorkflowIdentity identity = null;  
        switch (WorkflowType.SelectedItem.ToString())  
        {  
            case "SequentialNumberGuessWorkflow":  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
                break;  
  
            case "StateMachineNumberGuessWorkflow":  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
                break;  
  
            case "FlowchartNumberGuessWorkflow":  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
                break;  
        };  
  
        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
        WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
  
        // Add the workflow to the list and display the version information.  
        WorkflowStarting = true;  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
        WorkflowVersion.Text = identity.ToString();  
        WorkflowStarting = false;  
  
        // Configure the instance store, extensions, and   
        // workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Start the workflow.  
        wfApp.Run();  
    }  
    ```  
  
###  <a name="BKMK_ResumeWorkflow"></a> <span data-ttu-id="3087a-303">Pracovní postup obnovit</span><span class="sxs-lookup"><span data-stu-id="3087a-303">To resume a workflow</span></span>  
  
1.  <span data-ttu-id="3087a-304">Přidat `Click` obslužné rutiny pro `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="3087a-304">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="3087a-305">Chcete-li přidat obslužnou rutinu, přepněte **návrhové zobrazení** pro formulář a dvakrát klikněte na `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="3087a-305">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="3087a-306">Pokaždé, když uživatel stiskne toto tlačítko se obnoví pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="3087a-306">Whenever the user clicks this button a workflow is resumed.</span></span>  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="3087a-307">Přidejte následující kód k zajištění, že pracovní postup je vybrali v seznamu pracovního postupu a že odhad uživatele je platný.</span><span class="sxs-lookup"><span data-stu-id="3087a-307">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim userGuess As Integer  
    If Not Int32.TryParse(Guess.Text, userGuess) Then  
        MessageBox.Show("Please enter an integer.")  
        Guess.SelectAll()  
        Guess.Focus()  
        Return  
    End If  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    int guess;  
    if (!Int32.TryParse(Guess.Text, out guess))  
    {  
        MessageBox.Show("Please enter an integer.");  
        Guess.SelectAll();  
        Guess.Focus();  
        return;  
    }  
    ```  
  
3.  <span data-ttu-id="3087a-308">V dalším kroku načíst `WorkflowApplicationInstance` instance trvalá pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3087a-308">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="3087a-309">A `WorkflowApplicationInstance` představuje trvalé instance práce, který ještě nebyl přidružen s definicí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3087a-309">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="3087a-310">`DefinitionIdentity` z `WorkflowApplicationInstance` obsahuje `WorkflowIdentity` instance trvalá pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3087a-310">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="3087a-311">V tomto kurzu `WorkflowVersionMap` utility třída se používá k mapování `WorkflowIdentity` k definici pracovního postupu správné.</span><span class="sxs-lookup"><span data-stu-id="3087a-311">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="3087a-312">Jakmile je načtena definice pracovního postupu, `WorkflowApplication` je vytvořený pomocí definice pracovního postupu správné.</span><span class="sxs-lookup"><span data-stu-id="3087a-312">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>  
  
    ```vb  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = _  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
    ```  
  
    ```csharp  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf =  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
    ```  
  
4.  <span data-ttu-id="3087a-313">Jakmile `WorkflowApplication` je vytvořený, nakonfigurujte úložiště instancí, obslužné rutiny pracovních postupů životního cyklu a rozšíření voláním `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="3087a-313">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="3087a-314">Tyto kroky je nutné provést pokaždé, když se nový `WorkflowApplication` se vytvoří a je třeba provést před načtením do instance pracovního postupu `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="3087a-314">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="3087a-315">Po načtení pracovního postupu se obnoví se uživatele.</span><span class="sxs-lookup"><span data-stu-id="3087a-315">After the workflow is loaded, it is resumed with the user's guess.</span></span>  
  
    ```vb  
    'Configure the extensions and lifecycle handlers.  
    'Do this before the instance is loaded. Once the instance is  
    'loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", userGuess)  
    ```  
  
    ```csharp  
    // Configure the extensions and lifecycle handlers.  
    // Do this before the instance is loaded. Once the instance is  
    // loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", guess);  
    ```  
  
5.  <span data-ttu-id="3087a-316">A konečně zrušte textové pole odhad a připravte formuláře tak, aby přijímal jiného odhad.</span><span class="sxs-lookup"><span data-stu-id="3087a-316">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>  
  
    ```vb  
    'Clear the Guess textbox.  
    Guess.Clear()  
    Guess.Focus()  
    ```  
  
    ```csharp  
    // Clear the Guess textbox.  
    Guess.Clear();  
    Guess.Focus();  
    ```  
  
     <span data-ttu-id="3087a-317">V následujícím příkladu je dokončené `EnterGuess_Click` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="3087a-317">The following example is the completed `EnterGuess_Click` handler.</span></span>  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
        If WorkflowInstanceId = Guid.Empty Then  
            MessageBox.Show("Please select a workflow.")  
            Return  
        End If  
  
        Dim userGuess As Integer  
        If Not Int32.TryParse(Guess.Text, userGuess) Then  
            MessageBox.Show("Please enter an integer.")  
            Guess.SelectAll()  
            Guess.Focus()  
            Return  
        End If  
  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        'Use the persisted WorkflowIdentity to retrieve the correct workflow  
        'definition from the dictionary.  
        Dim wf As Activity = _  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
        'Associate the WorkflowApplication with the correct definition  
        Dim wfApp As WorkflowApplication = _  
            New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
        'Configure the extensions and lifecycle handlers.  
        'Do this before the instance is loaded. Once the instance is  
        'loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Load the workflow.  
        wfApp.Load(instance)  
  
        'Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", userGuess)  
  
        'Clear the Guess textbox.  
        Guess.Clear()  
        Guess.Focus()  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
        if (WorkflowInstanceId == Guid.Empty)  
        {  
            MessageBox.Show("Please select a workflow.");  
            return;  
        }  
  
        int guess;  
        if (!Int32.TryParse(Guess.Text, out guess))  
        {  
            MessageBox.Show("Please enter an integer.");  
            Guess.SelectAll();  
            Guess.Focus();  
            return;  
        }  
  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
        // Use the persisted WorkflowIdentity to retrieve the correct workflow  
        // definition from the dictionary.  
        Activity wf =  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
        // Associate the WorkflowApplication with the correct definition  
        WorkflowApplication wfApp =  
            new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
        // Configure the extensions and lifecycle handlers.  
        // Do this before the instance is loaded. Once the instance is  
        // loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Load the workflow.  
        wfApp.Load(instance);  
  
        // Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", guess);  
  
        // Clear the Guess textbox.  
        Guess.Clear();  
        Guess.Focus();  
    }  
    ```  
  
###  <a name="BKMK_TerminateWorkflow"></a> <span data-ttu-id="3087a-318">K ukončení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3087a-318">To terminate a workflow</span></span>  
  
1.  <span data-ttu-id="3087a-319">Přidat `Click` obslužné rutiny pro `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="3087a-319">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="3087a-320">Chcete-li přidat obslužnou rutinu, přepněte **návrhové zobrazení** pro formulář a dvakrát klikněte na `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="3087a-320">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="3087a-321">Pokaždé, když uživatel stiskne toto tlačítko se ukončí aktuálně vybraného pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3087a-321">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  <span data-ttu-id="3087a-322">Přidejte následující kód, který `QuitGame_Click` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="3087a-322">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="3087a-323">Tento kód nejprve zkontroluje, zda pracovní postup je vybrán v seznamu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3087a-323">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="3087a-324">Následně načte do trvalé instanci `WorkflowApplicationInstance`, používá `DefinitionIdentity` k určení definice pracovního postupu správný a potom inicializuje `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="3087a-324">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="3087a-325">Další rozšíření a obslužné rutiny pracovních postupů životního cyklu jsou nakonfigurovány s volání `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="3087a-325">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="3087a-326">Jednou `WorkflowApplication` je nakonfigurován, je načten a potom `Terminate` je volána.</span><span class="sxs-lookup"><span data-stu-id="3087a-326">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition.  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
    'Configure the extensions and lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Terminate the workflow.  
    wfApp.Terminate("User resigns.")  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
    // Configure the extensions and lifecycle handlers  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Terminate the workflow.  
    wfApp.Terminate("User resigns.");  
    ```  
  
###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="3087a-327">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="3087a-327">To build and run the application</span></span>  
  
1.  <span data-ttu-id="3087a-328">Dvakrát klikněte na panel **Program.cs** (nebo **Module1.vb**) v **Průzkumníka řešení** zobrazíte kód této.</span><span class="sxs-lookup"><span data-stu-id="3087a-328">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>  
  
2.  <span data-ttu-id="3087a-329">Přidejte následující `using` (nebo `Imports`) příkaz v horní části souboru k ostatním `using` (nebo `Imports`) příkazy.</span><span class="sxs-lookup"><span data-stu-id="3087a-329">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  <span data-ttu-id="3087a-330">Odstranit nebo okomentovat hostování kódu z existujícího pracovního postupu [postupy: spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)a nahraďte ho následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="3087a-330">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md), and replace it with the following code.</span></span>  
  
    ```vb  
    Sub Main()  
        Application.EnableVisualStyles()  
        Application.Run(New WorkflowHostForm())  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Application.EnableVisualStyles();  
        Application.Run(new WorkflowHostForm());  
    }  
    ```  
  
4.  <span data-ttu-id="3087a-331">Klikněte pravým tlačítkem na **NumberGuessWorkflowHost** v **Průzkumníka řešení** a zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="3087a-331">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="3087a-332">V **aplikace** kartu, zadejte **aplikace Windows** pro **typ výstupu**.</span><span class="sxs-lookup"><span data-stu-id="3087a-332">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="3087a-333">Tento krok je volitelný, ale pokud se nedodrží kromě formuláři se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="3087a-333">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>  
  
5.  <span data-ttu-id="3087a-334">Stiskněte kombinaci kláves Ctrl + Shift + B pro sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="3087a-334">Press Ctrl+Shift+B to build the application.</span></span>  
  
6.  <span data-ttu-id="3087a-335">Ujistěte se, že **NumberGuessWorkflowHost** je nastavena jako při spuštění aplikace a stiskněte klávesu Ctrl + F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3087a-335">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>  
  
7.  <span data-ttu-id="3087a-336">Vyberte oblast pro využití herních a typ pracovního postupu ke spouštění a klikněte na tlačítko **nová hra**.</span><span class="sxs-lookup"><span data-stu-id="3087a-336">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="3087a-337">Zadejte odhad v **odhad** pole a klikněte na tlačítko **Přejít** k odeslání vašeho odhadu.</span><span class="sxs-lookup"><span data-stu-id="3087a-337">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="3087a-338">Všimněte si, že výstup `WriteLine` aktivity se zobrazí ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="3087a-338">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>  
  
8.  <span data-ttu-id="3087a-339">Spustit několik pracovních postupů pomocí pracovního postupu různé typy a počet rozsahů, zadejte několik pokusů a přepínání pracovních postupů tak, že vyberete **Id Instance pracovního postupu** seznamu.</span><span class="sxs-lookup"><span data-stu-id="3087a-339">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>  
  
     <span data-ttu-id="3087a-340">Všimněte si, že když přepnete do nového pracovního postupu, předchozí pokusů a průběh pracovního postupu nejsou zobrazeny v okně Stav.</span><span class="sxs-lookup"><span data-stu-id="3087a-340">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="3087a-341">Z důvodů, proč stavu není k dispozici je, protože není zachycena a uloženy kdekoli.</span><span class="sxs-lookup"><span data-stu-id="3087a-341">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="3087a-342">V dalším kroku kurzu [postupy: vytvoření vlastního účastníka sledování](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), vytvoření vlastního účastníka sledování, která ukládá tyto informace.</span><span class="sxs-lookup"><span data-stu-id="3087a-342">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
