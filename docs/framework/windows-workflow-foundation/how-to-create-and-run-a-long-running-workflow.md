---
title: 'Postupy: Vytvoření a spuštění dlouhotrvajícího pracovního postupu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 15ee10120f4d4c92bdc95cb48cb3cb838f526343
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044380"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a><span data-ttu-id="1ceee-102">Postupy: Vytvoření a spuštění dlouhotrvajícího pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-102">How to: Create and Run a Long Running Workflow</span></span>

<span data-ttu-id="1ceee-103">Jednou z ústředních funkcí programovací model Windows Workflow Foundation (WF) je schopnost modulu runtime uchovávat a uvolňovat nečinné pracovní postupy do databáze.</span><span class="sxs-lookup"><span data-stu-id="1ceee-103">One of the central features of Windows Workflow Foundation (WF) is the runtime’s ability to persist and unload idle workflows to a database.</span></span> <span data-ttu-id="1ceee-104">Postup [: Spuštění pracovního postupu](how-to-run-a-workflow.md) ukázal základy hostování pracovního postupu pomocí konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ceee-104">The steps in [How to: Run a Workflow](how-to-run-a-workflow.md) demonstrated the basics of workflow hosting using a console application.</span></span> <span data-ttu-id="1ceee-105">V příkladech se zobrazily počáteční pracovní postupy, obslužné rutiny životního cyklu pracovního postupu a obnovení záložek.</span><span class="sxs-lookup"><span data-stu-id="1ceee-105">Examples were shown of starting workflows, workflow lifecycle handlers, and resuming bookmarks.</span></span> <span data-ttu-id="1ceee-106">Aby bylo možné předvést trvalost pracovního postupu efektivně, je zapotřebí složitější hostitel pracovního postupu, který podporuje spouštění a obnovování více instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-106">In order to demonstrate workflow persistence effectively, a more complex workflow host is required that supports starting and resuming multiple workflow instances.</span></span> <span data-ttu-id="1ceee-107">Tento krok v tomto kurzu ukazuje, jak vytvořit hostitelskou aplikaci Windows Form, která podporuje spouštění a obnovování více instancí pracovního postupu, trvalý pracovní postup a poskytuje základ pro pokročilé funkce, jako je například sledování a správa verzí, které jsou znázorněné v dalších krocích kurzu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-107">This step in the tutorial demonstrates how to create a Windows form host application that supports starting and resuming multiple workflow instances, workflow persistence, and provides a basis for the advanced features such as tracking and versioning that are demonstrated in subsequent tutorial steps.</span></span>

