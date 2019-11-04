---
title: 'Postupy: vytvoření a spuštění dlouhého běžícího pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: e5083b3d12cecc395500ef13405effa7b7e51633
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420621"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="6eda9-102">Postupy: vytvoření a spuštění dlouhého běžícího pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-102">How to: Create and Run a Long Running Workflow</span></span>

<span data-ttu-id="6eda9-103">Jednou z ústředních funkcí programovací model Windows Workflow Foundation (WF) je schopnost modulu runtime uchovávat a uvolňovat nečinné pracovní postupy do databáze.</span><span class="sxs-lookup"><span data-stu-id="6eda9-103">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="6eda9-104">Postup, [Jak spustit pracovní postup: spuštění pracovního postupu](how-to-run-a-workflow.md) ukázal základy hostování pracovního postupu pomocí konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6eda9-104">The steps in [How to: Run a Workflow](how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="6eda9-105">V příkladech se zobrazily počáteční pracovní postupy, obslužné rutiny životního cyklu pracovního postupu a obnovení záložek.</span><span class="sxs-lookup"><span data-stu-id="6eda9-105">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="6eda9-106">Aby bylo možné předvést trvalost pracovního postupu efektivně, je zapotřebí složitější hostitel pracovního postupu, který podporuje spouštění a obnovování více instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-106">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="6eda9-107">Tento krok v tomto kurzu ukazuje, jak vytvořit hostitelskou aplikaci Windows Form, která podporuje spouštění a obnovování více instancí pracovního postupu, trvalý pracovní postup a poskytuje základ pro pokročilé funkce, jako je například sledování a správa verzí, které jsou znázorněné v dalších krocích kurzu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-107">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>

