---
title: Použití aktivity InvokePowerShell
ms.date: 03/30/2017
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
ms.openlocfilehash: fa42cddd930b755e9938a02a137ee77ee273fad0
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595276"
---
# <a name="using-the-invokepowershell-activity"></a><span data-ttu-id="96984-102">Použití aktivity InvokePowerShell</span><span class="sxs-lookup"><span data-stu-id="96984-102">Using the InvokePowerShell Activity</span></span>
<span data-ttu-id="96984-103">Ukázka InvokePowerShell ukazuje, jak vyvolat pomocí příkazů prostředí Windows PowerShell `InvokePowerShell` aktivity.</span><span class="sxs-lookup"><span data-stu-id="96984-103">The InvokePowerShell sample demonstrates how to invoke Windows PowerShell commands using the `InvokePowerShell` activity.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="96984-104">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="96984-104">Demonstrates</span></span>  
  
-   <span data-ttu-id="96984-105">Jednoduché inovace z příkazů prostředí Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96984-105">Simple innovation of Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="96984-106">Načtení hodnot z výstupu kanálu Windows Powershellu a uložit je do proměnné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="96984-106">Retrieve values from the Windows PowerShell output pipeline and store them in workflow variables.</span></span>  
  
-   <span data-ttu-id="96984-107">Předejte data do windows Powershellu jako vstupní kanál pro provádění příkazu.</span><span class="sxs-lookup"><span data-stu-id="96984-107">Pass data into windows PowerShell as input pipeline for an executing command.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="96984-108">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="96984-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="96984-109">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="96984-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="96984-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="96984-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="96984-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="96984-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a><span data-ttu-id="96984-112">Diskuse</span><span class="sxs-lookup"><span data-stu-id="96984-112">Discussion</span></span>  
 <span data-ttu-id="96984-113">Tato ukázka obsahuje následující tři projekty.</span><span class="sxs-lookup"><span data-stu-id="96984-113">This sample contains the following three projects.</span></span>  
  