> [!NOTE]
> <span data-ttu-id="1ceee-108">Tento krok kurzu a následné kroky používají všechny tři typy pracovních postupů v [následujících krocích: Vytvořte pracovní postup](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="1ceee-108">This tutorial step and the subsequent steps use all three workflow types from [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span> <span data-ttu-id="1ceee-109">Pokud jste nedokončili všechny tři typy, můžete si stáhnout dokončenou verzi kroků z [programovací model Windows Workflow Foundation (WF45) – začínáme kurzu](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="1ceee-109">If you did not complete all three types you can download a completed version of the steps from [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

> [!NOTE]
> <span data-ttu-id="1ceee-110">Pokud si chcete stáhnout dokončenou verzi nebo zobrazit návod k videu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="1ceee-110">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="1ceee-111">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="1ceee-111">In this topic</span></span>

- [<span data-ttu-id="1ceee-112">Vytvoření databáze trvalosti</span><span class="sxs-lookup"><span data-stu-id="1ceee-112">To create the persistence database</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)

- [<span data-ttu-id="1ceee-113">Přidání odkazu na DurableInstancing sestavení</span><span class="sxs-lookup"><span data-stu-id="1ceee-113">To add the reference to the DurableInstancing assemblies</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)

- [<span data-ttu-id="1ceee-114">Vytvoření formuláře hostitele pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-114">To create the workflow host form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)

- [<span data-ttu-id="1ceee-115">Přidání vlastností a pomocných metod formuláře</span><span class="sxs-lookup"><span data-stu-id="1ceee-115">To add the properties and helper methods of the form</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)

- [<span data-ttu-id="1ceee-116">Konfigurace úložiště instancí, obslužných rutin životního cyklu pracovního postupu a rozšíření</span><span class="sxs-lookup"><span data-stu-id="1ceee-116">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)

- [<span data-ttu-id="1ceee-117">Povolení spouštění a obnovování více typů pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1ceee-117">To enable starting and resuming multiple workflow types</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)

- [<span data-ttu-id="1ceee-118">Spuštění nového pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-118">To start a new workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)

- [<span data-ttu-id="1ceee-119">Obnovení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-119">To resume a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)

- [<span data-ttu-id="1ceee-120">Ukončení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-120">To terminate a workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)

- [<span data-ttu-id="1ceee-121">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="1ceee-121">To build and run the application</span></span>](how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)

### <a name="BKMK_CreatePersistenceDatabase"></a><span data-ttu-id="1ceee-122">Vytvoření databáze trvalosti</span><span class="sxs-lookup"><span data-stu-id="1ceee-122">To create the persistence database</span></span>

1. <span data-ttu-id="1ceee-123">Otevřete SQL Server Management Studio a připojte se k místnímu serveru, například **.\SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-123">Open SQL Server Management Studio and connect to the local server, for example **.\SQLEXPRESS**.</span></span> <span data-ttu-id="1ceee-124">Pravým tlačítkem myši klikněte na uzel **databáze** na místním serveru a vyberte možnost **Nová databáze**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-124">Right-click the **Databases** node on the local server, and select **New Database**.</span></span> <span data-ttu-id="1ceee-125">Pojmenujte novou databázi **WF45GettingStartedTutorial**, přijměte všechny ostatní hodnoty a vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-125">Name the new database **WF45GettingStartedTutorial**, accept all other values, and select **OK**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1ceee-126">Před vytvořením databáze se ujistěte, že máte na místním serveru oprávnění **vytvořit databázi** .</span><span class="sxs-lookup"><span data-stu-id="1ceee-126">Ensure that you have **Create Database** permission on the local server before creating the database.</span></span>

2. <span data-ttu-id="1ceee-127">V nabídce **soubor** vyberte **otevřít**, **soubor** .</span><span class="sxs-lookup"><span data-stu-id="1ceee-127">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="1ceee-128">Přejděte do následující složky:`C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="1ceee-128">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>

    <span data-ttu-id="1ceee-129">Vyberte následující dva soubory a klikněte na **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-129">Select the following two files and click **Open**.</span></span>

    - <span data-ttu-id="1ceee-130">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="1ceee-130">SqlWorkflowInstanceStoreLogic.sql</span></span>

    - <span data-ttu-id="1ceee-131">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="1ceee-131">SqlWorkflowInstanceStoreSchema.sql</span></span>

3. <span data-ttu-id="1ceee-132">V nabídce **okno** vyberte **SqlWorkflowInstanceStoreSchema. SQL** .</span><span class="sxs-lookup"><span data-stu-id="1ceee-132">Choose **SqlWorkflowInstanceStoreSchema.sql** from the **Window** menu.</span></span> <span data-ttu-id="1ceee-133">V rozevíracím seznamu **dostupné databáze** zkontrolujte, že je vybraná možnost **WF45GettingStartedTutorial** a v nabídce **dotaz** vyberte **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="1ceee-133">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

4. <span data-ttu-id="1ceee-134">V nabídce **okno** vyberte **SqlWorkflowInstanceStoreLogic. SQL** .</span><span class="sxs-lookup"><span data-stu-id="1ceee-134">Choose **SqlWorkflowInstanceStoreLogic.sql** from the **Window** menu.</span></span> <span data-ttu-id="1ceee-135">V rozevíracím seznamu **dostupné databáze** zkontrolujte, že je vybraná možnost **WF45GettingStartedTutorial** a v nabídce **dotaz** vyberte **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="1ceee-135">Ensure that **WF45GettingStartedTutorial** is selected in the **Available Databases** drop-down and choose **Execute** from the **Query** menu.</span></span>

    > [!WARNING]
    > <span data-ttu-id="1ceee-136">Je důležité provést předchozí dva kroky ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1ceee-136">It is important to perform the previous two steps in the correct order.</span></span> <span data-ttu-id="1ceee-137">Pokud jsou dotazy spouštěny mimo pořadí, dojde k chybám a databáze trvalosti není správně nakonfigurována.</span><span class="sxs-lookup"><span data-stu-id="1ceee-137">If the queries are executed out of order, errors occur and the persistence database is not configured correctly.</span></span>

### <a name="BKMK_AddReference"></a><span data-ttu-id="1ceee-138">Přidání odkazu na DurableInstancing sestavení</span><span class="sxs-lookup"><span data-stu-id="1ceee-138">To add the reference to the DurableInstancing assemblies</span></span>

1. <span data-ttu-id="1ceee-139">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-139">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Add Reference**.</span></span>

2. <span data-ttu-id="1ceee-140">Vyberte **sestavení** ze seznamu **Přidat odkaz** a zadejte `DurableInstancing` do pole **vyhledávací sestavení** .</span><span class="sxs-lookup"><span data-stu-id="1ceee-140">Select **Assemblies** from the **Add Reference** list, and type `DurableInstancing` into the **Search Assemblies** box.</span></span> <span data-ttu-id="1ceee-141">To filtruje sestavení a usnadňuje výběr požadovaných odkazů.</span><span class="sxs-lookup"><span data-stu-id="1ceee-141">This filters the assemblies and makes the desired references easier to select.</span></span>

3. <span data-ttu-id="1ceee-142">Zaškrtněte políčko vedle položky **System. Activities. DurableInstancing** a **System. Runtime. DurableInstancing** ze seznamu **výsledků hledání** a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-142">Check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list, and click **OK**.</span></span>

### <a name="BKMK_CreateForm"></a><span data-ttu-id="1ceee-143">Vytvoření formuláře hostitele pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-143">To create the workflow host form</span></span>

> [!NOTE]
> <span data-ttu-id="1ceee-144">Kroky v tomto postupu popisují, jak formulář Přidat a nakonfigurovat ručně.</span><span class="sxs-lookup"><span data-stu-id="1ceee-144">The steps in this procedure describe how to add and configure the form manually.</span></span> <span data-ttu-id="1ceee-145">V případě potřeby si můžete stáhnout soubory řešení pro kurz a přidat dokončený formulář do projektu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-145">If desired, you can download the solution files for the tutorial and add the completed form to the project.</span></span> <span data-ttu-id="1ceee-146">Pokud si chcete stáhnout soubory kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45)-začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="1ceee-146">To download the tutorial files, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span> <span data-ttu-id="1ceee-147">Po stažení souborů klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-147">Once the files are downloaded, right-click **NumberGuessWorkflowHost** and choose **Add Reference**.</span></span> <span data-ttu-id="1ceee-148">Přidejte odkaz na **System. Windows. Forms** a **System. Drawing**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-148">Add a reference to **System.Windows.Forms** and **System.Drawing**.</span></span> <span data-ttu-id="1ceee-149">Tyto odkazy jsou přidány automaticky, pokud přidáte nový formulář z nabídky **Přidat**, **Nová položka** , ale je nutné jej přidat ručně při importu formuláře.</span><span class="sxs-lookup"><span data-stu-id="1ceee-149">These references are added automatically if you add a new form from the **Add**, **New Item** menu, but must be added manually when importing a form.</span></span> <span data-ttu-id="1ceee-150">Až budou odkazy přidány, klikněte pravým tlačítkem myši na **NumberGuessWorkflowHost** v **Průzkumník řešení** a vyberte **Přidat**, **existující položka**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-150">Once the references are added, right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Existing Item**.</span></span> <span data-ttu-id="1ceee-151">Přejděte `Form` do složky v souborech projektu, vyberte **WorkflowHostForm.cs** (nebo **WorkflowHostForm. vb**) a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-151">Browse to the `Form` folder in the project files, select **WorkflowHostForm.cs** (or **WorkflowHostForm.vb**), and click **Add**.</span></span> <span data-ttu-id="1ceee-152">Pokud se rozhodnete importovat formulář, můžete přeskočit dolů k další části a [Přidat vlastnosti a pomocné metody formuláře](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span><span class="sxs-lookup"><span data-stu-id="1ceee-152">If you choose to import the form, then you can skip down to the next section, [To add the properties and helper methods of the form](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).</span></span>

1. <span data-ttu-id="1ceee-153">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat**, **Nová položka**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-153">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **New Item**.</span></span>

2. <span data-ttu-id="1ceee-154">V seznamu **nainstalované** šablony vyberte možnost **formulář Windows**, do pole `WorkflowHostForm` **název** zadejte a klikněte na tlačítko **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-154">In the **Installed** templates list, choose **Windows Form**, type `WorkflowHostForm` in the **Name** box, and click **Add**.</span></span>

3. <span data-ttu-id="1ceee-155">Ve formuláři nakonfigurujte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1ceee-155">Configure the following properties on the form.</span></span>

    |<span data-ttu-id="1ceee-156">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="1ceee-156">Property</span></span>|<span data-ttu-id="1ceee-157">Value</span><span class="sxs-lookup"><span data-stu-id="1ceee-157">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="1ceee-158">FormBorderStyle</span><span class="sxs-lookup"><span data-stu-id="1ceee-158">FormBorderStyle</span></span>|<span data-ttu-id="1ceee-159">FixedSingle</span><span class="sxs-lookup"><span data-stu-id="1ceee-159">FixedSingle</span></span>|
    |<span data-ttu-id="1ceee-160">MaximizeBox</span><span class="sxs-lookup"><span data-stu-id="1ceee-160">MaximizeBox</span></span>|<span data-ttu-id="1ceee-161">False</span><span class="sxs-lookup"><span data-stu-id="1ceee-161">False</span></span>|
    |<span data-ttu-id="1ceee-162">Velikost</span><span class="sxs-lookup"><span data-stu-id="1ceee-162">Size</span></span>|<span data-ttu-id="1ceee-163">400, 420</span><span class="sxs-lookup"><span data-stu-id="1ceee-163">400, 420</span></span>|

4. <span data-ttu-id="1ceee-164">Do formuláře přidejte následující ovládací prvky v zadaném pořadí a nakonfigurujte vlastnosti jako směrované.</span><span class="sxs-lookup"><span data-stu-id="1ceee-164">Add the following controls to the form in the order specified and configure the properties as directed.</span></span>

    |<span data-ttu-id="1ceee-165">Control</span><span class="sxs-lookup"><span data-stu-id="1ceee-165">Control</span></span>|<span data-ttu-id="1ceee-166">Majetek Value</span><span class="sxs-lookup"><span data-stu-id="1ceee-166">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="1ceee-167">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="1ceee-167">**Button**</span></span>|<span data-ttu-id="1ceee-168">Jméno: NewGame</span><span class="sxs-lookup"><span data-stu-id="1ceee-168">Name: NewGame</span></span><br /><br /> <span data-ttu-id="1ceee-169">Oblasti 13, 13</span><span class="sxs-lookup"><span data-stu-id="1ceee-169">Location: 13, 13</span></span><br /><br /> <span data-ttu-id="1ceee-170">Hodnota 75, 23</span><span class="sxs-lookup"><span data-stu-id="1ceee-170">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="1ceee-171">Text: Nová hra</span><span class="sxs-lookup"><span data-stu-id="1ceee-171">Text: New Game</span></span>|
    |<span data-ttu-id="1ceee-172">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="1ceee-172">**Label**</span></span>|<span data-ttu-id="1ceee-173">Oblasti 94, 18</span><span class="sxs-lookup"><span data-stu-id="1ceee-173">Location: 94, 18</span></span><br /><br /> <span data-ttu-id="1ceee-174">Text: Odhadnout číslo od 1 do</span><span class="sxs-lookup"><span data-stu-id="1ceee-174">Text: Guess a number from 1 to</span></span>|
    |<span data-ttu-id="1ceee-175">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="1ceee-175">**ComboBox**</span></span>|<span data-ttu-id="1ceee-176">Jméno: NumberRange</span><span class="sxs-lookup"><span data-stu-id="1ceee-176">Name: NumberRange</span></span><br /><br /> <span data-ttu-id="1ceee-177">DropDownStyle: Rozevírací</span><span class="sxs-lookup"><span data-stu-id="1ceee-177">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="1ceee-178">Položek 10, 100, 1000</span><span class="sxs-lookup"><span data-stu-id="1ceee-178">Items: 10, 100, 1000</span></span><br /><br /> <span data-ttu-id="1ceee-179">Oblasti 228, 12</span><span class="sxs-lookup"><span data-stu-id="1ceee-179">Location: 228, 12</span></span><br /><br /> <span data-ttu-id="1ceee-180">Hodnota 143, 21</span><span class="sxs-lookup"><span data-stu-id="1ceee-180">Size: 143, 21</span></span>|
    |<span data-ttu-id="1ceee-181">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="1ceee-181">**Label**</span></span>|<span data-ttu-id="1ceee-182">Oblasti 13, 43</span><span class="sxs-lookup"><span data-stu-id="1ceee-182">Location: 13, 43</span></span><br /><br /> <span data-ttu-id="1ceee-183">Text: Typ pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-183">Text: Workflow type</span></span>|
    |<span data-ttu-id="1ceee-184">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="1ceee-184">**ComboBox**</span></span>|<span data-ttu-id="1ceee-185">Jméno: WorkflowType</span><span class="sxs-lookup"><span data-stu-id="1ceee-185">Name: WorkflowType</span></span><br /><br /> <span data-ttu-id="1ceee-186">DropDownStyle: Rozevírací</span><span class="sxs-lookup"><span data-stu-id="1ceee-186">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="1ceee-187">Položek StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="1ceee-187">Items: StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow</span></span><br /><br /> <span data-ttu-id="1ceee-188">Oblasti 94, 40</span><span class="sxs-lookup"><span data-stu-id="1ceee-188">Location: 94, 40</span></span><br /><br /> <span data-ttu-id="1ceee-189">Hodnota 277, 21</span><span class="sxs-lookup"><span data-stu-id="1ceee-189">Size: 277, 21</span></span>|
    |<span data-ttu-id="1ceee-190">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="1ceee-190">**Label**</span></span>|<span data-ttu-id="1ceee-191">Jméno: WorkflowVersion</span><span class="sxs-lookup"><span data-stu-id="1ceee-191">Name: WorkflowVersion</span></span><br /><br /> <span data-ttu-id="1ceee-192">Oblasti 13, 362</span><span class="sxs-lookup"><span data-stu-id="1ceee-192">Location: 13, 362</span></span><br /><br /> <span data-ttu-id="1ceee-193">Text: Verze pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-193">Text: Workflow version</span></span>|
    |<span data-ttu-id="1ceee-194">**GroupBox**</span><span class="sxs-lookup"><span data-stu-id="1ceee-194">**GroupBox**</span></span>|<span data-ttu-id="1ceee-195">Oblasti 13, 67</span><span class="sxs-lookup"><span data-stu-id="1ceee-195">Location: 13, 67</span></span><br /><br /> <span data-ttu-id="1ceee-196">Hodnota 358, 287</span><span class="sxs-lookup"><span data-stu-id="1ceee-196">Size: 358, 287</span></span><br /><br /> <span data-ttu-id="1ceee-197">Text: Lovu</span><span class="sxs-lookup"><span data-stu-id="1ceee-197">Text: Game</span></span>|

    > [!NOTE]
    > <span data-ttu-id="1ceee-198">Při přidávání následujících ovládacích prvků Umístěte tyto ovládací prvky do skupinového rámečku.</span><span class="sxs-lookup"><span data-stu-id="1ceee-198">When adding the following controls, put them into the GroupBox.</span></span>

    |<span data-ttu-id="1ceee-199">Control</span><span class="sxs-lookup"><span data-stu-id="1ceee-199">Control</span></span>|<span data-ttu-id="1ceee-200">Majetek Value</span><span class="sxs-lookup"><span data-stu-id="1ceee-200">Property: Value</span></span>|
    |-------------|---------------------|
    |<span data-ttu-id="1ceee-201">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="1ceee-201">**Label**</span></span>|<span data-ttu-id="1ceee-202">Oblasti 7, 20</span><span class="sxs-lookup"><span data-stu-id="1ceee-202">Location: 7, 20</span></span><br /><br /> <span data-ttu-id="1ceee-203">Text: ID instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-203">Text: Workflow Instance Id</span></span>|
    |<span data-ttu-id="1ceee-204">**ComboBox**</span><span class="sxs-lookup"><span data-stu-id="1ceee-204">**ComboBox**</span></span>|<span data-ttu-id="1ceee-205">Jméno: InstanceId</span><span class="sxs-lookup"><span data-stu-id="1ceee-205">Name: InstanceId</span></span><br /><br /> <span data-ttu-id="1ceee-206">DropDownStyle: Rozevírací</span><span class="sxs-lookup"><span data-stu-id="1ceee-206">DropDownStyle: DropDownList</span></span><br /><br /> <span data-ttu-id="1ceee-207">Oblasti 121, 17</span><span class="sxs-lookup"><span data-stu-id="1ceee-207">Location: 121, 17</span></span><br /><br /> <span data-ttu-id="1ceee-208">Hodnota 227, 21</span><span class="sxs-lookup"><span data-stu-id="1ceee-208">Size: 227, 21</span></span>|
    |<span data-ttu-id="1ceee-209">**Popisek**</span><span class="sxs-lookup"><span data-stu-id="1ceee-209">**Label**</span></span>|<span data-ttu-id="1ceee-210">Oblasti 7, 47</span><span class="sxs-lookup"><span data-stu-id="1ceee-210">Location: 7, 47</span></span><br /><br /> <span data-ttu-id="1ceee-211">Text: Odhalit</span><span class="sxs-lookup"><span data-stu-id="1ceee-211">Text: Guess</span></span>|
    |<span data-ttu-id="1ceee-212">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="1ceee-212">**TextBox**</span></span>|<span data-ttu-id="1ceee-213">Jméno: Odhalit</span><span class="sxs-lookup"><span data-stu-id="1ceee-213">Name: Guess</span></span><br /><br /> <span data-ttu-id="1ceee-214">Oblasti 50, 44</span><span class="sxs-lookup"><span data-stu-id="1ceee-214">Location: 50, 44</span></span><br /><br /> <span data-ttu-id="1ceee-215">Hodnota 65, 20</span><span class="sxs-lookup"><span data-stu-id="1ceee-215">Size: 65, 20</span></span>|
    |<span data-ttu-id="1ceee-216">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="1ceee-216">**Button**</span></span>|<span data-ttu-id="1ceee-217">Jméno: EnterGuess</span><span class="sxs-lookup"><span data-stu-id="1ceee-217">Name: EnterGuess</span></span><br /><br /> <span data-ttu-id="1ceee-218">Oblasti 121, 42</span><span class="sxs-lookup"><span data-stu-id="1ceee-218">Location: 121, 42</span></span><br /><br /> <span data-ttu-id="1ceee-219">Hodnota 75, 23</span><span class="sxs-lookup"><span data-stu-id="1ceee-219">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="1ceee-220">Text: Zadejte odhad</span><span class="sxs-lookup"><span data-stu-id="1ceee-220">Text: Enter Guess</span></span>|
    |<span data-ttu-id="1ceee-221">**Tlačítko**</span><span class="sxs-lookup"><span data-stu-id="1ceee-221">**Button**</span></span>|<span data-ttu-id="1ceee-222">Jméno: QuitGame</span><span class="sxs-lookup"><span data-stu-id="1ceee-222">Name: QuitGame</span></span><br /><br /> <span data-ttu-id="1ceee-223">Oblasti 274, 42</span><span class="sxs-lookup"><span data-stu-id="1ceee-223">Location: 274, 42</span></span><br /><br /> <span data-ttu-id="1ceee-224">Hodnota 75, 23</span><span class="sxs-lookup"><span data-stu-id="1ceee-224">Size: 75, 23</span></span><br /><br /> <span data-ttu-id="1ceee-225">Text: Ukončit</span><span class="sxs-lookup"><span data-stu-id="1ceee-225">Text: Quit</span></span>|
    |<span data-ttu-id="1ceee-226">**TextBox**</span><span class="sxs-lookup"><span data-stu-id="1ceee-226">**TextBox**</span></span>|<span data-ttu-id="1ceee-227">Jméno: WorkflowStatus</span><span class="sxs-lookup"><span data-stu-id="1ceee-227">Name: WorkflowStatus</span></span><br /><br /> <span data-ttu-id="1ceee-228">Oblasti 10, 73</span><span class="sxs-lookup"><span data-stu-id="1ceee-228">Location: 10, 73</span></span><br /><br /> <span data-ttu-id="1ceee-229">Víceřádkový Pravda</span><span class="sxs-lookup"><span data-stu-id="1ceee-229">Multiline: True</span></span><br /><br /> <span data-ttu-id="1ceee-230">ReadOnly Pravda</span><span class="sxs-lookup"><span data-stu-id="1ceee-230">ReadOnly: True</span></span><br /><br /> <span data-ttu-id="1ceee-231">Posuvníky Svislé</span><span class="sxs-lookup"><span data-stu-id="1ceee-231">ScrollBars: Vertical</span></span><br /><br /> <span data-ttu-id="1ceee-232">Hodnota 338, 208</span><span class="sxs-lookup"><span data-stu-id="1ceee-232">Size: 338, 208</span></span>|

5. <span data-ttu-id="1ceee-233">Nastavte vlastnost **AcceptButton** formuláře na **EnterGuess**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-233">Set the **AcceptButton** property of the form to **EnterGuess**.</span></span>

 <span data-ttu-id="1ceee-234">Následující příklad znázorňuje dokončený formulář.</span><span class="sxs-lookup"><span data-stu-id="1ceee-234">The following example illustrates the completed form.</span></span>

 ![Snímek obrazovky programovací model Windows Workflow Foundation formuláře hostitele pracovního postupu.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)

### <a name="BKMK_AddHelperMethods"></a><span data-ttu-id="1ceee-236">Přidání vlastností a pomocných metod formuláře</span><span class="sxs-lookup"><span data-stu-id="1ceee-236">To add the properties and helper methods of the form</span></span>

<span data-ttu-id="1ceee-237">Kroky v této části přidávají vlastnosti a pomocné metody do třídy formuláře, která konfiguruje uživatelské rozhraní formuláře tak, aby podporovalo spouštění a obnovování počtu vyčíslení pro odhadované pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="1ceee-237">The steps in this section add properties and helper methods to the form class that configure the UI of the form to support running and resuming number guess workflows.</span></span>

1. <span data-ttu-id="1ceee-238">V **Průzkumník řešení** klikněte pravým tlačítkem na **WorkflowHostForm** a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-238">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>

2. <span data-ttu-id="1ceee-239">Do horní části `using` souboru přidejte `Imports`následující příkazy (nebo), které budou `using` příkazy (nebo `Imports`).</span><span class="sxs-lookup"><span data-stu-id="1ceee-239">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

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

3. <span data-ttu-id="1ceee-240">Do třídy **WorkflowHostForm** přidejte následující deklarace členů.</span><span class="sxs-lookup"><span data-stu-id="1ceee-240">Add the following member declarations to the **WorkflowHostForm** class.</span></span>

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
    > <span data-ttu-id="1ceee-241">Pokud je váš připojovací řetězec jiný, aktualizujte `connectionString` , aby odkazoval na vaši databázi.</span><span class="sxs-lookup"><span data-stu-id="1ceee-241">If your connection string is different, update `connectionString` to refer to your database.</span></span>

4. <span data-ttu-id="1ceee-242">`WorkflowInstanceId` Přidejte vlastnost`WorkflowFormHost` do třídy.</span><span class="sxs-lookup"><span data-stu-id="1ceee-242">Add a `WorkflowInstanceId` property to the `WorkflowFormHost` class.</span></span>

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

    <span data-ttu-id="1ceee-243">V `InstanceId` poli se seznamem se zobrazí seznam trvalých ID instancí pracovního postupu `WorkflowInstanceId` a vlastnost vrátí aktuálně vybraný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="1ceee-243">The `InstanceId` combo box displays a list of persisted workflow instance ids, and the `WorkflowInstanceId` property returns the currently selected workflow.</span></span>

5. <span data-ttu-id="1ceee-244">Přidejte obslužnou rutinu pro událost `Load` formuláře.</span><span class="sxs-lookup"><span data-stu-id="1ceee-244">Add a handler for the form `Load` event.</span></span> <span data-ttu-id="1ceee-245">Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře, klikněte na ikonu **události** v horní části okna **vlastnosti** a dvakrát klikněte na položku **načíst**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-245">To add the handler, switch to **Design View** for the form, click the **Events** icon at the top of the **Properties** window, and double-click **Load**.</span></span>

    ```vb
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load

    End Sub
    ```

    ```csharp
    private void WorkflowHostForm_Load(object sender, EventArgs e)
    {

    }
    ```

6. <span data-ttu-id="1ceee-246">Přidejte následující kód do `WorkflowHostForm_Load`.</span><span class="sxs-lookup"><span data-stu-id="1ceee-246">Add the following code to `WorkflowHostForm_Load`.</span></span>

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

    <span data-ttu-id="1ceee-247">Když je formulář načtený `SqlWorkflowInstanceStore` , je nakonfigurovaný rozsah a typ pracovního postupu pole se seznamem na výchozí hodnoty a trvalé instance pracovního postupu se přidají `InstanceId` do pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="1ceee-247">When the form loads, the `SqlWorkflowInstanceStore` is configured, the range and workflow type combo boxes are set to default values, and the persisted workflow instances are added to the `InstanceId` combo box.</span></span>

7. <span data-ttu-id="1ceee-248">Přidejte obslužnou rutinu `InstanceId`pro. `SelectedIndexChanged`</span><span class="sxs-lookup"><span data-stu-id="1ceee-248">Add a `SelectedIndexChanged` handler for `InstanceId`.</span></span> <span data-ttu-id="1ceee-249">Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře, vyberte `InstanceId` pole se seznamem, klikněte na ikonu **události** v horní části okna **vlastnosti** a dvakrát klikněte na položku **SelectedIndexChanged**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-249">To add the handler, switch to **Design View** for the form, select the `InstanceId` combo box, click the **Events** icon at the top of the **Properties** window, and double-click **SelectedIndexChanged**.</span></span>

    ```vb
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged

    End Sub
    ```

    ```csharp
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)
    {

    }
    ```

8. <span data-ttu-id="1ceee-250">Přidejte následující kód do `InstanceId_SelectedIndexChanged`.</span><span class="sxs-lookup"><span data-stu-id="1ceee-250">Add the following code to `InstanceId_SelectedIndexChanged`.</span></span> <span data-ttu-id="1ceee-251">Vždy, když uživatel vybere pracovní postup pomocí pole se seznamem, tato obslužná rutina aktualizuje stavové okno.</span><span class="sxs-lookup"><span data-stu-id="1ceee-251">Whenever the user selects a workflow by using the combo box this handler updates the status window.</span></span>

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

9. <span data-ttu-id="1ceee-252">Do třídy Form `ListPersistedWorkflows` přidejte následující metodu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-252">Add the following `ListPersistedWorkflows` method to the form class.</span></span>

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

    <span data-ttu-id="1ceee-253">`ListPersistedWorkflows`vyhledá v úložišti instancí trvalé instance pracovního postupu a přidá ID instancí do `cboInstanceId` pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="1ceee-253">`ListPersistedWorkflows` queries the instance store for persisted workflow instances, and adds the instance ids to the `cboInstanceId` combo box.</span></span>

10. <span data-ttu-id="1ceee-254">Do třídy Form `UpdateStatus` přidejte následující metodu a odpovídající delegát.</span><span class="sxs-lookup"><span data-stu-id="1ceee-254">Add the following `UpdateStatus` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="1ceee-255">Tato metoda aktualizuje stavové okno ve formuláři se stavem aktuálně spuštěného pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-255">This method updates the status window on the form with the status of the currently running workflow.</span></span>

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

11. <span data-ttu-id="1ceee-256">Do třídy Form `GameOver` přidejte následující metodu a odpovídající delegát.</span><span class="sxs-lookup"><span data-stu-id="1ceee-256">Add the following `GameOver` method and corresponding delegate to the form class.</span></span> <span data-ttu-id="1ceee-257">Po dokončení pracovního postupu Tato metoda aktualizuje uživatelské rozhraní formuláře odebráním ID instance dokončeného pracovního postupu z pole se seznamem **InstanceId** .</span><span class="sxs-lookup"><span data-stu-id="1ceee-257">When a workflow completes, this method updates the form UI by removing the instance id of the completed workflow from the **InstanceId** combo box.</span></span>

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

### <a name="BKMK_ConfigureWorkflowApplication"></a><span data-ttu-id="1ceee-258">Konfigurace úložiště instancí, obslužných rutin životního cyklu pracovního postupu a rozšíření</span><span class="sxs-lookup"><span data-stu-id="1ceee-258">To configure the instance store, workflow lifecycle handlers, and extensions</span></span>

1. <span data-ttu-id="1ceee-259">`ConfigureWorkflowApplication` Přidejte metodu do třídy Form.</span><span class="sxs-lookup"><span data-stu-id="1ceee-259">Add a `ConfigureWorkflowApplication` method to the form class.</span></span>

    ```vb
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)

    End Sub
    ```

    ```csharp
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)
    {
    }
    ```

    <span data-ttu-id="1ceee-260">Tato metoda konfiguruje `WorkflowApplication`, přidá požadovaná rozšíření a přidá obslužné rutiny pro události životního cyklu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-260">This method configures the `WorkflowApplication`, adds the desired extensions, and adds handlers for the workflow lifecycle events.</span></span>

2. <span data-ttu-id="1ceee-261">V `ConfigureWorkflowApplication` Zadejte`SqlWorkflowInstanceStore` pro .`WorkflowApplication`</span><span class="sxs-lookup"><span data-stu-id="1ceee-261">In `ConfigureWorkflowApplication`, specify the `SqlWorkflowInstanceStore` for the `WorkflowApplication`.</span></span>

    ```vb
    'Configure the persistence store.
    wfApp.InstanceStore = store
    ```

    ```csharp
    // Configure the persistence store.
    wfApp.InstanceStore = store;
    ```

3. <span data-ttu-id="1ceee-262">Dále vytvořte `StringWriter` instanci a přidejte ji `Extensions` do kolekce `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="1ceee-262">Next, create a `StringWriter` instance and add it to the `Extensions` collection of the `WorkflowApplication`.</span></span> <span data-ttu-id="1ceee-263">Když se přidá do rozšíření, zachytí všechny `WriteLine` výstupy aktivity. `StringWriter`</span><span class="sxs-lookup"><span data-stu-id="1ceee-263">When a `StringWriter` is added to the extensions it captures all `WriteLine` activity output.</span></span> <span data-ttu-id="1ceee-264">Když je pracovní postup nečinný, `WriteLine` lze výstup extrahovat `StringWriter` z a zobrazeného ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="1ceee-264">When the workflow becomes idle, the `WriteLine` output can be extracted from the `StringWriter` and displayed on the form.</span></span>

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

4. <span data-ttu-id="1ceee-265">Přidejte následující obslužnou rutinu pro `Completed` událost.</span><span class="sxs-lookup"><span data-stu-id="1ceee-265">Add the following handler for the `Completed` event.</span></span> <span data-ttu-id="1ceee-266">Po úspěšném dokončení pracovního postupu se v okně stav zobrazí počet pokusů o odhadované číslo.</span><span class="sxs-lookup"><span data-stu-id="1ceee-266">When a workflow successfully completes, the number of turns taken to guess the number is displayed to the status window.</span></span> <span data-ttu-id="1ceee-267">Pokud se pracovní postup ukončí, zobrazí se informace o výjimce, která způsobila ukončení.</span><span class="sxs-lookup"><span data-stu-id="1ceee-267">If the workflow terminates, the exception information that caused the termination is displayed.</span></span> <span data-ttu-id="1ceee-268">Na konci obslužné rutiny `GameOver` je volána metoda, která odebere dokončený pracovní postup ze seznamu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-268">At the end of the handler the `GameOver` method is called, which removes the completed workflow from the workflow list.</span></span>

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

5. <span data-ttu-id="1ceee-269">Přidejte následující `Aborted` obslužné rutiny a `OnUnhandledException` .</span><span class="sxs-lookup"><span data-stu-id="1ceee-269">Add the following `Aborted` and `OnUnhandledException` handlers.</span></span> <span data-ttu-id="1ceee-270">Metoda není volána `Aborted` z obslužné rutiny, protože když je instance pracovního postupu přerušena, nekončí, a je možné instanci obnovit později. `GameOver`</span><span class="sxs-lookup"><span data-stu-id="1ceee-270">The `GameOver` method is not called from the `Aborted` handler because when a workflow instance is aborted, it does not terminate, and it is possible to resume the instance at a later time.</span></span>

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

6. <span data-ttu-id="1ceee-271">Přidejte následující `PersistableIdle` obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-271">Add the following `PersistableIdle` handler.</span></span> <span data-ttu-id="1ceee-272">Tato obslužná rutina `StringWriter` načte rozšíření, které bylo přidáno, extrahuje výstup `WriteLine` z aktivit a zobrazí jej v okně stav.</span><span class="sxs-lookup"><span data-stu-id="1ceee-272">This handler retrieves the `StringWriter` extension that was added, extracts the output from the `WriteLine` activities, and displays it in the status window.</span></span>

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

    <span data-ttu-id="1ceee-273">Výčet má tři hodnoty: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>a <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction></span><span class="sxs-lookup"><span data-stu-id="1ceee-273">The <xref:System.Activities.PersistableIdleAction> enumeration has three values: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, and <xref:System.Activities.PersistableIdleAction.Unload>.</span></span> <span data-ttu-id="1ceee-274"><xref:System.Activities.PersistableIdleAction.Persist>způsobí, že pracovní postup zůstane zachován, ale nezpůsobí, že se pracovní postup uvolní.</span><span class="sxs-lookup"><span data-stu-id="1ceee-274"><xref:System.Activities.PersistableIdleAction.Persist> causes the workflow to persist but it does not cause the workflow to unload.</span></span> <span data-ttu-id="1ceee-275"><xref:System.Activities.PersistableIdleAction.Unload>způsobí, že se pracovní postup uchová a uvolní.</span><span class="sxs-lookup"><span data-stu-id="1ceee-275"><xref:System.Activities.PersistableIdleAction.Unload> causes the workflow to persist and be unloaded.</span></span>

    <span data-ttu-id="1ceee-276">Následující příklad je dokončená `ConfigureWorkflowApplication` metoda.</span><span class="sxs-lookup"><span data-stu-id="1ceee-276">The following example is the completed `ConfigureWorkflowApplication` method.</span></span>

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

### <a name="BKMK_WorkflowVersionMap"></a><span data-ttu-id="1ceee-277">Povolení spouštění a obnovování více typů pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1ceee-277">To enable starting and resuming multiple workflow types</span></span>

<span data-ttu-id="1ceee-278">Aby bylo možné obnovit instanci pracovního postupu, musí hostitel zadat definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-278">In order to resume a workflow instance, the host has to provide the workflow definition.</span></span> <span data-ttu-id="1ceee-279">V tomto kurzu existují tři typy pracovních postupů a další kroky kurzu představují více verzí těchto typů.</span><span class="sxs-lookup"><span data-stu-id="1ceee-279">In this tutorial there are three workflow types, and subsequent tutorial steps introduce multiple versions of these types.</span></span> <span data-ttu-id="1ceee-280">`WorkflowIdentity`poskytuje způsob, jak může hostitelská aplikace přidružit identifikační informace k trvalé instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-280">`WorkflowIdentity` provides a way for a host application to associate identifying information with a persisted workflow instance.</span></span> <span data-ttu-id="1ceee-281">Kroky v této části ukazují, jak vytvořit třídu nástrojů, která vám pomůže s mapováním identity pracovního postupu z trvalé instance pracovního postupu na odpovídající definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-281">The steps in this section demonstrate how to create a utility class to assist with mapping the workflow identity from a persisted workflow instance to the corresponding workflow definition.</span></span> <span data-ttu-id="1ceee-282">Další informace o `WorkflowIdentity` a verzi najdete v tématu [použití identita WorkflowIdentity a správy verzí](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="1ceee-282">For more information about `WorkflowIdentity` and versioning, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

1. <span data-ttu-id="1ceee-283">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **Přidat**, **Třída**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-283">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="1ceee-284">Do `WorkflowVersionMap` pole **název** zadejte a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-284">Type `WorkflowVersionMap` into the **Name** box and click **Add**.</span></span>

2. <span data-ttu-id="1ceee-285">Přidejte následující `using` příkazy nebo `Imports` v horní části souboru s ostatními `using` příkazy or `Imports` .</span><span class="sxs-lookup"><span data-stu-id="1ceee-285">Add the following `using` or `Imports` statements at the top of the file with the other `using` or `Imports` statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Activities
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Activities;
    ```

3. <span data-ttu-id="1ceee-286">Nahraďte `WorkflowVersionMap` deklaraci třídy následující deklarací.</span><span class="sxs-lookup"><span data-stu-id="1ceee-286">Replace the `WorkflowVersionMap` class declaration with the following declaration.</span></span>

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

    <span data-ttu-id="1ceee-287">`WorkflowVersionMap`obsahuje tři identity pracovního postupu, které se mapují na tři definice pracovního postupu z tohoto kurzu a používají se v následujících oddílech při spuštění a obnovení pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="1ceee-287">`WorkflowVersionMap` contains three workflow identities that map to the three workflow definitions from this tutorial and is used in the following sections when workflows are started and resumed.</span></span>

### <a name="BKMK_StartWorkflow"></a><span data-ttu-id="1ceee-288">Spuštění nového pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-288">To start a new workflow</span></span>

1. <span data-ttu-id="1ceee-289">Přidejte obslužnou rutinu `NewGame`pro. `Click`</span><span class="sxs-lookup"><span data-stu-id="1ceee-289">Add a `Click` handler for `NewGame`.</span></span> <span data-ttu-id="1ceee-290">Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na `NewGame`položku.</span><span class="sxs-lookup"><span data-stu-id="1ceee-290">To add the handler, switch to **Design View** for the form, and double-click `NewGame`.</span></span> <span data-ttu-id="1ceee-291">Přidá `NewGame_Click` se obslužná rutina a zobrazení se přepne do zobrazení kódu pro formulář.</span><span class="sxs-lookup"><span data-stu-id="1ceee-291">A `NewGame_Click` handler is added and the view switches to code view for the form.</span></span> <span data-ttu-id="1ceee-292">Vždy, když uživatel klikne na toto tlačítko, je spuštěn nový pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="1ceee-292">Whenever the user clicks this button a new workflow is started.</span></span>

    ```vb
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click

    End Sub
    ```

    ```csharp
    private void NewGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="1ceee-293">Do obslužné rutiny Click přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="1ceee-293">Add the following code to the click handler.</span></span> <span data-ttu-id="1ceee-294">Tento kód vytvoří slovník vstupních argumentů pro pracovní postup, který je označen názvem argumentu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-294">This code creates a dictionary of input arguments for the workflow, keyed by argument name.</span></span> <span data-ttu-id="1ceee-295">Tento slovník má jednu položku, která obsahuje rozsah náhodně generovaného čísla načteného z pole se seznamem rozsah.</span><span class="sxs-lookup"><span data-stu-id="1ceee-295">This dictionary has one entry that contains the range of the randomly generated number retrieved from the range combo box.</span></span>

    ```vb
    Dim inputs As New Dictionary(Of String, Object)()
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))
    ```

    ```csharp
    var inputs = new Dictionary<string, object>();
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));
    ```

3. <span data-ttu-id="1ceee-296">Dále přidejte následující kód, který spustí pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="1ceee-296">Next, add the following code that starts the workflow.</span></span> <span data-ttu-id="1ceee-297">Definice pracovního postupu `WorkflowVersionMap` aodpovídajícítypuvybranéhopracovníhopostupusenačte`WorkflowIdentity` pomocí pomocné třídy.</span><span class="sxs-lookup"><span data-stu-id="1ceee-297">The `WorkflowIdentity` and workflow definition corresponding to the type of workflow selected are retrieved using the `WorkflowVersionMap` helper class.</span></span> <span data-ttu-id="1ceee-298">V dalším kroku se `WorkflowApplication` vytvoří nová instance pomocí definice pracovního postupu, `WorkflowIdentity`a slovníku vstupních argumentů.</span><span class="sxs-lookup"><span data-stu-id="1ceee-298">Next, a new `WorkflowApplication` instance is created using the workflow definition, `WorkflowIdentity`, and dictionary of input arguments.</span></span>

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

4. <span data-ttu-id="1ceee-299">Dále přidejte následující kód, který přidá pracovní postup do seznamu pracovních postupů a zobrazí informace o verzi pracovního postupu ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="1ceee-299">Next, add the following code which adds the workflow to the workflow list and displays the workflow's version information on the form.</span></span>

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

5. <span data-ttu-id="1ceee-300">Zavolejte `ConfigureWorkflowApplication` ke konfiguraci obslužných rutin pro úložiště instancí, rozšíření a životního cyklu `WorkflowApplication` pracovního postupu pro tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="1ceee-300">Call `ConfigureWorkflowApplication` to configure the instance store, extensions, and workflow lifecycle handlers for this `WorkflowApplication` instance.</span></span>

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

6. <span data-ttu-id="1ceee-301">Nakonec zavolejte `Run`.</span><span class="sxs-lookup"><span data-stu-id="1ceee-301">Finally, call `Run`.</span></span>

    ```vb
    'Start the workflow.
    wfApp.Run()
    ```

    ```csharp
    // Start the workflow.
    wfApp.Run();
    ```

     <span data-ttu-id="1ceee-302">Následující příklad je dokončená `NewGame_Click` obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="1ceee-302">The following example is the completed `NewGame_Click` handler.</span></span>

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

### <a name="BKMK_ResumeWorkflow"></a><span data-ttu-id="1ceee-303">Obnovení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-303">To resume a workflow</span></span>

1. <span data-ttu-id="1ceee-304">Přidejte obslužnou rutinu `EnterGuess`pro. `Click`</span><span class="sxs-lookup"><span data-stu-id="1ceee-304">Add a `Click` handler for `EnterGuess`.</span></span> <span data-ttu-id="1ceee-305">Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na `EnterGuess`položku.</span><span class="sxs-lookup"><span data-stu-id="1ceee-305">To add the handler, switch to **Design View** for the form, and double-click `EnterGuess`.</span></span> <span data-ttu-id="1ceee-306">Vždy, když uživatel klikne na toto tlačítko, bude pracovní postup obnoven.</span><span class="sxs-lookup"><span data-stu-id="1ceee-306">Whenever the user clicks this button a workflow is resumed.</span></span>

    ```vb
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click

    End Sub
    ```

    ```csharp
    private void EnterGuess_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="1ceee-307">Přidejte následující kód, abyste se ujistili, že je v seznamu pracovního postupu vybraný pracovní postup a že je odhad uživatele platný.</span><span class="sxs-lookup"><span data-stu-id="1ceee-307">Add the following code to ensure that a workflow is selected in the workflow list, and that the user's guess is valid.</span></span>

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

3. <span data-ttu-id="1ceee-308">V `WorkflowApplicationInstance` dalším kroku načtěte trvalou instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-308">Next, retrieve the `WorkflowApplicationInstance` of the persisted workflow instance.</span></span> <span data-ttu-id="1ceee-309">`WorkflowApplicationInstance` Představuje trvalou instanci pracovního postupu, která ještě nebyla přidružena k definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-309">A `WorkflowApplicationInstance` represents a persisted workflow instance that has not yet been associated with a workflow definition.</span></span> <span data-ttu-id="1ceee-310">`DefinitionIdentity` Z`WorkflowApplicationInstance`obsahujeinstancitrvaléhopracovníhopostupu. `WorkflowIdentity`</span><span class="sxs-lookup"><span data-stu-id="1ceee-310">The `DefinitionIdentity` of the `WorkflowApplicationInstance` contains the `WorkflowIdentity` of the persisted workflow instance.</span></span> <span data-ttu-id="1ceee-311">V tomto kurzu `WorkflowVersionMap` se třída utility používá k `WorkflowIdentity` mapování správné definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-311">In this tutorial, the `WorkflowVersionMap` utility class is used to map the `WorkflowIdentity` to the correct workflow definition.</span></span> <span data-ttu-id="1ceee-312">Po načtení definice pracovního postupu se vytvoří a `WorkflowApplication` pomocí správné definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-312">Once the workflow definition is retrieved, a `WorkflowApplication` is created, using the correct workflow definition.</span></span>

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

4. <span data-ttu-id="1ceee-313">Po vytvoření nakonfigurujte úložiště instancí, obslužné rutiny životního cyklu pracovního postupu a rozšíření tím, že zavoláte `ConfigureWorkflowApplication`. `WorkflowApplication`</span><span class="sxs-lookup"><span data-stu-id="1ceee-313">Once the `WorkflowApplication` is created, configure the instance store, workflow lifecycle handlers, and extensions by calling `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="1ceee-314">Tyto kroky je nutné provést při každém vytvoření nového `WorkflowApplication` a musí být provedeny před načtením instance pracovního postupu `WorkflowApplication`do.</span><span class="sxs-lookup"><span data-stu-id="1ceee-314">These steps must be done every time a new `WorkflowApplication` is created, and they must be done before the workflow instance is loaded into the `WorkflowApplication`.</span></span> <span data-ttu-id="1ceee-315">Po načtení je pracovní postup obnovený s odhadem uživatele.</span><span class="sxs-lookup"><span data-stu-id="1ceee-315">After the workflow is loaded, it is resumed with the user's guess.</span></span>

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

5. <span data-ttu-id="1ceee-316">Nakonec zrušte zaškrtnutí políčka odhad a připravte formulář, abyste mohli akceptovat další odhad.</span><span class="sxs-lookup"><span data-stu-id="1ceee-316">Finally, clear the guess textbox and prepare the form to accept another guess.</span></span>

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

    <span data-ttu-id="1ceee-317">Následující příklad je dokončená `EnterGuess_Click` obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="1ceee-317">The following example is the completed `EnterGuess_Click` handler.</span></span>

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

### <a name="BKMK_TerminateWorkflow"></a><span data-ttu-id="1ceee-318">Ukončení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ceee-318">To terminate a workflow</span></span>

1. <span data-ttu-id="1ceee-319">Přidejte obslužnou rutinu `QuitGame`pro. `Click`</span><span class="sxs-lookup"><span data-stu-id="1ceee-319">Add a `Click` handler for `QuitGame`.</span></span> <span data-ttu-id="1ceee-320">Chcete-li přidat obslužnou rutinu, přepněte do **zobrazení Návrh** formuláře a dvakrát klikněte na `QuitGame`položku.</span><span class="sxs-lookup"><span data-stu-id="1ceee-320">To add the handler, switch to **Design View** for the form, and double-click `QuitGame`.</span></span> <span data-ttu-id="1ceee-321">Vždy, když uživatel klikne na toto tlačítko, je ukončen aktuálně vybraný pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="1ceee-321">Whenever the user clicks this button the currently selected workflow is terminated.</span></span>

    ```vb
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click

    End Sub
    ```

    ```csharp
    private void QuitGame_Click(object sender, EventArgs e)
    {

    }
    ```

2. <span data-ttu-id="1ceee-322">Přidejte následující kód do `QuitGame_Click` obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="1ceee-322">Add the following code to the `QuitGame_Click` handler.</span></span> <span data-ttu-id="1ceee-323">Tento kód nejprve kontroluje, zda je v seznamu pracovních postupů vybrán pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="1ceee-323">This code first checks to ensure that a workflow is selected in the workflow list.</span></span> <span data-ttu-id="1ceee-324">Poté načte trvalou instanci do a `WorkflowApplicationInstance`, `DefinitionIdentity` používá k určení správné definice pracovního postupu a poté inicializuje `WorkflowApplication`.</span><span class="sxs-lookup"><span data-stu-id="1ceee-324">Then it loads the persisted instance into a `WorkflowApplicationInstance`, uses the `DefinitionIdentity` to determine the correct workflow definition, and then initializes the `WorkflowApplication`.</span></span> <span data-ttu-id="1ceee-325">Dále jsou nakonfigurované obslužné rutiny pro rozšíření a životní cyklus pracovního `ConfigureWorkflowApplication`postupu pro volání.</span><span class="sxs-lookup"><span data-stu-id="1ceee-325">Next the extensions and workflow lifecycle handlers are configured with a call to `ConfigureWorkflowApplication`.</span></span> <span data-ttu-id="1ceee-326">Po nakonfigurování se načte a potom `Terminate` se zavolá. `WorkflowApplication`</span><span class="sxs-lookup"><span data-stu-id="1ceee-326">Once the `WorkflowApplication` is configured, it is loaded, and then `Terminate` is called.</span></span>

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

### <a name="BKMK_BuildAndRun"></a><span data-ttu-id="1ceee-327">Sestavení a spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="1ceee-327">To build and run the application</span></span>

1. <span data-ttu-id="1ceee-328">Dvakrát klikněte na **program.cs** (nebo **Module1. vb**) v **Průzkumník řešení** pro zobrazení kódu.</span><span class="sxs-lookup"><span data-stu-id="1ceee-328">Double-click **Program.cs** (or **Module1.vb**) in **Solution Explorer** to display the code.</span></span>

2. <span data-ttu-id="1ceee-329">Do horní části `using` souboru přidejte `Imports`následující příkaz (nebo) pomocí příkazů other `using` (nebo `Imports`).</span><span class="sxs-lookup"><span data-stu-id="1ceee-329">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Windows.Forms;
    ```

3. <span data-ttu-id="1ceee-330">Odeberte nebo Odkomentujte existující kód hostování pracovního postupu [pomocí postupu: Spusťte pracovní postup](how-to-run-a-workflow.md)a nahraďte ho následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="1ceee-330">Remove or comment out the existing workflow hosting code from [How to: Run a Workflow](how-to-run-a-workflow.md), and replace it with the following code.</span></span>

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

4. <span data-ttu-id="1ceee-331">V **Průzkumník řešení** klikněte pravým tlačítkem na **NumberGuessWorkflowHost** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-331">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Properties**.</span></span> <span data-ttu-id="1ceee-332">Na kartě **aplikace** zadejte pro **Typ výstupu** **aplikace systému Windows** .</span><span class="sxs-lookup"><span data-stu-id="1ceee-332">In the **Application** tab, specify **Windows Application** for the **Output type**.</span></span> <span data-ttu-id="1ceee-333">Tento krok je nepovinný, ale pokud se nedodržuje, zobrazí se kromě formuláře okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="1ceee-333">This step is optional, but if it is not followed the console window is displayed in addition to the form.</span></span>

5. <span data-ttu-id="1ceee-334">Stisknutím kombinace kláves CTRL + SHIFT + B sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1ceee-334">Press Ctrl+Shift+B to build the application.</span></span>

6. <span data-ttu-id="1ceee-335">Zajistěte, aby byla aplikace **NumberGuessWorkflowHost** nastavená jako spouštěcí aplikace, a stisknutím kláves CTRL + F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1ceee-335">Ensure that **NumberGuessWorkflowHost** is set as the startup application, and press Ctrl+F5 to start the application.</span></span>

7. <span data-ttu-id="1ceee-336">Vyberte rozsah pro odhad hry a typ pracovního postupu, který chcete spustit, a klikněte na **Nová hra**.</span><span class="sxs-lookup"><span data-stu-id="1ceee-336">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="1ceee-337">V poli **odhad** zadejte odhad a kliknutím na tlačítko **Přejít** odešlete svůj odhad.</span><span class="sxs-lookup"><span data-stu-id="1ceee-337">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="1ceee-338">Všimněte si, že výstup `WriteLine` aktivit se zobrazí ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="1ceee-338">Note that the output from the `WriteLine` activities is displayed on the form.</span></span>

8. <span data-ttu-id="1ceee-339">Spusťte několik pracovních postupů pomocí různých typů pracovních postupů a rozsahů čísel, zadejte několik odhadů a přepněte mezi pracovními postupy výběrem ze seznamu **ID instance pracovního postupu** .</span><span class="sxs-lookup"><span data-stu-id="1ceee-339">Start several workflows using different workflow types and number ranges, enter some guesses, and switch between the workflows by selecting from the **Workflow Instance Id** list.</span></span>

    <span data-ttu-id="1ceee-340">Všimněte si, že když přepnete na nový pracovní postup, předchozí odhad a průběh pracovního postupu se v okně stav nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="1ceee-340">Note that when you switch to a new workflow, the previous guesses and progress of the workflow are not displayed in the status window.</span></span> <span data-ttu-id="1ceee-341">Důvod, proč stav není k dispozici, je, že není zachycen a ukládán nikde.</span><span class="sxs-lookup"><span data-stu-id="1ceee-341">The reason the status is not available is because it is not captured and saved anywhere.</span></span> <span data-ttu-id="1ceee-342">V dalším kroku kurzu [: Vytvořte vlastního účastníka](how-to-create-a-custom-tracking-participant.md)sledování a vytvořte vlastního účastníka sledování, který tyto informace uloží.</span><span class="sxs-lookup"><span data-stu-id="1ceee-342">In the next step of the tutorial, [How to: Create a Custom Tracking Participant](how-to-create-a-custom-tracking-participant.md), you create a custom tracking participant that saves this information.</span></span>