> [!NOTE]
> <span data-ttu-id="6eda9-108">Tento krok kurzu a následné kroky používají všechny tři typy pracovních postupů v tématu [Postupy: vytvoření pracovního postupu](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="6eda9-108">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span> <span data-ttu-id="6eda9-109">Pokud jste nedokončili všechny tři typy, můžete si stáhnout dokončenou verzi kroků z [programovací model Windows Workflow Foundation (WF45) – začínáme kurzu](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="6eda9-109">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

> [!NOTE]
> <span data-ttu-id="6eda9-110">Pokud si chcete stáhnout dokončenou verzi nebo zobrazit návod k videu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="6eda9-110">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="6eda9-111">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="6eda9-111">In this topic</span></span>

- [<span data-ttu-id="6eda9-112">Vytvoření databáze trvalosti</span><span class="sxs-lookup"><span data-stu-id="6eda9-112">To create the persistence database</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)

- [<span data-ttu-id="6eda9-113">Přidání odkazu na DurableInstancing sestavení</span><span class="sxs-lookup"><span data-stu-id="6eda9-113">To add the reference to the DurableInstancing assemblies</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)

- [<span data-ttu-id="6eda9-114">Vytvoření formuláře hostitele pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-114">To create the workflow host form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)

- [<span data-ttu-id="6eda9-115">Přidání vlastností a pomocných metod formuláře</span><span class="sxs-lookup"><span data-stu-id="6eda9-115">To add the properties and helper methods of the form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)

- [<span data-ttu-id="6eda9-116">Konfigurace úložiště instancí, obslužných rutin životního cyklu pracovního postupu a rozšíření</span><span class="sxs-lookup"><span data-stu-id="6eda9-116">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)

- [<span data-ttu-id="6eda9-117">Povolení spouštění a obnovování více typů pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6eda9-117">To enable starting and resuming multiple workflow types</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)

- [<span data-ttu-id="6eda9-118">Spuštění nového pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-118">To start a new workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)

- [<span data-ttu-id="6eda9-119">Obnovení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-119">To resume a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)

- [<span data-ttu-id="6eda9-120">Ukončení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-120">To terminate a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)

- [<span data-ttu-id="6eda9-121">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="6eda9-121">To build and run the application</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)

### <a name="BKMK_CreatePersistenceDatabase"></a><span data-ttu-id="6eda9-122">Vytvoření databáze trvalosti</span><span class="sxs-lookup"><span data-stu-id="6eda9-122">To create the persistence database</span></span>

1. <span data-ttu-id="6eda9-123">Otevřete SQL Server Management Studio a připojte se k místnímu serveru, například **.\SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-123">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="6eda9-124">Pravým tlačítkem myši klikněte na uzel **databáze** na místním serveru a vyberte možnost **Nová databáze**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-124">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="6eda9-125">Pojmenujte novou databázi **WF45GettingStartedTutorial**, přijměte všechny ostatní hodnoty a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-125">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6eda9-126">Před vytvořením databáze se ujistěte, že máte na místním serveru oprávnění **vytvořit databázi** .</span><span class="sxs-lookup"><span data-stu-id="6eda9-126">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>

2. <span data-ttu-id="6eda9-127">V nabídce **soubor** vyberte **otevřít**, **soubor** .</span><span class="sxs-lookup"><span data-stu-id="6eda9-127">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="6eda9-128">Přejděte do následující složky: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="6eda9-128">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>

    <span data-ttu-id="6eda9-129">Vyberte následující dva soubory a klikněte na **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-129">Select the following two files and click **Open**.</span></span>

    - <span data-ttu-id="6eda9-130">SqlWorkflowInstanceStoreLogic. SQL</span><span class="sxs-lookup"><span data-stu-id="6eda9-130">SqlWorkflowInstanceStoreLogic.sql</span></span>

    - <span data-ttu-id="6eda9-131">SqlWorkflowInstanceStoreSchema. SQL</span><span class="sxs-lookup"><span data-stu-id="6eda9-131">SqlWorkflowInstanceStoreSchema.sql</span></span>

3. <span data-ttu-id="6eda9-132">V nabídce **okno** vyberte **SqlWorkflowInstanceStoreSchema. SQL** .</span><span class="sxs-lookup"><span data-stu-id="6eda9-132">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="6eda9-133">V rozevíracím seznamu **dostupné databáze** zkontrolujte, že je vybraná možnost **WF45GettingStartedTutorial** a v nabídce **dotaz** vyberte **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="6eda9-133">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

4. <span data-ttu-id="6eda9-134">V nabídce **okno** vyberte **SqlWorkflowInstanceStoreLogic. SQL** .</span><span class="sxs-lookup"><span data-stu-id="6eda9-134">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="6eda9-135">V rozevíracím seznamu **dostupné databáze** zkontrolujte, že je vybraná možnost **WF45GettingStartedTutorial** a v nabídce **dotaz** vyberte **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="6eda9-135">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

    > [!WARNING]
    > <span data-ttu-id="6eda9-136">Je důležité provést předchozí dva kroky ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6eda9-136">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="6eda9-137">Pokud jsou dotazy spouštěny mimo pořadí, dojde k chybám a databáze trvalosti není správně nakonfigurována.</span><span class="sxs-lookup"><span data-stu-id="6eda9-137">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>

### <a name="BKMK_AddReference"></a><span data-ttu-id="6eda9-138">Přidání odkazu na DurableInstancing sestavení</span><span class="sxs-lookup"><span data-stu-id="6eda9-138">To add the reference to the DurableInstancing assemblies</span></span>

1. <span data-ttu-id="6eda9-139">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-139">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>

2. <span data-ttu-id="6eda9-140">V seznamu **Přidat odkaz** vyberte **sestavení** a do pole **vyhledávací sestavení** zadejte `DurableInstancing`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-140">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="6eda9-141">To filtruje sestavení a usnadňuje výběr požadovaných odkazů.</span><span class="sxs-lookup"><span data-stu-id="6eda9-141">This filters the assemblies and makes the desired references easier to select.</span></span>

3. <span data-ttu-id="6eda9-142">Zaškrtněte políčko vedle položky **System. Activities. DurableInstancing** a **System. Runtime. DurableInstancing** ze seznamu **výsledků hledání** a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-142">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>

### <a name="BKMK_CreateForm"></a><span data-ttu-id="6eda9-143">Vytvoření formuláře hostitele pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-143">To create the workflow host form</span></span>

> [!NOTE]
> <span data-ttu-id="6eda9-144">Kroky v tomto postupu popisují, jak formulář Přidat a nakonfigurovat ručně.</span><span class="sxs-lookup"><span data-stu-id="6eda9-144">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="6eda9-145">V případě potřeby si můžete stáhnout soubory řešení pro kurz a přidat dokončený formulář do projektu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-145">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="6eda9-146">Pokud si chcete stáhnout soubory kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="6eda9-146">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="6eda9-147">Po stažení souborů klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-147">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="6eda9-148">Přidejte odkaz na **System. Windows. Forms** a **System. Drawing**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-148">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="6eda9-149">Tyto odkazy jsou přidány automaticky, pokud přidáte nový formulář z nabídky **Přidat**, **Nová položka** , ale je nutné jej přidat ručně při importu formuláře.</span><span class="sxs-lookup"><span data-stu-id="6eda9-149">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="6eda9-150">Až budou odkazy přidány, klikněte pravým tlačítkem myši na **NumberGuessWorkflowHost** v **Průzkumník řešení** a vyberte **Přidat**, **existující položka**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-150">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="6eda9-151">Přejděte do složky `Form` v souborech projektu, vyberte **WorkflowHostForm.cs** (nebo **WorkflowHostForm. vb**) a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-151">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="6eda9-152">Pokud se rozhodnete importovat formulář, můžete přeskočit dolů k další části a [Přidat vlastnosti a pomocné metody formuláře](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span><span class="sxs-lookup"><span data-stu-id="6eda9-152">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span></span>

1. <span data-ttu-id="6eda9-153">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat**, **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-153">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>

2. <span data-ttu-id="6eda9-154">V seznamu **nainstalované** šablony vyberte možnost **formulář Windows**, do pole **název** zadejte `WorkflowHostForm` a klikněte na tlačítko **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-154">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>

3. <span data-ttu-id="6eda9-155">Ve formuláři nakonfigurujte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6eda9-155">Configure the following properties on the form.</span></span>

    |<span data-ttu-id="6eda9-156">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="6eda9-156">Property</span></span>|<span data-ttu-id="6eda9-157">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6eda9-157">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="6eda9-158">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="6eda9-158">FormBorderStyle</span></span>|<span data-ttu-id="6eda9-159">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="6eda9-159">FixedSingle</span></span>|
    |<span data-ttu-id="6eda9-160">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="6eda9-160">MaximizeBox</span></span>|<span data-ttu-id="6eda9-161">False</span><span class="sxs-lookup"><span data-stu-id="6eda9-161">False</span></span>|
    |<span data-ttu-id="6eda9-162">Velikost</span><span class="sxs-lookup"><span data-stu-id="6eda9-162">Size</span></span>|<span data-ttu-id="6eda9-163">400, 420</span><span class="sxs-lookup"><span data-stu-id="6eda9-163">400, 420</span></span>|

4. <span data-ttu-id="6eda9-164">Do formuláře přidejte následující ovládací prvky v zadaném pořadí a nakonfigurujte vlastnosti jako směrované.</span><span class="sxs-lookup"><span data-stu-id="6eda9-164">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>

    |<span data-ttu-id="6eda9-165">Control</span><span class="sxs-lookup"><span data-stu-id="6eda9-165">Control</span></span>|<span data-ttu-id="6eda9-166">Vlastnost: hodnota</span><span class="sxs-lookup"><span data-stu-id="6eda9-166">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="6eda9-167">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="6eda9-167">**Button**</span></span>|<span data-ttu-id="6eda9-168">Název: NewGame</span><span class="sxs-lookup"><span data-stu-id="6eda9-168">Name: NewGame</span></span><br /><br /> <span data-ttu-id="6eda9-169">Umístění: 13, 13</span><span class="sxs-lookup"><span data-stu-id="6eda9-169">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="6eda9-170">Velikost: 75, 23</span><span class="sxs-lookup"><span data-stu-id="6eda9-170">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="6eda9-171">Text: nová hra</span><span class="sxs-lookup"><span data-stu-id="6eda9-171">Text: New Game</span></span>|
    |<span data-ttu-id="6eda9-172">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="6eda9-172">**Label**</span></span>|<span data-ttu-id="6eda9-173">Umístění: 94, 18</span><span class="sxs-lookup"><span data-stu-id="6eda9-173">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="6eda9-174">Text: vyodhaduje číslo od 1 do.</span><span class="sxs-lookup"><span data-stu-id="6eda9-174">Text: Guess a number from 1 to</span></span>|
    |<span data-ttu-id="6eda9-175">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="6eda9-175">**ComboBox**</span></span>|<span data-ttu-id="6eda9-176">Název: NumberRange</span><span class="sxs-lookup"><span data-stu-id="6eda9-176">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="6eda9-177">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="6eda9-177">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="6eda9-178">Položky: 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="6eda9-178">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="6eda9-179">Umístění: 228, 12</span><span class="sxs-lookup"><span data-stu-id="6eda9-179">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="6eda9-180">Velikost: 143, 21</span><span class="sxs-lookup"><span data-stu-id="6eda9-180">Size: 143, 21</span></span>|
    |<span data-ttu-id="6eda9-181">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="6eda9-181">**Label**</span></span>|<span data-ttu-id="6eda9-182">Umístění: 13, 43</span><span class="sxs-lookup"><span data-stu-id="6eda9-182">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="6eda9-183">Text: typ pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-183">Text: Workflow type</span></span>|
    |<span data-ttu-id="6eda9-184">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="6eda9-184">**ComboBox**</span></span>|<span data-ttu-id="6eda9-185">Název: WorkflowType</span><span class="sxs-lookup"><span data-stu-id="6eda9-185">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="6eda9-186">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="6eda9-186">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="6eda9-187">Položky: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="6eda9-187">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="6eda9-188">Umístění: 94, 40</span><span class="sxs-lookup"><span data-stu-id="6eda9-188">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="6eda9-189">Velikost: 277, 21</span><span class="sxs-lookup"><span data-stu-id="6eda9-189">Size: 277, 21</span></span>|
    |<span data-ttu-id="6eda9-190">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="6eda9-190">**Label**</span></span>|<span data-ttu-id="6eda9-191">Název: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="6eda9-191">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="6eda9-192">Umístění: 13, 362</span><span class="sxs-lookup"><span data-stu-id="6eda9-192">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="6eda9-193">Text: verze pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-193">Text: Workflow version</span></span>|
    |<span data-ttu-id="6eda9-194">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="6eda9-194">**GroupBox**</span></span>|<span data-ttu-id="6eda9-195">Umístění: 13, 67</span><span class="sxs-lookup"><span data-stu-id="6eda9-195">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="6eda9-196">Velikost: 358, 287</span><span class="sxs-lookup"><span data-stu-id="6eda9-196">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="6eda9-197">Text: hra</span><span class="sxs-lookup"><span data-stu-id="6eda9-197">Text: Game</span></span>|

    > [!NOTE]
    > <span data-ttu-id="6eda9-198">Při přidávání následujících ovládacích prvků Umístěte tyto ovládací prvky do skupinového rámečku.</span><span class="sxs-lookup"><span data-stu-id="6eda9-198">When adding the following controls, put them into the GroupBox.</span></span>

    |<span data-ttu-id="6eda9-199">Control</span><span class="sxs-lookup"><span data-stu-id="6eda9-199">Control</span></span>|<span data-ttu-id="6eda9-200">Vlastnost: hodnota</span><span class="sxs-lookup"><span data-stu-id="6eda9-200">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="6eda9-201">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="6eda9-201">**Label**</span></span>|<span data-ttu-id="6eda9-202">Umístění: 7, 20</span><span class="sxs-lookup"><span data-stu-id="6eda9-202">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="6eda9-203">Text: ID instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-203">Text: Workflow Instance Id</span></span>|
    |<span data-ttu-id="6eda9-204">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="6eda9-204">**ComboBox**</span></span>|<span data-ttu-id="6eda9-205">Název: InstanceId</span><span class="sxs-lookup"><span data-stu-id="6eda9-205">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="6eda9-206">DropDownStyle: DropDownList</span><span class="sxs-lookup"><span data-stu-id="6eda9-206">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="6eda9-207">Umístění: 121, 17</span><span class="sxs-lookup"><span data-stu-id="6eda9-207">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="6eda9-208">Velikost: 227, 21</span><span class="sxs-lookup"><span data-stu-id="6eda9-208">Size: 227, 21</span></span>|
    |<span data-ttu-id="6eda9-209">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="6eda9-209">**Label**</span></span>|<span data-ttu-id="6eda9-210">Umístění: 7, 47</span><span class="sxs-lookup"><span data-stu-id="6eda9-210">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="6eda9-211">Text: odhad</span><span class="sxs-lookup"><span data-stu-id="6eda9-211">Text: Guess</span></span>|
    |<span data-ttu-id="6eda9-212">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="6eda9-212">**TextBox**</span></span>|<span data-ttu-id="6eda9-213">Název: odhad</span><span class="sxs-lookup"><span data-stu-id="6eda9-213">Name: Guess</span></span><br /><br /> <span data-ttu-id="6eda9-214">Umístění: 50, 44</span><span class="sxs-lookup"><span data-stu-id="6eda9-214">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="6eda9-215">Velikost: 65, 20</span><span class="sxs-lookup"><span data-stu-id="6eda9-215">Size: 65, 20</span></span>|
    |<span data-ttu-id="6eda9-216">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="6eda9-216">**Button**</span></span>|<span data-ttu-id="6eda9-217">Název: EnterGuess</span><span class="sxs-lookup"><span data-stu-id="6eda9-217">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="6eda9-218">Umístění: 121, 42</span><span class="sxs-lookup"><span data-stu-id="6eda9-218">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="6eda9-219">Velikost: 75, 23</span><span class="sxs-lookup"><span data-stu-id="6eda9-219">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="6eda9-220">Text: zadejte odhad.</span><span class="sxs-lookup"><span data-stu-id="6eda9-220">Text: Enter Guess</span></span>|
    |<span data-ttu-id="6eda9-221">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="6eda9-221">**Button**</span></span>|<span data-ttu-id="6eda9-222">Název: QuitGame</span><span class="sxs-lookup"><span data-stu-id="6eda9-222">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="6eda9-223">Umístění: 274, 42</span><span class="sxs-lookup"><span data-stu-id="6eda9-223">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="6eda9-224">Velikost: 75, 23</span><span class="sxs-lookup"><span data-stu-id="6eda9-224">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="6eda9-225">Text: konec</span><span class="sxs-lookup"><span data-stu-id="6eda9-225">Text: Quit</span></span>|
    |<span data-ttu-id="6eda9-226">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="6eda9-226">**TextBox**</span></span>|<span data-ttu-id="6eda9-227">Název: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="6eda9-227">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="6eda9-228">Umístění: 10, 73</span><span class="sxs-lookup"><span data-stu-id="6eda9-228">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="6eda9-229">Víceřádkové: pravda</span><span class="sxs-lookup"><span data-stu-id="6eda9-229">Multiline: True</span></span><br /><br /> <span data-ttu-id="6eda9-230">Jen pro čtení: true</span><span class="sxs-lookup"><span data-stu-id="6eda9-230">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="6eda9-231">Posuvníky: svislé</span><span class="sxs-lookup"><span data-stu-id="6eda9-231">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="6eda9-232">Velikost: 338, 208</span><span class="sxs-lookup"><span data-stu-id="6eda9-232">Size: 338, 208</span></span>|

5. <span data-ttu-id="6eda9-233">Nastavte vlastnost **AcceptButton** formuláře na **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-233">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>

 <span data-ttu-id="6eda9-234">Následující příklad znázorňuje dokončený formulář.</span><span class="sxs-lookup"><span data-stu-id="6eda9-234">The following example illustrates the completed form.</span></span>

 ![Snímek obrazovky programovací model Windows Workflow Foundation formuláře hostitele pracovního postupu.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

### <a name="BKMK_AddHelperMethods"></a><span data-ttu-id="6eda9-236">Přidání vlastností a pomocných metod formuláře</span><span class="sxs-lookup"><span data-stu-id="6eda9-236">To add the properties and helper methods of the form</span></span>

<span data-ttu-id="6eda9-237">Kroky v této části přidávají vlastnosti a pomocné metody do třídy formuláře, která konfiguruje uživatelské rozhraní formuláře tak, aby podporovalo spouštění a obnovování počtu vyčíslení pro odhadované pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="6eda9-237">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>

1. <span data-ttu-id="6eda9-238">V **Průzkumník řešení** klikněte pravým tlačítkem na **WorkflowHostForm** a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-238">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>

2. <span data-ttu-id="6eda9-239">Do horní části souboru přidejte následující příkazy `using` (nebo `Imports`) s jinými příkazy `using` (nebo `Imports`).</span><span class="sxs-lookup"><span data-stu-id="6eda9-239">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

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

3. <span data-ttu-id="6eda9-240">Do třídy **WorkflowHostForm** přidejte následující deklarace členů.</span><span class="sxs-lookup"><span data-stu-id="6eda9-240">Add the following member declarations to the **WorkflowHostForm** class.</span></span>

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
    > <span data-ttu-id="6eda9-241">Pokud je váš připojovací řetězec jiný, aktualizujte `connectionString`, aby odkazovaly na vaši databázi.</span><span class="sxs-lookup"><span data-stu-id="6eda9-241">If your connection string is different, update `connectionString` to refer to your database.</span></span>

4. <span data-ttu-id="6eda9-242">Do `WorkflowFormHost` třídy přidejte vlastnost `WorkflowInstanceId`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-242">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>

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

    <span data-ttu-id="6eda9-243">V poli se seznamem `InstanceId` se zobrazí seznam trvalých ID instancí pracovního postupu a vlastnost `WorkflowInstanceId` vrací aktuálně vybraný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="6eda9-243">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>

5. <span data-ttu-id="6eda9-244">Přidejte obslužnou rutinu pro událost `Load` formuláře.</span><span class="sxs-lookup"><span data-stu-id="6eda9-244">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="6eda9-245">Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře, klikněte na ikonu **události** v horní části okna **vlastnosti** a dvakrát klikněte na položku **načíst**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-245">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. <span data-ttu-id="6eda9-246">Přidejte následující kód pro `WorkflowHostForm_Load`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-246">Add the following code to `WorkflowHostForm_Load`.</span></span>

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

    <span data-ttu-id="6eda9-247">Když se formulář načte, `SqlWorkflowInstanceStore` se nakonfigurují, rozsah a typ pracovního postupu se pole se seznamem nastaví na výchozí hodnoty a trvalé instance pracovního postupu se přidají do pole se seznamem `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-247">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>

7. <span data-ttu-id="6eda9-248">Přidejte obslužnou rutinu `SelectedIndexChanged` pro `InstanceId`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-248">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="6eda9-249">Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře, vyberte pole se seznamem `InstanceId`, klikněte na ikonu **události** v horní části okna **vlastnosti** a dvakrát klikněte na položku **SelectedIndexChanged**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-249">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. <span data-ttu-id="6eda9-250">Přidejte následující kód pro `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-250">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="6eda9-251">Vždy, když uživatel vybere pracovní postup pomocí pole se seznamem, tato obslužná rutina aktualizuje stavové okno.</span><span class="sxs-lookup"><span data-stu-id="6eda9-251">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>

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

9. <span data-ttu-id="6eda9-252">Do třídy Form přidejte následující metodu `ListPersistedWorkflows`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-252">Add the following `ListPersistedWorkflows` method to the form class.</span></span>

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

    <span data-ttu-id="6eda9-253">`ListPersistedWorkflows` se dotazuje úložiště instancí na trvalé instance pracovního postupu a přidá ID instance do pole se seznamem `cboInstanceId`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-253">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>

10. <span data-ttu-id="6eda9-254">Do třídy Form přidejte následující metodu `UpdateStatus` a odpovídající delegát.</span><span class="sxs-lookup"><span data-stu-id="6eda9-254">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="6eda9-255">Tato metoda aktualizuje stavové okno ve formuláři se stavem aktuálně spuštěného pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-255">This method updates the status window on the form with the status of the currently running workflow.</span></span>

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

11. <span data-ttu-id="6eda9-256">Do třídy Form přidejte následující metodu `GameOver` a odpovídající delegát.</span><span class="sxs-lookup"><span data-stu-id="6eda9-256">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="6eda9-257">Po dokončení pracovního postupu Tato metoda aktualizuje uživatelské rozhraní formuláře odebráním ID instance dokončeného pracovního postupu z pole se seznamem **InstanceId** .</span><span class="sxs-lookup"><span data-stu-id="6eda9-257">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>

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

### <a name="BKMK_ConfigureWorkflowApplication"></a><span data-ttu-id="6eda9-258">Konfigurace úložiště instancí, obslužných rutin životního cyklu pracovního postupu a rozšíření</span><span class="sxs-lookup"><span data-stu-id="6eda9-258">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>

1. <span data-ttu-id="6eda9-259">Do třídy formuláře přidejte metodu `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-259">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    <span data-ttu-id="6eda9-260">Tato metoda konfiguruje `WorkflowApplication`, přidá požadovaná rozšíření a přidá obslužné rutiny pro události životního cyklu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-260">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>

2. <span data-ttu-id="6eda9-261">V `ConfigureWorkflowApplication`zadejte `SqlWorkflowInstanceStore` pro `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-261">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>

    ```vb
    'Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. <span data-ttu-id="6eda9-262">Dále vytvořte instanci `StringWriter` a přidejte ji do kolekce `Extensions` `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-262">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="6eda9-263">Když se do rozšíření přidá `StringWriter`, zachytí se veškerý výstup aktivity `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-263">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="6eda9-264">Když se pracovní postup přestanou nečinný, může být výstup `WriteLine` z `StringWriter` extrahován a zobrazený ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="6eda9-264">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>

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

4. <span data-ttu-id="6eda9-265">Přidejte následující obslužnou rutinu pro událost `Completed`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-265">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="6eda9-266">Po úspěšném dokončení pracovního postupu se v okně stav zobrazí počet pokusů o odhadované číslo.</span><span class="sxs-lookup"><span data-stu-id="6eda9-266">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="6eda9-267">Pokud se pracovní postup ukončí, zobrazí se informace o výjimce, která způsobila ukončení.</span><span class="sxs-lookup"><span data-stu-id="6eda9-267">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="6eda9-268">Na konci obslužné rutiny je volána metoda `GameOver`, která odebere dokončený pracovní postup ze seznamu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-268">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>

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
                UpdateStatus($"Congratulations, you guessed the number in {Turns} turns.")
            End If
            GameOver()
        End Sub
    ```

    ```csharp
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)
    {
        if (e.CompletionState == ActivityInstanceState.Faulted)
        {
            UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
        }
        else if (e.CompletionState == ActivityInstanceState.Canceled)
        {
            UpdateStatus("Workflow Canceled.");
        }
        else
        {
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);
            UpdateStatus($"Congratulations, you guessed the number in {Turns} turns.");
        }
        GameOver();
    };
    ```

5. <span data-ttu-id="6eda9-269">Přidejte následující `Aborted` a `OnUnhandledException` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="6eda9-269">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="6eda9-270">Metoda `GameOver` není volána z obslužné rutiny `Aborted`, protože když je instance pracovního postupu přerušena, nekončí, a je možné instanci obnovit později.</span><span class="sxs-lookup"><span data-stu-id="6eda9-270">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>

    ```vb
    wfApp.Aborted = _
        Sub(e As WorkflowApplicationAbortedEventArgs)
            UpdateStatus($"Workflow Aborted. Exception: {0e.Reason.GetType().FullName}" & vbCrLf & $"{e.Reason.Message}")
        End Sub

    wfApp.OnUnhandledException = _
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}" & vbCrLf & $"{e.UnhandledException.Message}")
            GameOver()
            Return UnhandledExceptionAction.Terminate
        End Function
    ```

    ```csharp
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
    {
        UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
    };

    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
    {
        UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
        GameOver();
        return UnhandledExceptionAction.Terminate;
    };
    ```

6. <span data-ttu-id="6eda9-271">Přidejte následující obslužnou rutinu `PersistableIdle`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-271">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="6eda9-272">Tato obslužná rutina načte rozšíření `StringWriter`, které bylo přidáno, extrahuje výstup z aktivit `WriteLine` a zobrazí jej v okně stav.</span><span class="sxs-lookup"><span data-stu-id="6eda9-272">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>

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

    <span data-ttu-id="6eda9-273">Výčet <xref:System.Activities.PersistableIdleAction> má tři hodnoty: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>a <xref:System.Activities.PersistableIdleAction.Unload>.</span><span class="sxs-lookup"><span data-stu-id="6eda9-273">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="6eda9-274"><xref:System.Activities.PersistableIdleAction.Persist> způsobí, že pracovní postup zůstane zachován, ale nezpůsobí, že se pracovní postup uvolní.</span><span class="sxs-lookup"><span data-stu-id="6eda9-274"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="6eda9-275"><xref:System.Activities.PersistableIdleAction.Unload> způsobí, že se pracovní postup uchová a uvolní.</span><span class="sxs-lookup"><span data-stu-id="6eda9-275"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>

    <span data-ttu-id="6eda9-276">Následující příklad je dokončená `ConfigureWorkflowApplication` metoda.</span><span class="sxs-lookup"><span data-stu-id="6eda9-276">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>

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
                    UpdateStatus($"Congratulations, you guessed the number in {Turns} turns.")
                End If
                GameOver()
            End Sub

        wfApp.Aborted = _
            Sub(e As WorkflowApplicationAbortedEventArgs)
                UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}" & vbCrLf & $"{e.Reason.Message}")
            End Sub

        wfApp.OnUnhandledException = _
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)
                UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}" & vbCrLf & $"{e.UnhandledException.Message}")
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
                UpdateStatus($"Workflow Terminated. Exception: {e.TerminationException.GetType().FullName}\r\n{e.TerminationException.Message}");
            }
            else if (e.CompletionState == ActivityInstanceState.Canceled)
            {
                UpdateStatus("Workflow Canceled.");
            }
            else
            {
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);
                UpdateStatus($"Congratulations, you guessed the number in {Turns} turns.");
            }
            GameOver();
        };

        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)
        {
            UpdateStatus($"Workflow Aborted. Exception: {e.Reason.GetType().FullName}\r\n{e.Reason.Message}");
        };

        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)
        {
            UpdateStatus($"Unhandled Exception: {e.UnhandledException.GetType().FullName}\r\n{e.UnhandledException.Message}");
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

### <a name="BKMK_WorkflowVersionMap"></a><span data-ttu-id="6eda9-277">Povolení spouštění a obnovování více typů pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6eda9-277">To enable starting and resuming multiple workflow types</span></span>

<span data-ttu-id="6eda9-278">Aby bylo možné obnovit instanci pracovního postupu, musí hostitel zadat definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-278">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="6eda9-279">V tomto kurzu existují tři typy pracovních postupů a další kroky kurzu představují více verzí těchto typů.</span><span class="sxs-lookup"><span data-stu-id="6eda9-279">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="6eda9-280">`WorkflowIdentity` poskytuje, aby mohla hostitelská aplikace přidružit identifikační informace k trvalé instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-280">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="6eda9-281">Kroky v této části ukazují, jak vytvořit třídu nástrojů, která vám pomůže s mapováním identity pracovního postupu z trvalé instance pracovního postupu na odpovídající definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-281">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="6eda9-282">Další informace o `WorkflowIdentity` a verzích najdete v tématu [použití identita WorkflowIdentity a správy verzí](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="6eda9-282">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

1. <span data-ttu-id="6eda9-283">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat**, **Třída**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-283">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="6eda9-284">Do pole **název** zadejte `WorkflowVersionMap` a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-284">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>

2. <span data-ttu-id="6eda9-285">Do horní části souboru přidejte následující příkazy `using` nebo `Imports` s ostatními `using` nebo `Imports` příkazy.</span><span class="sxs-lookup"><span data-stu-id="6eda9-285">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Activities
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Activities;
    ```

3. <span data-ttu-id="6eda9-286">Nahraďte deklaraci třídy `WorkflowVersionMap` následující deklarací.</span><span class="sxs-lookup"><span data-stu-id="6eda9-286">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>

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

    <span data-ttu-id="6eda9-287">`WorkflowVersionMap` obsahuje tři identity pracovního postupu, které se mapují na tři definice pracovního postupu z tohoto kurzu a používají se v následujících oddílech při spuštění a obnovení pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="6eda9-287">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>

### <a name="BKMK_StartWorkflow"></a><span data-ttu-id="6eda9-288">Spuštění nového pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-288">To start a new workflow</span></span>

1. <span data-ttu-id="6eda9-289">Přidejte obslužnou rutinu `Click` pro `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-289">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="6eda9-290">Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na položku `NewGame`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-290">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="6eda9-291">Je přidána obslužná rutina `NewGame_Click` a zobrazení se přepne do zobrazení kódu pro formulář.</span><span class="sxs-lookup"><span data-stu-id="6eda9-291">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="6eda9-292">Vždy, když uživatel klikne na toto tlačítko, je spuštěn nový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="6eda9-292">Whenever the user clicks this button a new workflow is started.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="6eda9-293">Do obslužné rutiny Click přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="6eda9-293">Add the following code to the click handler.</span></span> <span data-ttu-id="6eda9-294">Tento kód vytvoří slovník vstupních argumentů pro pracovní postup, který je označen názvem argumentu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-294">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="6eda9-295">Tento slovník má jednu položku, která obsahuje rozsah náhodně generovaného čísla načteného z pole se seznamem rozsah.</span><span class="sxs-lookup"><span data-stu-id="6eda9-295">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. <span data-ttu-id="6eda9-296">Dále přidejte následující kód, který spustí pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="6eda9-296">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="6eda9-297">Definice `WorkflowIdentity` a pracovního postupu odpovídající typu vybraného pracovního postupu se načítají pomocí pomocné třídy `WorkflowVersionMap`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-297">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="6eda9-298">V dalším kroku se vytvoří nová instance `WorkflowApplication` pomocí definice pracovního postupu, `WorkflowIdentity`a slovníku vstupních argumentů.</span><span class="sxs-lookup"><span data-stu-id="6eda9-298">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>

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

4. <span data-ttu-id="6eda9-299">Dále přidejte následující kód, který přidá pracovní postup do seznamu pracovních postupů a zobrazí informace o verzi pracovního postupu ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="6eda9-299">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>

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

5. <span data-ttu-id="6eda9-300">Zavolejte `ConfigureWorkflowApplication` ke konfiguraci obslužných rutin pro úložiště instancí, rozšíření a životní cyklus pracovního cyklu pro tuto instanci `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-300">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>

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

6. <span data-ttu-id="6eda9-301">Nakonec zavolejte `Run`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-301">Finally, call `Run`.</span></span>

    ```vb
    'Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     <span data-ttu-id="6eda9-302">Následující příklad je dokončená obslužná rutina `NewGame_Click`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-302">The following example is the completed `NewGame_Click` handler.</span></span>

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

### <a name="BKMK_ResumeWorkflow"></a><span data-ttu-id="6eda9-303">Obnovení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-303">To resume a workflow</span></span>

1. <span data-ttu-id="6eda9-304">Přidejte obslužnou rutinu `Click` pro `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-304">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="6eda9-305">Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na položku `EnterGuess`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-305">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="6eda9-306">Vždy, když uživatel klikne na toto tlačítko, bude pracovní postup obnoven.</span><span class="sxs-lookup"><span data-stu-id="6eda9-306">Whenever the user clicks this button a workflow is resumed.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="6eda9-307">Přidejte následující kód, abyste se ujistili, že je v seznamu pracovního postupu vybraný pracovní postup a že je odhad uživatele platný.</span><span class="sxs-lookup"><span data-stu-id="6eda9-307">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>

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

3. <span data-ttu-id="6eda9-308">Dále načtěte `WorkflowApplicationInstance` trvalé instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-308">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="6eda9-309">`WorkflowApplicationInstance` představuje trvalou instanci pracovního postupu, která ještě nebyla přidružena k definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-309">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="6eda9-310">`DefinitionIdentity` `WorkflowApplicationInstance` obsahuje `WorkflowIdentity` trvalé instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-310">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="6eda9-311">V tomto kurzu se třída `WorkflowVersionMap` Utility používá k mapování `WorkflowIdentity` na správnou definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-311">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="6eda9-312">Po načtení definice pracovního postupu se vytvoří `WorkflowApplication` pomocí správné definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-312">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>

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

4. <span data-ttu-id="6eda9-313">Po vytvoření `WorkflowApplication` nakonfigurujte úložiště instancí, obslužné rutiny životního cyklu pracovního postupu a rozšíření tím, že zavoláte `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-313">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="6eda9-314">Tyto kroky je nutné provést při každém vytvoření nového `WorkflowApplication` a je třeba je provést před načtením instance pracovního postupu do `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-314">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="6eda9-315">Po načtení je pracovní postup obnovený s odhadem uživatele.</span><span class="sxs-lookup"><span data-stu-id="6eda9-315">After the workflow is loaded, it is resumed with the user's guess.</span></span>

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

5. <span data-ttu-id="6eda9-316">Nakonec zrušte zaškrtnutí políčka odhad a připravte formulář, abyste mohli akceptovat další odhad.</span><span class="sxs-lookup"><span data-stu-id="6eda9-316">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>

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

    <span data-ttu-id="6eda9-317">Následující příklad je dokončená obslužná rutina `EnterGuess_Click`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-317">The following example is the completed `EnterGuess_Click` handler.</span></span>

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

### <a name="BKMK_TerminateWorkflow"></a><span data-ttu-id="6eda9-318">Ukončení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6eda9-318">To terminate a workflow</span></span>

1. <span data-ttu-id="6eda9-319">Přidejte obslužnou rutinu `Click` pro `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-319">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="6eda9-320">Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na položku `QuitGame`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-320">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="6eda9-321">Vždy, když uživatel klikne na toto tlačítko, je ukončen aktuálně vybraný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="6eda9-321">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="6eda9-322">Do obslužné rutiny `QuitGame_Click` přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="6eda9-322">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="6eda9-323">Tento kód nejprve kontroluje, zda je v seznamu pracovních postupů vybrán pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="6eda9-323">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="6eda9-324">Poté načte trvalou instanci do `WorkflowApplicationInstance`, používá `DefinitionIdentity` k určení správné definice pracovního postupu a poté inicializuje `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-324">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="6eda9-325">V dalších rozšířeních a obslužných rutinách životního cyklu pracovního postupu se nakonfigurují volání `ConfigureWorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="6eda9-325">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="6eda9-326">Po nakonfigurování `WorkflowApplication` je načtena a poté `Terminate` volána.</span><span class="sxs-lookup"><span data-stu-id="6eda9-326">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>

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

### <a name="BKMK_BuildAndRun"></a><span data-ttu-id="6eda9-327">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="6eda9-327">To build and run the application</span></span>

1. <span data-ttu-id="6eda9-328">Dvakrát klikněte na **program.cs** (nebo **Module1. vb**) v **Průzkumník řešení** pro zobrazení kódu.</span><span class="sxs-lookup"><span data-stu-id="6eda9-328">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>

2. <span data-ttu-id="6eda9-329">Do horní části souboru přidejte následující příkaz `using` (nebo `Imports`) s jinými příkazy `using` (nebo `Imports`).</span><span class="sxs-lookup"><span data-stu-id="6eda9-329">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="6eda9-330">Odeberte nebo Odkomentujte existující kód hostování pracovního postupu z tématu [Postupy: spuštění pracovního postupu](how-to-run-a-workflow.md)a jeho nahrazení následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="6eda9-330">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](how-to-run-a-workflow.md), and replace it with the following code.</span></span>

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

4. <span data-ttu-id="6eda9-331">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-331">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="6eda9-332">Na kartě **aplikace** zadejte pro **Typ výstupu** **aplikace systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="6eda9-332">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="6eda9-333">Tento krok je nepovinný, ale pokud se nedodržuje, zobrazí se kromě formuláře okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="6eda9-333">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>

5. <span data-ttu-id="6eda9-334">Stisknutím kombinace kláves CTRL + SHIFT + B sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6eda9-334">Press Ctrl+Shift+B to build the application.</span></span>

6. <span data-ttu-id="6eda9-335">Zajistěte, aby byla aplikace **NumberGuessWorkflowHost** nastavená jako spouštěcí aplikace, a stisknutím kláves CTRL + F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6eda9-335">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>

7. <span data-ttu-id="6eda9-336">Vyberte rozsah pro odhad hry a typ pracovního postupu, který chcete spustit, a klikněte na **Nová hra**.</span><span class="sxs-lookup"><span data-stu-id="6eda9-336">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="6eda9-337">V poli **odhad** zadejte odhad a kliknutím na tlačítko **Přejít** odešlete svůj odhad.</span><span class="sxs-lookup"><span data-stu-id="6eda9-337">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="6eda9-338">Všimněte si, že výstup aktivit `WriteLine` se zobrazí ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="6eda9-338">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>

8. <span data-ttu-id="6eda9-339">Spusťte několik pracovních postupů pomocí různých typů pracovních postupů a rozsahů čísel, zadejte několik odhadů a přepněte mezi pracovními postupy výběrem ze seznamu **ID instance pracovního postupu** .</span><span class="sxs-lookup"><span data-stu-id="6eda9-339">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>

    <span data-ttu-id="6eda9-340">Všimněte si, že když přepnete na nový pracovní postup, předchozí odhad a průběh pracovního postupu se v okně stav nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="6eda9-340">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="6eda9-341">Důvod, proč stav není k dispozici, je, že není zachycen a ukládán nikde.</span><span class="sxs-lookup"><span data-stu-id="6eda9-341">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="6eda9-342">V dalším kroku tohoto kurzu se [naučíte: vytvořit vlastního účastníka sledování](how-to-create-a-custom-tracking-participant.md)a vytvořit vlastního účastníka sledování, který tyto informace uloží.</span><span class="sxs-lookup"><span data-stu-id="6eda9-342">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