|<span data-ttu-id="96984-114">Název projektu</span><span class="sxs-lookup"><span data-stu-id="96984-114">Project Name</span></span>|<span data-ttu-id="96984-115">Popis</span><span class="sxs-lookup"><span data-stu-id="96984-115">Description</span></span>|<span data-ttu-id="96984-116">Hlavní soubory</span><span class="sxs-lookup"><span data-stu-id="96984-116">Main Files</span></span>|  
|------------------|-----------------|----------------|  
|<span data-ttu-id="96984-117">CodedClient</span><span class="sxs-lookup"><span data-stu-id="96984-117">CodedClient</span></span>|<span data-ttu-id="96984-118">Ukázková klientská aplikace, která používá aktivitu prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96984-118">A sample client application that uses the PowerShell activity.</span></span>|<span data-ttu-id="96984-119">-   **Soubor program.cs**: prostřednictvím kódu programu pracovních postupů podle pořadí, která volá aktivity InvokePowerShell vytvoří.</span><span class="sxs-lookup"><span data-stu-id="96984-119">-   **Program.cs**: Programmatically creates a sequence-based workflow that calls the InvokePowerShell activity.</span></span>|  
|<span data-ttu-id="96984-120">DesignerClient</span><span class="sxs-lookup"><span data-stu-id="96984-120">DesignerClient</span></span>|<span data-ttu-id="96984-121">Sadu vlastních aktivit, které obsahují `InvokePowerShell` vlastní aktivity a dalších vedlejších vlastní aktivity a pracovní postup, který je využívá.</span><span class="sxs-lookup"><span data-stu-id="96984-121">A set of custom activities that contain the `InvokePowerShell` custom activity and other miscellaneous custom activities, and a workflow that uses them.</span></span>|<ul><li><span data-ttu-id="96984-122">Aktivity:</span><span class="sxs-lookup"><span data-stu-id="96984-122">Activities:</span></span><br /><br /> <ul><li><span data-ttu-id="96984-123">**PrintCollection.cs**: aktivitu pomocné rutiny, která vytiskne všechny položky v kolekci do konzoly.</span><span class="sxs-lookup"><span data-stu-id="96984-123">**PrintCollection.cs**: A helper activity that prints all the items in a collection to the console.</span></span></li><li><span data-ttu-id="96984-124">**ReadLine.cs**: aktivita pomocné rutiny pro čtení vstupu z konzoly.</span><span class="sxs-lookup"><span data-stu-id="96984-124">**ReadLine.cs**: A helper activity for reading input from the console.</span></span></li></ul></li><li><span data-ttu-id="96984-125">Systém souborů:</span><span class="sxs-lookup"><span data-stu-id="96984-125">File System:</span></span><br /><br /> <ul><li><span data-ttu-id="96984-126">**Copy.XAML**: aktivitu, která zkopíruje soubor.</span><span class="sxs-lookup"><span data-stu-id="96984-126">**Copy.xaml**: An activity that copies a file.</span></span></li><li><span data-ttu-id="96984-127">**CreateFile.xaml**: aktivitu, která vytvoří soubor.</span><span class="sxs-lookup"><span data-stu-id="96984-127">**CreateFile.xaml**: An activity that creates a file.</span></span></li><li><span data-ttu-id="96984-128">**DeleteFile.xaml**: aktivitu, která odstraní soubor.</span><span class="sxs-lookup"><span data-stu-id="96984-128">**DeleteFile.xaml**: An activity that deletes a file.</span></span></li><li><span data-ttu-id="96984-129">**MakeDir.xaml**: aktivitu, která vytvoří adresář.</span><span class="sxs-lookup"><span data-stu-id="96984-129">**MakeDir.xaml**: An activity that creates a directory.</span></span></li><li><span data-ttu-id="96984-130">**Move.XAML**: aktivitu, která se přesune do souboru.</span><span class="sxs-lookup"><span data-stu-id="96984-130">**Move.xaml**: An activity that moves a file.</span></span></li><li><span data-ttu-id="96984-131">**ReadFile.xaml**: aktivitu, která načte soubor a vrátí jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="96984-131">**ReadFile.xaml**: An activity that reads a file and returns its contents.</span></span></li><li><span data-ttu-id="96984-132">**TestPath.xaml**: aktivitu, která otestuje existenci cestu.</span><span class="sxs-lookup"><span data-stu-id="96984-132">**TestPath.xaml**: An activity that tests for the existence of a path.</span></span></li></ul></li><li><span data-ttu-id="96984-133">Proces:</span><span class="sxs-lookup"><span data-stu-id="96984-133">Process:</span></span><br /><br /> <ul><li><span data-ttu-id="96984-134">**GetProcess.xaml**: aktivitu, která načte seznam spuštěných procesů.</span><span class="sxs-lookup"><span data-stu-id="96984-134">**GetProcess.xaml**: An activity that gets a list of running processes.</span></span></li><li><span data-ttu-id="96984-135">**StopProcess.xaml**: aktivitu, která zastaví konkrétní proces.</span><span class="sxs-lookup"><span data-stu-id="96984-135">**StopProcess.xaml**: An activity that stops a specific process.</span></span></li></ul></li><li><span data-ttu-id="96984-136">**Soubor program.cs**: volá Sequence1 pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="96984-136">**Program.cs**: Calls the Sequence1 workflow.</span></span></li><li><span data-ttu-id="96984-137">**Sequence1.XAML**: pracovních postupů založených na pořadí.</span><span class="sxs-lookup"><span data-stu-id="96984-137">**Sequence1.xaml**: A sequence-based workflow.</span></span></li></ul>|  
|<span data-ttu-id="96984-138">PowerShell</span><span class="sxs-lookup"><span data-stu-id="96984-138">PowerShell</span></span>|<span data-ttu-id="96984-139">`InvokePowerShell` Aktivita a její přidružené designeru.</span><span class="sxs-lookup"><span data-stu-id="96984-139">The `InvokePowerShell` activity and its associated designers.</span></span>|<span data-ttu-id="96984-140">Soubory aktivit</span><span class="sxs-lookup"><span data-stu-id="96984-140">Activity Files</span></span><br /><br /> <span data-ttu-id="96984-141">-   **ExecutePowerShell.cs**: logika hlavní spuštění aktivity.</span><span class="sxs-lookup"><span data-stu-id="96984-141">-   **ExecutePowerShell.cs**: The main execution logic of the activity.</span></span><br /><span data-ttu-id="96984-142">-   **InvokePowerShell.cs**: obálku kolem logika hlavní spuštění, který obsahuje obecný (návratová hodnota) verze a verze neobecnou (bez návratová hodnota).</span><span class="sxs-lookup"><span data-stu-id="96984-142">-   **InvokePowerShell.cs**: The wrapper around the main execution logic, which contains a generic (return value) version and a non-generic (non-return value) version.</span></span> <span data-ttu-id="96984-143">Toto je veřejné rozhraní pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="96984-143">This is the public interface for the activity.</span></span><br /><span data-ttu-id="96984-144">-   **NoPersistZone.cs**: Tato aktivita zabraňuje uchování všechny podřízené aktivity.</span><span class="sxs-lookup"><span data-stu-id="96984-144">-   **NoPersistZone.cs**: This activity prevents any child activities from persisting.</span></span> <span data-ttu-id="96984-145">Tato třída se používá v rámci `InvokePowerShell` implementace aktivitu do aktivity brání trvalý uprostřed zpracování.</span><span class="sxs-lookup"><span data-stu-id="96984-145">This class is used within the `InvokePowerShell` activity implementation to prevent the activity from being persisted mid-execution.</span></span><br /><br /> <span data-ttu-id="96984-146">Soubory návrháře:</span><span class="sxs-lookup"><span data-stu-id="96984-146">Designer files:</span></span><br /><br /> <span data-ttu-id="96984-147">1.  **ArgumentDictionaryEditor.cs**: dialogové okno A Windows, který umožňuje uživateli upravit argumentů `InvokePowerShell` aktivity.</span><span class="sxs-lookup"><span data-stu-id="96984-147">1.  **ArgumentDictionaryEditor.cs**: A Windows dialog that allows the user to edit the arguments of the `InvokePowerShell` activity.</span></span><br /><span data-ttu-id="96984-148">2.  **GenericInvokePowerShellDesigner.xaml** a **GenericInvokePowerShellDesigner.xaml.cs**: definuje vzhled elementů Obecné `InvokePowerShell` aktivity v [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="96984-148">2.  **GenericInvokePowerShellDesigner.xaml** and **GenericInvokePowerShellDesigner.xaml.cs**: Defines the appearance of the generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span><br /><span data-ttu-id="96984-149">3.  **InvokePowerShellDesigner.xaml** a **InvokePowerShellDesigner.cs**: definuje vzhled elementů neobecné `InvokePowerShell` aktivity v [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="96984-149">3.  **InvokePowerShellDesigner.xaml** and **InvokePowerShellDesigner.cs**: Defines the appearance of the non-generic `InvokePowerShell` activity in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>|  
  
 <span data-ttu-id="96984-150">Klientské projekty jsou popsány nejprve, jak je lze snáze pochopit vnitřní funkce Powershellu aktivity po jeho použití je srozumitelný.</span><span class="sxs-lookup"><span data-stu-id="96984-150">The client projects are discussed first, as it is easier to understand the internal functionality of the PowerShell activity once its use is understood.</span></span>  
  
## <a name="using-this-sample"></a><span data-ttu-id="96984-151">Pomocí této ukázky</span><span class="sxs-lookup"><span data-stu-id="96984-151">Using This Sample</span></span>  
 <span data-ttu-id="96984-152">Následující části popisují způsob použití tří projektů v ukázce.</span><span class="sxs-lookup"><span data-stu-id="96984-152">The following sections describe how to use the three projects in the sample.</span></span>  
  
### <a name="using-the-coded-client-project"></a><span data-ttu-id="96984-153">Pomocí programového klientský projekt</span><span class="sxs-lookup"><span data-stu-id="96984-153">Using the Coded Client Project</span></span>  
 <span data-ttu-id="96984-154">Klient ukázka vytvoří prostřednictvím kódu programu sekvenční aktivitu, která obsahuje příklady použití několika různých metod `InvokePowerShell` aktivity.</span><span class="sxs-lookup"><span data-stu-id="96984-154">The sample client programmatically creates a sequence activity, which contains examples of several different methods of using the `InvokePowerShell` activity.</span></span> <span data-ttu-id="96984-155">Před prvním vyvoláním spustí program Poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="96984-155">The first invocation launches Notepad.</span></span>  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 <span data-ttu-id="96984-156">Druhé volání získá seznam procesů spuštěných na místním počítači.</span><span class="sxs-lookup"><span data-stu-id="96984-156">The second invocation gets a list of the processes running on the local machine.</span></span>  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 <span data-ttu-id="96984-157">`Output` slouží k uložení výstupu příkazu proměnné.</span><span class="sxs-lookup"><span data-stu-id="96984-157">`Output` is the variable used to store the output of the command.</span></span>  
  
 <span data-ttu-id="96984-158">Další volání ukazuje, jak spustit krok následného zpracování na každé jednotlivé výstupu při vyvolání prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96984-158">The next call demonstrates how to run a post-processing step on each individual output of the PowerShell invocation.</span></span> <span data-ttu-id="96984-159">`InitializationAction` je nastaven na funkce, jejichž výstupem jsou řetězcovou reprezentaci pro každý proces.</span><span class="sxs-lookup"><span data-stu-id="96984-159">`InitializationAction` is set to the function that outputs a string representation for each process.</span></span> <span data-ttu-id="96984-160">V je vrácena kolekci z těchto řetězců `Output` proměnnou `InvokePowerShell<string>` aktivity.</span><span class="sxs-lookup"><span data-stu-id="96984-160">The collection of these strings is returned in the `Output` variable by the `InvokePowerShell<string>` activity.</span></span>  
  
 <span data-ttu-id="96984-161">Následných `InvokePowerShell` volání ukazují předání dat do aktivity a výstupů a chyby navýšení kapacity.</span><span class="sxs-lookup"><span data-stu-id="96984-161">The succeeding `InvokePowerShell` calls demonstrate passing data into the activity and getting outputs and errors out.</span></span>  
  
### <a name="using-the-designer-client-project"></a><span data-ttu-id="96984-162">Pomocí návrháře klientský projekt</span><span class="sxs-lookup"><span data-stu-id="96984-162">Using the Designer Client Project</span></span>  
 <span data-ttu-id="96984-163">Projekt DesignerClient sestává ze sady vlastních aktivit, téměř všechny z nich jsou sestaveny obsahující `InvokePowerShell` aktivity.</span><span class="sxs-lookup"><span data-stu-id="96984-163">The DesignerClient project consists of a set of custom activities, almost all of which are built containing the `InvokePowerShell` activity.</span></span> <span data-ttu-id="96984-164">Většina aktivit volání obecné verzi `InvokePowerShell` aktivitu a ne očekávají, že návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="96984-164">Most of the activities call the non-generic version of the `InvokePowerShell` activity, and do not expect a return value.</span></span> <span data-ttu-id="96984-165">Další aktivity použít obecné verzi `InvokePowerShell` aktivity a použití `InitializationAction` argument následného zpracování výsledků.</span><span class="sxs-lookup"><span data-stu-id="96984-165">Other activities use the generic version of the `InvokePowerShell` activity, and use the `InitializationAction` argument to post-process the results.</span></span>  
  
## <a name="using-the-powershell-project"></a><span data-ttu-id="96984-166">Pomocí prostředí PowerShell projektu</span><span class="sxs-lookup"><span data-stu-id="96984-166">Using the PowerShell Project</span></span>  
 <span data-ttu-id="96984-167">Hlavní akce aktivity probíhá `ExecutePowerShell` třídy.</span><span class="sxs-lookup"><span data-stu-id="96984-167">The main action of the activity takes place in the `ExecutePowerShell` class.</span></span> <span data-ttu-id="96984-168">Protože spouštění příkazů prostředí PowerShell by neměla blokovat vlákno hlavní pracovního postupu, vytvoří se aktivity být asynchronní aktivita děděním z <xref:System.Activities.AsyncCodeActivity> třídy.</span><span class="sxs-lookup"><span data-stu-id="96984-168">Because the execution of PowerShell commands should not block the main workflow thread, the activity is created to be an asynchronous activity by inheriting from the <xref:System.Activities.AsyncCodeActivity> class.</span></span>  
  
 <span data-ttu-id="96984-169"><xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Metoda je volána modulem runtime pracovního postupu zahájíte spuštění aktivity.</span><span class="sxs-lookup"><span data-stu-id="96984-169">The <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> method is called by the workflow runtime to begin running the activity.</span></span> <span data-ttu-id="96984-170">Spustí voláním rozhraní API prostředí PowerShell k vytvoření kanálu prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96984-170">It starts by calling PowerShell APIs to create a PowerShell pipeline.</span></span>  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 <span data-ttu-id="96984-171">Potom příkaz prostředí PowerShell vytvoří a naplní s parametry a proměnné.</span><span class="sxs-lookup"><span data-stu-id="96984-171">It then creates a PowerShell command and populates it with parameters and variables.</span></span>  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 <span data-ttu-id="96984-172">Vstupy směrované v se také odesílají do kanálu v tomto okamžiku.</span><span class="sxs-lookup"><span data-stu-id="96984-172">The inputs piped in are also sent to the pipeline at this point.</span></span> <span data-ttu-id="96984-173">Nakonec je obalen kanálu `PipelineInvokerAsyncResult` objekt a vrátí.</span><span class="sxs-lookup"><span data-stu-id="96984-173">Finally, the pipeline is wrapped in a `PipelineInvokerAsyncResult` object and returned.</span></span> <span data-ttu-id="96984-174">`PipelineInvokerAsyncResult` Objekt zaregistruje naslouchací proces a vyvolá kanál.</span><span class="sxs-lookup"><span data-stu-id="96984-174">The `PipelineInvokerAsyncResult` object registers a listener and invokes the pipeline.</span></span>  
  
```  
pipeline.InvokeAsync();  
```  
  
 <span data-ttu-id="96984-175">Po dokončení provádění výstup a chyby jsou uloženy v rámci stejného `PipelineInvokerAsyncResult` objektu a ovládací prvek bude předán zpět do modulu runtime pracovního postupu zavoláním metody zpětného volání původně předána <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span><span class="sxs-lookup"><span data-stu-id="96984-175">When execution finishes, output and errors are stored within the same `PipelineInvokerAsyncResult` object, and control is handed back to the workflow runtime by calling the callback method originally passed to <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>.</span></span>  
  
 <span data-ttu-id="96984-176">Na konci metody provedení volání modulu runtime pracovního postupu aktivity <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="96984-176">At the end of the method's execution, the workflow runtime calls the activity’s <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> method.</span></span>  
  
 <span data-ttu-id="96984-177">`InvokePowerShell` Třídy zalomí `ExecutePowerShellCommand` třídy a vytvoří dvě verze aktivity; obecné verzi a obecné verze.</span><span class="sxs-lookup"><span data-stu-id="96984-177">The `InvokePowerShell` class wraps the `ExecutePowerShellCommand` class and creates two versions of the activity; a generic version and a non-generic version.</span></span> <span data-ttu-id="96984-178">Verze neobecnou vrátí její výstup spouštění prostředí PowerShell přímo, zatímco transformuje jednotlivé výsledky obecného typu Obecné verze.</span><span class="sxs-lookup"><span data-stu-id="96984-178">The non-generic version returns the output of the PowerShell execution directly, whereas the generic version transforms the individual results to the generic type.</span></span>  
  
 <span data-ttu-id="96984-179">Obecné verzi aktivity je implementovaný jako sekvenční pracovní postup, který volá `ExecutePowerShellCommand` a následného zpracovává jeho výsledky.</span><span class="sxs-lookup"><span data-stu-id="96984-179">The generic version of the activity is implemented as a sequential workflow that calls `ExecutePowerShellCommand` and post-processes its results.</span></span> <span data-ttu-id="96984-180">Pro každý prvek v kolekci výsledek volání krok následného zpracování `InitializationAction` Pokud je nastavena.</span><span class="sxs-lookup"><span data-stu-id="96984-180">For each element in the result collection, the post-processing step calls `InitializationAction` if it is set.</span></span> <span data-ttu-id="96984-181">V opačném případě provádí jednoduché přetypování.</span><span class="sxs-lookup"><span data-stu-id="96984-181">Otherwise, it does a simple cast.</span></span>  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 <span data-ttu-id="96984-182">Pro každý z nich `InvokePowerShell` aktivity (obecných a neobecných), návrháře byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="96984-182">For each of the two `InvokePowerShell` activities (generic, and non-generic), a designer was created.</span></span> <span data-ttu-id="96984-183">InvokePowerShellDesigner.xaml a její přidružené .cs souboru definujte vzhled v [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] obecné verzi `InvokePowerShell` aktivity.</span><span class="sxs-lookup"><span data-stu-id="96984-183">InvokePowerShellDesigner.xaml and its associated .cs file define the appearance in [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] for the non-generic version of the `InvokePowerShell` activity.</span></span> <span data-ttu-id="96984-184">Uvnitř InvokePowerShellDesigner.xaml <xref:System.Windows.Controls.DockPanel> se používá k reprezentování grafické rozhraní.</span><span class="sxs-lookup"><span data-stu-id="96984-184">Inside InvokePowerShellDesigner.xaml, a <xref:System.Windows.Controls.DockPanel> is used to represent the graphical interface.</span></span>  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 <span data-ttu-id="96984-185">Všimněte si, že `Text` vlastnosti textového pole je obousměrnou vazbu, která zajistí, že hodnota aktivity `CommandText` vlastnost je ekvivalentní hodnotu vstupu do návrháře.</span><span class="sxs-lookup"><span data-stu-id="96984-185">Note that the `Text` property of the text box is a two-way binding that ensures that the value of the activity’s `CommandText` property is equivalent to the value input into the designer.</span></span>  
  
 <span data-ttu-id="96984-186">GenericInvokePowerShellDesigner.xaml a její přidružené .cs soubor definují grafické rozhraní pro obecné `InvokePowerShell` aktivity.</span><span class="sxs-lookup"><span data-stu-id="96984-186">GenericInvokePowerShellDesigner.xaml and its associated .cs file define the graphical interface for the generic `InvokePowerShell` activity.</span></span> <span data-ttu-id="96984-187">Návrhář je o něco složitější, protože umožňuje uživatelům nastavit `InitializationAction`.</span><span class="sxs-lookup"><span data-stu-id="96984-187">The designer is slightly more complicated because it allows users to set an `InitializationAction`.</span></span> <span data-ttu-id="96984-188">Je klíčovým prvkem použití <xref:System.Activities.Presentation.WorkflowItemPresenter> povolení přetažení myší podřízených aktivit do `InvokePowerShell` návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="96984-188">The key element is the usage of <xref:System.Activities.Presentation.WorkflowItemPresenter> to allow drag and drop of child activities onto the `InvokePowerShell` designer surface.</span></span>  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 <span data-ttu-id="96984-189">Přizpůsobení řešení pro banku návrháře, ale nezastaví se soubory .xaml, které definují vzhled aktivity na plátno s návrhem.</span><span class="sxs-lookup"><span data-stu-id="96984-189">The designer customization does not stop with the .xaml files that define the appearance of the activity on the design canvas.</span></span> <span data-ttu-id="96984-190">Dialogová okna slouží k zobrazení parametry aktivity se taky dají upravit.</span><span class="sxs-lookup"><span data-stu-id="96984-190">The dialog boxes used to display the parameters of the activity can also be customized.</span></span> <span data-ttu-id="96984-191">Tyto parametry a proměnné prostředí PowerShell ovlivňují chování příkazů Powershellu.</span><span class="sxs-lookup"><span data-stu-id="96984-191">These parameters and PowerShell variables affect the behavior of PowerShell commands.</span></span> <span data-ttu-id="96984-192">Aktivita poskytuje jako <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` typy.</span><span class="sxs-lookup"><span data-stu-id="96984-192">The activity exposes them as <!--zz <xref:System.Collections.Generic.Dictionary%601>--> `System.Collections.Generic.Dictionary` types.</span></span> <span data-ttu-id="96984-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml a PropertyEditorResources.cs definovat dialogovém okně, které slouží k úpravě těchto typů.</span><span class="sxs-lookup"><span data-stu-id="96984-193">ArgumentDictionaryEditor.cs, PropertyEditorResources.xaml and PropertyEditorResources.cs define the dialog box that allows you to edit these types.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="96984-194">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="96984-194">To set up, build, and run the sample</span></span>  
 <span data-ttu-id="96984-195">Je nutné nainstalovat prostředí Windows PowerShell pro tuto ukázku spustit.</span><span class="sxs-lookup"><span data-stu-id="96984-195">You must install Windows PowerShell to run this sample.</span></span> <span data-ttu-id="96984-196">Prostředí Windows PowerShell můžete nainstalovat z tohoto umístění: [prostředí Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383).</span><span class="sxs-lookup"><span data-stu-id="96984-196">Windows PowerShell can be installed from this location: [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383).</span></span>  
  
#### <a name="to-run-the-coded-client"></a><span data-ttu-id="96984-197">Spustit programový klienta</span><span class="sxs-lookup"><span data-stu-id="96984-197">To run the coded client</span></span>  
  
1.  <span data-ttu-id="96984-198">Otevřít pomocí PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="96984-198">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="96984-199">Klikněte pravým tlačítkem na řešení a sestavte ho.</span><span class="sxs-lookup"><span data-stu-id="96984-199">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="96984-200">Klikněte pravým tlačítkem myši **CodedClient** projektu a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="96984-200">Right-click the **CodedClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="96984-201">Stisknutím kláves CTRL + F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="96984-201">Press CTRL+F5 to run the application.</span></span>  
  
#### <a name="to-run-the-designer-client"></a><span data-ttu-id="96984-202">Ke spuštění návrháře klienta</span><span class="sxs-lookup"><span data-stu-id="96984-202">To run the designer client</span></span>  
  
1.  <span data-ttu-id="96984-203">Otevřít pomocí PowerShell.sln [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="96984-203">Open PowerShell.sln using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="96984-204">Klikněte pravým tlačítkem na řešení a sestavte ho.</span><span class="sxs-lookup"><span data-stu-id="96984-204">Right-click the solution and build it.</span></span>  
  
3.  <span data-ttu-id="96984-205">Klikněte pravým tlačítkem myši **DesignerClient** projektu a vyberte **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="96984-205">Right-click the **DesignerClient** project and select **Set as Startup Project**.</span></span>  
  
4.  <span data-ttu-id="96984-206">Stisknutím kláves CTRL + F5 spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="96984-206">Press CTRL+F5 to run the application.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="96984-207">Známé problémy</span><span class="sxs-lookup"><span data-stu-id="96984-207">Known Issues</span></span>  
  
1.  <span data-ttu-id="96984-208">Pokud odkazující `InvokePowerShell` sestavení aktivit nebo z jiného projektu výsledkem chyba sestavení projektu, budete muset ručně přidat `<SpecificVersion>True</SpecificVersion>` elementu do nového projektu v rámci řádku, který odkazuje na soubor .csproj `InvokePowerShell`.</span><span class="sxs-lookup"><span data-stu-id="96984-208">If referencing the `InvokePowerShell` activity assembly or project from another project results in a build error, you may need to manually add the `<SpecificVersion>True</SpecificVersion>` element to the .csproj file of the new project under the line that references `InvokePowerShell`.</span></span>  
  
2.  <span data-ttu-id="96984-209">Pokud není nainstalováno prostředí Windows PowerShell, tato chybová zpráva se zobrazí v sadě Visual Studio, jakmile přidáte `InvokePowerShell` aktivitu do pracovního postupu: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span><span class="sxs-lookup"><span data-stu-id="96984-209">If Windows PowerShell is not installed, the following error message is displayed in Visual Studio as soon as you add an `InvokePowerShell` activity onto a workflow: `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`</span></span>  
  
3.  <span data-ttu-id="96984-210">V rozhraní Windows PowerShell 2.0, programově volá `$input.MoveNext()` selže a skriptů pomocí `$input.MoveNext()` neúmyslným chybám a výsledky.</span><span class="sxs-lookup"><span data-stu-id="96984-210">In Windows PowerShell 2.0, programmatically calling `$input.MoveNext()` fails and scripts using `$input.MoveNext()` produce unintended errors and results.</span></span> <span data-ttu-id="96984-211">Chcete-li tento problém obejít, zvažte použití příkaz prostředí PowerShell `foreach` namísto volání metody `MoveNext()` při iteraci pole.</span><span class="sxs-lookup"><span data-stu-id="96984-211">To work around this issue, consider using the PowerShell verb `foreach` instead of calling `MoveNext()` when iterating an array.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="96984-212">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="96984-212">The samples may already be installed on your machine.</span></span> <span data-ttu-id="96984-213">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="96984-213">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="96984-214">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="96984-214">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="96984-215">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="96984-215">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`