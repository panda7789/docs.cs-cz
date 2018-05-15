---
title: 'Návod: Vytváření rozšiřitelné aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 292447fa3cf2dbad70dbfef32b7c184b250ed25e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="walkthrough-creating-an-extensible-application"></a><span data-ttu-id="a9a55-102">Návod: Vytváření rozšiřitelné aplikace</span><span class="sxs-lookup"><span data-stu-id="a9a55-102">Walkthrough: Creating an Extensible Application</span></span>
<span data-ttu-id="a9a55-103">Tento návod popisuje, jak vytvořit kanál pro doplněk provádí jednoduché Kalkulačka funkcí.</span><span class="sxs-lookup"><span data-stu-id="a9a55-103">This walkthrough describes how to create a pipeline for an add-in that performs simple calculator functions.</span></span> <span data-ttu-id="a9a55-104">Nepředvádí scénářem z reálného prostředí; Místo toho ukazuje základní funkce kanálu a jak doplňku poskytuje služby pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="a9a55-104">It does not demonstrate a real-world scenario; rather, it demonstrates the basic functionality of a pipeline and how an add-in can provide services for a host.</span></span>  
  
 <span data-ttu-id="a9a55-105">Tento návod popisuje následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="a9a55-105">This walkthrough describes the following tasks:</span></span>  
  
-   <span data-ttu-id="a9a55-106">Vytváření řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9a55-106">Creating a Visual Studio solution.</span></span>  
  
-   <span data-ttu-id="a9a55-107">Vytvoření kanálu adresářové struktury.</span><span class="sxs-lookup"><span data-stu-id="a9a55-107">Creating the pipeline directory structure.</span></span>  
  
-   <span data-ttu-id="a9a55-108">Vytvoření kontraktu a zobrazení.</span><span class="sxs-lookup"><span data-stu-id="a9a55-108">Creating the contract and views.</span></span>  
  
-   <span data-ttu-id="a9a55-109">Vytvoření adaptéru přidat straně.</span><span class="sxs-lookup"><span data-stu-id="a9a55-109">Creating the add-in-side adapter.</span></span>  
  
-   <span data-ttu-id="a9a55-110">Vytvoření adaptéru straně hostitele.</span><span class="sxs-lookup"><span data-stu-id="a9a55-110">Creating the host-side adapter.</span></span>  
  
-   <span data-ttu-id="a9a55-111">Vytváření hostitele.</span><span class="sxs-lookup"><span data-stu-id="a9a55-111">Creating the host.</span></span>  
  
-   <span data-ttu-id="a9a55-112">Vytváření v doplňku.</span><span class="sxs-lookup"><span data-stu-id="a9a55-112">Creating the add-in.</span></span>  
  
-   <span data-ttu-id="a9a55-113">Nasazení kanálu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-113">Deploying the pipeline.</span></span>  
  
-   <span data-ttu-id="a9a55-114">Spuštění hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a9a55-114">Running the host application.</span></span>  
  
 <span data-ttu-id="a9a55-115">Tento kanál předá pouze Serializovatelné typy (<xref:System.Double> a <xref:System.String>), mezi hostitelem a doplněk.</span><span class="sxs-lookup"><span data-stu-id="a9a55-115">This pipeline passes only serializable types (<xref:System.Double> and <xref:System.String>), between the host and the add-in.</span></span> <span data-ttu-id="a9a55-116">Příklad, který ukazuje, jak předat kolekce komplexními datovými typy, naleznete v části [návod: předávání kolekce mezi hostiteli a doplňky](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span><span class="sxs-lookup"><span data-stu-id="a9a55-116">For an example that shows how to pass collections of complex data types, see [Walkthrough: Passing Collections Between Hosts and Add-Ins](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span></span>  
  
 <span data-ttu-id="a9a55-117">Definuje smlouvu pro tento kanál objektový model čtyři aritmetických operací: přidat, odečíst, násobit a dělit.</span><span class="sxs-lookup"><span data-stu-id="a9a55-117">The contract for this pipeline defines an object model of four arithmetic operations: add, subtract, multiply, and divide.</span></span> <span data-ttu-id="a9a55-118">Hostitel poskytuje doplněk rovnici k výpočtu, jako je například 2 + 2, a v doplňku vrátí výsledek na hostitele.</span><span class="sxs-lookup"><span data-stu-id="a9a55-118">The host provides the add-in with an equation to calculate, such as 2 + 2, and the add-in returns the result to the host.</span></span>  
  
 <span data-ttu-id="a9a55-119">Verze 2-in kalkulačky poskytuje více výpočtu možnosti a předvádí správy verzí.</span><span class="sxs-lookup"><span data-stu-id="a9a55-119">Version 2 of the calculator add-in provides more calculating possibilities and demonstrates versioning.</span></span> <span data-ttu-id="a9a55-120">Je popsán v [návod: povolení zpětné kompatibility jako vaše změny hostitele](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="a9a55-120">It is described in [Walkthrough: Enabling Backward Compatibility as Your Host Changes](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a9a55-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9a55-121">Prerequisites</span></span>  
 <span data-ttu-id="a9a55-122">Budete potřebovat k dokončení tohoto názorného postupu:</span><span class="sxs-lookup"><span data-stu-id="a9a55-122">You need the following to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="a9a55-123">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9a55-123">Visual Studio.</span></span>  
  
## <a name="creating-a-visual-studio-solution"></a><span data-ttu-id="a9a55-124">Vytváření řešení sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a9a55-124">Creating a Visual Studio Solution</span></span>  
 <span data-ttu-id="a9a55-125">Pomocí řešení v sadě Visual Studio projektů segmenty kanálu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-125">Use a solution in Visual Studio to contain the projects of your pipeline segments.</span></span>  
  
#### <a name="to-create-the-pipeline-solution"></a><span data-ttu-id="a9a55-126">Chcete-li vytvořit kanál řešení</span><span class="sxs-lookup"><span data-stu-id="a9a55-126">To create the pipeline solution</span></span>  
  
1.  <span data-ttu-id="a9a55-127">V sadě Visual Studio vytvořte nový projekt s názvem `Calc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-127">In Visual Studio, create a new project named `Calc1Contract`.</span></span> <span data-ttu-id="a9a55-128">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="a9a55-128">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a9a55-129">Název řešení `CalculatorV1`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-129">Name the solution `CalculatorV1`.</span></span>  
  
## <a name="creating-the-pipeline-directory-structure"></a><span data-ttu-id="a9a55-130">Vytvoření kanálu adresářové struktury</span><span class="sxs-lookup"><span data-stu-id="a9a55-130">Creating the Pipeline Directory Structure</span></span>  
 <span data-ttu-id="a9a55-131">Model doplněk vyžaduje sestavení segment kanálu, které chcete umístit do struktury určeného adresáře.</span><span class="sxs-lookup"><span data-stu-id="a9a55-131">The add-in model requires the pipeline segment assemblies to be placed in a specified directory structure.</span></span> <span data-ttu-id="a9a55-132">Další informace o struktuře kanálu najdete v tématu [požadavky na vývoj kanálu](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="a9a55-132">For more information about the pipeline structure, see [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
#### <a name="to-create-the-pipeline-directory-structure"></a><span data-ttu-id="a9a55-133">Chcete-li vytvořit strukturu adresáře kanálu</span><span class="sxs-lookup"><span data-stu-id="a9a55-133">To create the pipeline directory structure</span></span>  
  
1.  <span data-ttu-id="a9a55-134">Vytváření složky aplikace kdekoli v počítači.</span><span class="sxs-lookup"><span data-stu-id="a9a55-134">Create an application folder anywhere on your computer.</span></span>  
  
2.  <span data-ttu-id="a9a55-135">V této složce vytvořte následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="a9a55-135">In that folder, create the following structure:</span></span>  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     <span data-ttu-id="a9a55-136">Není nutné uvést struktura složek kanálu ve složce aplikace; se provádí zde pouze ke zvýšení pohodlí.</span><span class="sxs-lookup"><span data-stu-id="a9a55-136">It is not necessary to put the pipeline folder structure in your application folder; it is done here only for convenience.</span></span> <span data-ttu-id="a9a55-137">V příslušné kroku průvodce vysvětluje, jak změnit kód v případě struktura složek kanálu je v jiném umístění.</span><span class="sxs-lookup"><span data-stu-id="a9a55-137">At the appropriate step, the walkthrough explains how to change the code if the pipeline folder structure is in a different location.</span></span> <span data-ttu-id="a9a55-138">Přečtěte si diskuzi o kanálu directory požadavky v [požadavky na vývoj kanálu](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="a9a55-138">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9a55-139">`CalcV2` Složky není použit v tomto návodu, je zástupný symbol pro [návod: povolení zpětné kompatibility jako vaše změny hostitele](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="a9a55-139">The `CalcV2` folder is not used in this walkthrough; it is a placeholder for [Walkthrough: Enabling Backward Compatibility as Your Host Changes](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="creating-the-contract-and-views"></a><span data-ttu-id="a9a55-140">Vytvoření kontraktu a zobrazení</span><span class="sxs-lookup"><span data-stu-id="a9a55-140">Creating the Contract and Views</span></span>  
 <span data-ttu-id="a9a55-141">Definuje kontrakt segmentu pro tento kanál `ICalc1Contract` rozhraní, které definuje čtyři metody: `add`, `subtract`, `multiply`, a `divide`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-141">The contract segment for this pipeline defines the `ICalc1Contract` interface, which defines four methods: `add`, `subtract`, `multiply`, and `divide`.</span></span>  
  
#### <a name="to-create-the-contract"></a><span data-ttu-id="a9a55-142">K vytvoření kontraktu</span><span class="sxs-lookup"><span data-stu-id="a9a55-142">To create the contract</span></span>  
  
1.  <span data-ttu-id="a9a55-143">V sadě Visual Studio řešení s názvem `CalculatorV1`, otevřete `Calc1Contract` projektu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-143">In the Visual Studio solution named `CalculatorV1`, open the `Calc1Contract` project.</span></span>  
  
2.  <span data-ttu-id="a9a55-144">V **Průzkumníku řešení**, přidáte odkazy na následující sestavení, které chcete `Calc1Contract` projektu:</span><span class="sxs-lookup"><span data-stu-id="a9a55-144">In **Solution Explorer**, add references to the following assemblies to the `Calc1Contract` project:</span></span>  
  
     <span data-ttu-id="a9a55-145">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="a9a55-145">System.AddIn.Contract.dll</span></span>  
  
     <span data-ttu-id="a9a55-146">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="a9a55-146">System.AddIn.dll</span></span>  
  
3.  <span data-ttu-id="a9a55-147">V **Průzkumníku řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty.</span><span class="sxs-lookup"><span data-stu-id="a9a55-147">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects.</span></span>  
  
4.  <span data-ttu-id="a9a55-148">V **Průzkumníku řešení**, přidejte novou položku do projektu, pomocí **rozhraní** šablony.</span><span class="sxs-lookup"><span data-stu-id="a9a55-148">In **Solution Explorer**, add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="a9a55-149">V **přidat novou položku** dialogové okno, název rozhraní `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-149">In the **Add New Item** dialog box, name the interface `ICalc1Contract`.</span></span>  
  
5.  <span data-ttu-id="a9a55-150">V souboru rozhraní, přidejte odkazy na obor názvů pro <xref:System.AddIn.Contract> a <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="a9a55-150">In the interface file, add namespace references to <xref:System.AddIn.Contract> and <xref:System.AddIn.Pipeline>.</span></span>  
  
6.  <span data-ttu-id="a9a55-151">Použijte následující kód k dokončení tohoto kontraktu segmentu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-151">Use the following code to complete this contract segment.</span></span> <span data-ttu-id="a9a55-152">Všimněte si, že musí mít toto rozhraní <xref:System.AddIn.Pipeline.AddInContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="a9a55-152">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  <span data-ttu-id="a9a55-153">Volitelně můžete sestavte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9a55-153">Optionally, build the Visual Studio solution.</span></span> <span data-ttu-id="a9a55-154">Řešení nelze spustit, dokud poslední postup, ale vytváření ho po každý postup zajišťuje, že každý projekt, opravte.</span><span class="sxs-lookup"><span data-stu-id="a9a55-154">The solution cannot be run until the final procedure, but building it after each procedure ensures that each project is correct.</span></span>  
  
 <span data-ttu-id="a9a55-155">Protože zobrazení add-in a hostitel zobrazení doplněk obvykle mají stejný kód, zejména v první verzi doplňku, můžete snadno vytvořit zobrazení ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-155">Because the add-in view and the host view of the add-in usually have the same code, especially in the first version of an add-in, you can easily create the views at the same time.</span></span> <span data-ttu-id="a9a55-156">Se liší pouze jediný faktor: Zobrazit doplněk vyžaduje <xref:System.AddIn.Pipeline.AddInBaseAttribute> atributu při zobrazení hostitele add-in nevyžaduje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="a9a55-156">They differ by only one factor: the add-in view requires the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute, while the host view of the add-in does not require any attributes.</span></span>  
  
#### <a name="to-create-the-add-in-view"></a><span data-ttu-id="a9a55-157">Vytvoření zobrazení doplňku</span><span class="sxs-lookup"><span data-stu-id="a9a55-157">To create the add-in view</span></span>  
  
1.  <span data-ttu-id="a9a55-158">Přidat nový projekt s názvem `Calc1AddInView` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="a9a55-158">Add a new project named `Calc1AddInView` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a9a55-159">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="a9a55-159">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a9a55-160">V **Průzkumníku řešení**, přidejte odkaz na System.AddIn.dll k `Calc1AddInView` projektu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-160">In **Solution Explorer**, add a reference to System.AddIn.dll to the `Calc1AddInView` project.</span></span>  
  
3.  <span data-ttu-id="a9a55-161">V **Průzkumníku řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty a přidat novou položku do projektu pomocí **rozhraní** šablony.</span><span class="sxs-lookup"><span data-stu-id="a9a55-161">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="a9a55-162">V **přidat novou položku** dialogové okno, název rozhraní `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-162">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
4.  <span data-ttu-id="a9a55-163">V souboru rozhraní přidat odkaz na obor názvů <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="a9a55-163">In the interface file, add a namespace reference to <xref:System.AddIn.Pipeline>.</span></span>  
  
5.  <span data-ttu-id="a9a55-164">Použijte následující kód k dokončení tohoto doplňku zobrazení.</span><span class="sxs-lookup"><span data-stu-id="a9a55-164">Use the following code to complete this add-in view.</span></span> <span data-ttu-id="a9a55-165">Všimněte si, že musí mít toto rozhraní <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="a9a55-165">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  <span data-ttu-id="a9a55-166">Volitelně můžete sestavte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9a55-166">Optionally, build the Visual Studio solution.</span></span>  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a><span data-ttu-id="a9a55-167">Vytvoření zobrazení hostitele add-in</span><span class="sxs-lookup"><span data-stu-id="a9a55-167">To create the host view of the add-in</span></span>  
  
1.  <span data-ttu-id="a9a55-168">Přidat nový projekt s názvem `Calc1HVA` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="a9a55-168">Add a new project named `Calc1HVA` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a9a55-169">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="a9a55-169">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a9a55-170">V **Průzkumníku řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty a přidat novou položku do projektu pomocí **rozhraní** šablony.</span><span class="sxs-lookup"><span data-stu-id="a9a55-170">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="a9a55-171">V **přidat novou položku** dialogové okno, název rozhraní `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-171">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
3.  <span data-ttu-id="a9a55-172">V souboru rozhraní použijte následující kód k dokončení hostitelském zobrazení v doplňku.</span><span class="sxs-lookup"><span data-stu-id="a9a55-172">In the interface file, use the following code to complete the host view of the add-in.</span></span>  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  <span data-ttu-id="a9a55-173">Volitelně můžete sestavte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9a55-173">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in-side-adapter"></a><span data-ttu-id="a9a55-174">Vytvoření adaptéru přidat straně</span><span class="sxs-lookup"><span data-stu-id="a9a55-174">Creating the Add-in-side Adapter</span></span>  
 <span data-ttu-id="a9a55-175">Tento adaptér přidat straně se skládá z jednoho zobrazení kontrakt adaptéru.</span><span class="sxs-lookup"><span data-stu-id="a9a55-175">This add-in-side adapter consists of one view-to-contract adapter.</span></span> <span data-ttu-id="a9a55-176">Tento kanál segment převede typy ze zobrazení doplněk kontrakt.</span><span class="sxs-lookup"><span data-stu-id="a9a55-176">This pipeline segment converts the types from the add-in view to the contract.</span></span>  
  
 <span data-ttu-id="a9a55-177">U tohoto kanálu v doplňku poskytuje službu na hostiteli a typy toku z v doplňku na hostitele.</span><span class="sxs-lookup"><span data-stu-id="a9a55-177">In this pipeline, the add-in provides a service to the host, and the types flow from the add-in to the host.</span></span> <span data-ttu-id="a9a55-178">Protože žádné typy toku z hostitele na doplněk, nemáte zahrnují adaptér kontrakt zobrazení na straně doplňku tohoto kanálu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-178">Because no types flow from the host to the add-in, you do not have to include a contract-to-view adapter on the add-in side of this pipeline.</span></span>  
  
#### <a name="to-create-the-add-in-side-adapter"></a><span data-ttu-id="a9a55-179">Chcete-li vytvořit adaptér přidat straně</span><span class="sxs-lookup"><span data-stu-id="a9a55-179">To create the add-in-side adapter</span></span>  
  
1.  <span data-ttu-id="a9a55-180">Přidat nový projekt s názvem `Calc1AddInSideAdapter` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="a9a55-180">Add a new project named `Calc1AddInSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a9a55-181">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="a9a55-181">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a9a55-182">V **Průzkumníku řešení**, přidáte odkazy na následující sestavení, které chcete `Calc1AddInSideAdapter` projektu:</span><span class="sxs-lookup"><span data-stu-id="a9a55-182">In **Solution Explorer**, add references to the following assemblies to the `Calc1AddInSideAdapter` project:</span></span>  
  
     <span data-ttu-id="a9a55-183">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="a9a55-183">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="a9a55-184">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="a9a55-184">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="a9a55-185">Přidejte odkazy na projekt na projekty na segmenty přiléhající kanál:</span><span class="sxs-lookup"><span data-stu-id="a9a55-185">Add project references to the projects for the adjacent pipeline segments:</span></span>  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  <span data-ttu-id="a9a55-186">Vyberte každý odkaz na projekt a v **vlastnosti** nastavit **místní kopie** k **False**.</span><span class="sxs-lookup"><span data-stu-id="a9a55-186">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="a9a55-187">V jazyce Visual Basic, použijte **odkazy** kartě **vlastnosti projektu** nastavit **místní kopie** k **False** pro dva odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="a9a55-187">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="a9a55-188">Přejmenování projektu výchozí třídu `CalculatorViewToContractAddInSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-188">Rename the project's default class `CalculatorViewToContractAddInSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="a9a55-189">V souboru třídy, přidejte odkazy na obor názvů pro <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="a9a55-189">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="a9a55-190">V souboru třídy, přidejte odkazy na obor názvů pro přiléhající segmenty: `CalcAddInViews` a `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-190">In the class file, add namespace references for the adjacent segments: `CalcAddInViews` and `CalculatorContracts`.</span></span> <span data-ttu-id="a9a55-191">(V jazyku Visual Basic, jsou tyto odkazy na obor názvů `Calc1AddInView.CalcAddInViews` a `Calc1Contract.CalculatorContracts`, pokud jste vypnuli výchozí obory názvů v projektech Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="a9a55-191">(In Visual Basic, these namespace references are `Calc1AddInView.CalcAddInViews` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="a9a55-192">Použít <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atribut `CalculatorViewToContractAddInSideAdapter` třída identifikovat jako adaptér přidat straně.</span><span class="sxs-lookup"><span data-stu-id="a9a55-192">Apply the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute to the `CalculatorViewToContractAddInSideAdapter` class, to identify it as the add-in-side adapter.</span></span>  
  
9. <span data-ttu-id="a9a55-193">Ujistěte se, `CalculatorViewToContractAddInSideAdapter` dědění třídy <xref:System.AddIn.Pipeline.ContractBase>, který poskytuje výchozí implementaci třídy <xref:System.AddIn.Contract.IContract> rozhraní a implementovat rozhraní kontraktu pro kanál, `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-193">Make the `CalculatorViewToContractAddInSideAdapter` class inherit <xref:System.AddIn.Pipeline.ContractBase>, which provides a default implementation of the <xref:System.AddIn.Contract.IContract> interface, and implement the contract interface for the pipeline, `ICalc1Contract`.</span></span>  
  
10. <span data-ttu-id="a9a55-194">Přidejte konstruktor public, který přijímá `ICalculator`, ukládá do mezipaměti v soukromé pole a volá konstruktor základní třídy.</span><span class="sxs-lookup"><span data-stu-id="a9a55-194">Add a public constructor that accepts an `ICalculator`, caches it in a private field, and calls the base class constructor.</span></span>  
  
11. <span data-ttu-id="a9a55-195">K implementaci členů `ICalc1Contract`, jednoduše volání odpovídající členů `ICalculator` instance, který je předaný konstruktoru a vrátí výsledky.</span><span class="sxs-lookup"><span data-stu-id="a9a55-195">To implement the members of `ICalc1Contract`, simply call the corresponding members of the `ICalculator` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="a9a55-196">Toto přizpůsobení zobrazení (`ICalculator`) se smlouvou (`ICalc1Contract`).</span><span class="sxs-lookup"><span data-stu-id="a9a55-196">This adapts the view (`ICalculator`) to the contract (`ICalc1Contract`).</span></span>  
  
     <span data-ttu-id="a9a55-197">Následující kód ukazuje dokončené adaptér přidat straně.</span><span class="sxs-lookup"><span data-stu-id="a9a55-197">The following code shows the completed add-in-side adapter.</span></span>  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. <span data-ttu-id="a9a55-198">Volitelně můžete sestavte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9a55-198">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host-side-adapter"></a><span data-ttu-id="a9a55-199">Vytvoření adaptéru straně hostitele</span><span class="sxs-lookup"><span data-stu-id="a9a55-199">Creating the Host-side Adapter</span></span>  
 <span data-ttu-id="a9a55-200">Tento adaptér hostitelské se skládá z jednoho zobrazení smlouvy adaptéru.</span><span class="sxs-lookup"><span data-stu-id="a9a55-200">This host-side adapter consists of one contract-to-view adapter.</span></span> <span data-ttu-id="a9a55-201">Tento segment přizpůsobuje smlouvy na hostitelském zobrazení v doplňku.</span><span class="sxs-lookup"><span data-stu-id="a9a55-201">This segment adapts the contract to the host view of the add-in.</span></span>  
  
 <span data-ttu-id="a9a55-202">U tohoto kanálu v doplňku poskytuje službu na hostiteli a typy toku z doplněk k hostiteli.</span><span class="sxs-lookup"><span data-stu-id="a9a55-202">In this pipeline, the add-in provides a service to the host and the types flow from the add-in to the host.</span></span> <span data-ttu-id="a9a55-203">Protože žádné typy toku z hostitele na doplněk, nemáte zahrnují adaptér zobrazení kontrakt.</span><span class="sxs-lookup"><span data-stu-id="a9a55-203">Because no types flow from the host to the add-in, you do not have to include a view-to-contract adapter.</span></span>  
  
 <span data-ttu-id="a9a55-204">Chcete-li implementovat správu životního cyklu, použijte <xref:System.AddIn.Pipeline.ContractHandle> objekt, který chcete přiřadit kontrakt doba platnosti tokenu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-204">To implement lifetime management, use a <xref:System.AddIn.Pipeline.ContractHandle> object to attach a lifetime token to the contract.</span></span> <span data-ttu-id="a9a55-205">Odkaz na tento popisovač musí zůstat v pořadí pro správu životního cyklu pro práci.</span><span class="sxs-lookup"><span data-stu-id="a9a55-205">You must keep a reference to this handle in order for lifetime management to work.</span></span> <span data-ttu-id="a9a55-206">Po použití tokenu žádné další programování není nutná, protože v systému může odstranění objektů při jejich se již nepoužívají a zpřístupnit pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a9a55-206">After the token is applied, no additional programming is required because the add-in system can dispose of objects when they are no longer being used and make them available for garbage collection.</span></span> <span data-ttu-id="a9a55-207">Další informace najdete v tématu [správu životního cyklu](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="a9a55-207">For more information, see [Lifetime Management](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
#### <a name="to-create-the-host-side-adapter"></a><span data-ttu-id="a9a55-208">Chcete-li vytvořit adaptér straně hostitele</span><span class="sxs-lookup"><span data-stu-id="a9a55-208">To create the host-side adapter</span></span>  
  
1.  <span data-ttu-id="a9a55-209">Přidat nový projekt s názvem `Calc1HostSideAdapter` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="a9a55-209">Add a new project named `Calc1HostSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a9a55-210">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="a9a55-210">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a9a55-211">V **Průzkumníku řešení**, přidáte odkazy na následující sestavení, které chcete `Calc1HostSideAdapter` projektu:</span><span class="sxs-lookup"><span data-stu-id="a9a55-211">In **Solution Explorer**, add references to the following assemblies to the `Calc1HostSideAdapter` project:</span></span>  
  
     <span data-ttu-id="a9a55-212">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="a9a55-212">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="a9a55-213">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="a9a55-213">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="a9a55-214">Přidejte odkazy na projekt na projekty na sousedících segmenty:</span><span class="sxs-lookup"><span data-stu-id="a9a55-214">Add project references to the projects for the adjacent segments:</span></span>  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  <span data-ttu-id="a9a55-215">Vyberte každý odkaz na projekt a v **vlastnosti** nastavit **místní kopie** k **False**.</span><span class="sxs-lookup"><span data-stu-id="a9a55-215">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="a9a55-216">V jazyce Visual Basic, použijte **odkazy** kartě **vlastnosti projektu** nastavit **místní kopie** k **False** pro dva odkazy na projekt.</span><span class="sxs-lookup"><span data-stu-id="a9a55-216">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="a9a55-217">Přejmenování projektu výchozí třídu `CalculatorContractToViewHostSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-217">Rename the project's default class `CalculatorContractToViewHostSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="a9a55-218">V souboru třídy, přidejte odkazy na obor názvů pro <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="a9a55-218">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="a9a55-219">V souboru třídy, přidejte odkazy na obor názvů pro přiléhající segmenty: `CalcHVAs` a `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-219">In the class file, add namespace references for the adjacent segments: `CalcHVAs` and `CalculatorContracts`.</span></span> <span data-ttu-id="a9a55-220">(V jazyku Visual Basic, jsou tyto odkazy na obor názvů `Calc1HVA.CalcHVAs` a `Calc1Contract.CalculatorContracts`, pokud jste vypnuli výchozí obory názvů v projektech Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="a9a55-220">(In Visual Basic, these namespace references are `Calc1HVA.CalcHVAs` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="a9a55-221">Použít <xref:System.AddIn.Pipeline.HostAdapterAttribute> atribut `CalculatorContractToViewHostSideAdapter` třída identifikovat jako adaptér hostitelské segment.</span><span class="sxs-lookup"><span data-stu-id="a9a55-221">Apply the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute to the `CalculatorContractToViewHostSideAdapter` class, to identify it as the host-side adapter segment.</span></span>  
  
9. <span data-ttu-id="a9a55-222">Ujistěte se, `CalculatorContractToViewHostSideAdapter` třída implementovat rozhraní, které představuje hostitelském zobrazení v doplňku: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a9a55-222">Make the `CalculatorContractToViewHostSideAdapter` class implement the interface that represents the host view of the add-in: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` in Visual Basic).</span></span>  
  
10. <span data-ttu-id="a9a55-223">Přidejte konstruktor public, který přijímá kontrakt typ kanálu `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-223">Add a public constructor that accepts the pipeline contract type, `ICalc1Contract`.</span></span> <span data-ttu-id="a9a55-224">Konstruktor musí mezipaměti odkaz na kontrakt.</span><span class="sxs-lookup"><span data-stu-id="a9a55-224">The constructor must cache the reference to the contract.</span></span> <span data-ttu-id="a9a55-225">Musíte také vytvořit a mezipaměti novou <xref:System.AddIn.Pipeline.ContractHandle> pro kontrakt, Správa životního cyklu add-in.</span><span class="sxs-lookup"><span data-stu-id="a9a55-225">It must also create and cache a new <xref:System.AddIn.Pipeline.ContractHandle> for the contract, to manage the lifetime of the add-in.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a9a55-226"><xref:System.AddIn.Pipeline.ContractHandle> Je důležité pro správu životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-226">The <xref:System.AddIn.Pipeline.ContractHandle> is critical to lifetime management.</span></span> <span data-ttu-id="a9a55-227">Pokud se nepodaří zachovat odkaz na <xref:System.AddIn.Pipeline.ContractHandle> objektu uvolňování paměti se uvolnit ho a kanál vypne, pokud váš program neočekává.</span><span class="sxs-lookup"><span data-stu-id="a9a55-227">If you fail to keep a reference to the <xref:System.AddIn.Pipeline.ContractHandle> object, garbage collection will reclaim it, and the pipeline will shut down when your program does not expect it.</span></span> <span data-ttu-id="a9a55-228">To může způsobit chyby, které je obtížné diagnostikovat, jako například <xref:System.AppDomainUnloadedException>.</span><span class="sxs-lookup"><span data-stu-id="a9a55-228">This can lead to errors that are difficult to diagnose, such as <xref:System.AppDomainUnloadedException>.</span></span> <span data-ttu-id="a9a55-229">Vypnutí je normální úsek dobu životnosti kanál, takže neexistuje žádný způsob pro kód životního cyklu správy ke zjištění, zda tento stav se o chybu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-229">Shutdown is a normal stage in the life of a pipeline, so there is no way for the lifetime management code to detect that this condition is an error.</span></span>  
  
11. <span data-ttu-id="a9a55-230">K implementaci členů `ICalculator`, jednoduše volání odpovídající členů `ICalc1Contract` instance, který je předaný konstruktoru a vrátí výsledky.</span><span class="sxs-lookup"><span data-stu-id="a9a55-230">To implement the members of `ICalculator`, simply call the corresponding members of the `ICalc1Contract` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="a9a55-231">Toto přizpůsobení kontrakt (`ICalc1Contract`) k zobrazení (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="a9a55-231">This adapts the contract (`ICalc1Contract`) to the view (`ICalculator`).</span></span>  
  
     <span data-ttu-id="a9a55-232">Následující kód ukazuje dokončené adaptér straně hostitele.</span><span class="sxs-lookup"><span data-stu-id="a9a55-232">The following code shows the completed host-side adapter.</span></span>  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. <span data-ttu-id="a9a55-233">Volitelně můžete sestavte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9a55-233">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host"></a><span data-ttu-id="a9a55-234">Vytváření hostitele</span><span class="sxs-lookup"><span data-stu-id="a9a55-234">Creating the Host</span></span>  
 <span data-ttu-id="a9a55-235">Komunikuje se službou doplněk prostřednictvím hostitelském zobrazení doplněk hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a9a55-235">A host application interacts with the add-in through the host view of the add-in.</span></span> <span data-ttu-id="a9a55-236">Využívá doplněk zjišťování a aktivaci metody poskytované <xref:System.AddIn.Hosting.AddInStore> a <xref:System.AddIn.Hosting.AddInToken> třídy proveďte následující:</span><span class="sxs-lookup"><span data-stu-id="a9a55-236">It uses add-in discovery and activation methods provided by the <xref:System.AddIn.Hosting.AddInStore> and <xref:System.AddIn.Hosting.AddInToken> classes to do the following:</span></span>  
  
-   <span data-ttu-id="a9a55-237">Aktualizace mezipaměti kanálu a doplněk informací.</span><span class="sxs-lookup"><span data-stu-id="a9a55-237">Update the cache of pipeline and add-in information.</span></span>  
  
-   <span data-ttu-id="a9a55-238">Najít doplňky typu zobrazení hostitele, `ICalculator`, v kořenovém adresáři zadané kanálu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-238">Find add-ins of the host view type, `ICalculator`, under the specified pipeline root directory.</span></span>  
  
-   <span data-ttu-id="a9a55-239">Vyzvat uživatele k určení, které doplněk používat.</span><span class="sxs-lookup"><span data-stu-id="a9a55-239">Prompt the user to specify which add-in to use.</span></span>  
  
-   <span data-ttu-id="a9a55-240">Aktivujte vybrané v aplikaci v nové doméně aplikace s úrovní důvěryhodnosti zadaný zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a9a55-240">Activate the selected add-in in a new application domain with a specified security trust level.</span></span>  
  
-   <span data-ttu-id="a9a55-241">Spusťte vlastní `RunCalculator` metodu, která volá metody v doplňku na podle specifikace hostitelském zobrazení v doplňku.</span><span class="sxs-lookup"><span data-stu-id="a9a55-241">Run the custom `RunCalculator` method, which calls the add-in's methods as specified by the host view of the add-in.</span></span>  
  
#### <a name="to-create-the-host"></a><span data-ttu-id="a9a55-242">Chcete-li vytvořit hostitele</span><span class="sxs-lookup"><span data-stu-id="a9a55-242">To create the host</span></span>  
  
1.  <span data-ttu-id="a9a55-243">Přidat nový projekt s názvem `Calc1Host` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="a9a55-243">Add a new project named `Calc1Host` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a9a55-244">Založit na **konzolové aplikace** šablony.</span><span class="sxs-lookup"><span data-stu-id="a9a55-244">Base it on the **Console Application** template.</span></span>  
  
2.  <span data-ttu-id="a9a55-245">V **Průzkumníku řešení**, přidejte odkaz na sestavení System.AddIn.dll do `Calc1Host` projektu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-245">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the `Calc1Host` project.</span></span>  
  
3.  <span data-ttu-id="a9a55-246">Přidat odkaz na projekt `Calc1HVA` projektu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-246">Add a project reference to the `Calc1HVA` project.</span></span> <span data-ttu-id="a9a55-247">Vyberte odkaz na projekt a v **vlastnosti** nastavit **místní kopie** k **False**.</span><span class="sxs-lookup"><span data-stu-id="a9a55-247">Select the project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="a9a55-248">V jazyce Visual Basic, použijte **odkazy** kartě **vlastnosti projektu** nastavit **místní kopie** k **False**.</span><span class="sxs-lookup"><span data-stu-id="a9a55-248">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False**.</span></span>  
  
4.  <span data-ttu-id="a9a55-249">Přejmenujte soubor – třída (modulu v jazyce Visual Basic) `MathHost1`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-249">Rename the class file (module in Visual Basic) `MathHost1`.</span></span>  
  
5.  <span data-ttu-id="a9a55-250">V jazyce Visual Basic, použijte **aplikace** kartě **vlastnosti projektu** dialogové okno nastavit **spouštěcí objekt** k **Sub Main**.</span><span class="sxs-lookup"><span data-stu-id="a9a55-250">In Visual Basic, use the **Application** tab of the **Project Properties** dialog box to set **Startup object** to **Sub Main**.</span></span>  
  
6.  <span data-ttu-id="a9a55-251">V souboru třídy nebo modulu Přidat odkaz na obor názvů <xref:System.AddIn.Hosting>.</span><span class="sxs-lookup"><span data-stu-id="a9a55-251">In the class or module file, add a namespace reference to <xref:System.AddIn.Hosting>.</span></span>  
  
7.  <span data-ttu-id="a9a55-252">V souboru třídy nebo modulu Přidat odkaz na obor názvů pro hostitele zobrazení add-in: `CalcHVAs`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-252">In the class or module file, add a namespace reference for the host view of the add-in: `CalcHVAs`.</span></span> <span data-ttu-id="a9a55-253">(V jazyku Visual Basic, je tento odkaz na obor názvů `Calc1HVA.CalcHVAs`, pokud jste vypnuli výchozí obory názvů v projektech Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="a9a55-253">(In Visual Basic, this namespace reference is `Calc1HVA.CalcHVAs`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="a9a55-254">V **Průzkumníku řešení**, vyberte řešení a z **projektu** nabídce zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a9a55-254">In **Solution Explorer**, select the solution and from the **Project** menu choose **Properties**.</span></span> <span data-ttu-id="a9a55-255">V **stránky vlastností řešení** dialogové okno, sada **jeden spouštěný projekt** jako tento projekt aplikace hostitele.</span><span class="sxs-lookup"><span data-stu-id="a9a55-255">In the **Solution Property Pages** dialog box, set the **Single Startup Project** to be this host application project.</span></span>  
  
9. <span data-ttu-id="a9a55-256">V souboru třídy nebo modulu, použijte <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> metodu za účelem aktualizace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a9a55-256">In the class or module file, use the <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> method to update the cache.</span></span> <span data-ttu-id="a9a55-257">Použít <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> metodu za účelem získání kolekce tokenů a použít <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> metodu pro aktivaci v.</span><span class="sxs-lookup"><span data-stu-id="a9a55-257">Use the <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> method to get a collection of tokens, and use the <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> method to activate an add-in.</span></span>  
  
     <span data-ttu-id="a9a55-258">Následující kód ukazuje dokončené hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a9a55-258">The following code shows the completed host application.</span></span>  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="a9a55-259">Tento kód předpokládá, že struktura složek kanál se nachází ve složce aplikace.</span><span class="sxs-lookup"><span data-stu-id="a9a55-259">This code assumes that the pipeline folder structure is located in the application folder.</span></span> <span data-ttu-id="a9a55-260">Pokud jste ho jinam, změňte řádek kódu, který nastaví `addInRoot` proměnné tak, aby se proměnná obsahuje cestu k kanálu adresářové struktury.</span><span class="sxs-lookup"><span data-stu-id="a9a55-260">If you located it elsewhere, change the line of code that sets the `addInRoot` variable, so that the variable contains the path to your pipeline directory structure.</span></span>  
  
     <span data-ttu-id="a9a55-261">Kód používá `ChooseCalculator` metoda seznam tokenů a aby se zobrazila výzva k výběru doplňku.</span><span class="sxs-lookup"><span data-stu-id="a9a55-261">The code uses a `ChooseCalculator` method to list the tokens and to prompt the user to choose an add-in.</span></span> <span data-ttu-id="a9a55-262">`RunCalculator` Metoda vyzve uživatele k jednoduché matematické výrazy, analyzuje výrazy pomocí `Parser` třídy a zobrazí výsledky vracené pomocí doplňku.</span><span class="sxs-lookup"><span data-stu-id="a9a55-262">The `RunCalculator` method prompts the user for simple math expressions, parses the expressions using the `Parser` class, and displays the results returned by the add-in.</span></span>  
  
10. <span data-ttu-id="a9a55-263">Volitelně můžete sestavte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9a55-263">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in"></a><span data-ttu-id="a9a55-264">Vytváření v aplikaci</span><span class="sxs-lookup"><span data-stu-id="a9a55-264">Creating the Add-In</span></span>  
 <span data-ttu-id="a9a55-265">Doplněk implementuje metody zadaný v zobrazení.</span><span class="sxs-lookup"><span data-stu-id="a9a55-265">An add-in implements the methods specified by the add-in view.</span></span> <span data-ttu-id="a9a55-266">Tento doplněk implementuje `Add`, `Subtract`, `Multiply`, a `Divide` operace a vrací výsledky do hostitele.</span><span class="sxs-lookup"><span data-stu-id="a9a55-266">This add-in implements the `Add`, `Subtract`, `Multiply`, and `Divide` operations and returns the results to the host.</span></span>  
  
#### <a name="to-create-the-add-in"></a><span data-ttu-id="a9a55-267">Chcete-li vytvořit v doplňku</span><span class="sxs-lookup"><span data-stu-id="a9a55-267">To create the add-in</span></span>  
  
1.  <span data-ttu-id="a9a55-268">Přidat nový projekt s názvem `AddInCalcV1` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="a9a55-268">Add a new project named `AddInCalcV1` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="a9a55-269">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="a9a55-269">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="a9a55-270">V **Průzkumníku**, přidejte odkaz na sestavení System.AddIn.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-270">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the project.</span></span>  
  
3.  <span data-ttu-id="a9a55-271">Přidat odkaz na projekt `Calc1AddInView` projektu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-271">Add a project reference to the `Calc1AddInView` project.</span></span> <span data-ttu-id="a9a55-272">Vyberte odkaz na projekt a v **vlastnosti**, nastavte **místní kopie** k **False**.</span><span class="sxs-lookup"><span data-stu-id="a9a55-272">Select the project reference, and in **Properties**, set **Copy Local** to **False**.</span></span> <span data-ttu-id="a9a55-273">V jazyce Visual Basic, použijte **odkazy** kartě **vlastnosti projektu** nastavit **místní kopie** k **False** pro odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="a9a55-273">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the project reference.</span></span>  
  
4.  <span data-ttu-id="a9a55-274">Přejmenování třídy `AddInCalcV1`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-274">Rename the class `AddInCalcV1`.</span></span>  
  
5.  <span data-ttu-id="a9a55-275">V souboru třídy, přidejte odkaz na obor názvů <xref:System.AddIn> a doplněk zobrazení segmentu: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a9a55-275">In the class file, add a namespace reference to <xref:System.AddIn> and the add-in view segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` in Visual Basic).</span></span>  
  
6.  <span data-ttu-id="a9a55-276">Použít <xref:System.AddIn.AddInAttribute> atribut `AddInCalcV1` třída k identifikaci třídy jako doplněk.</span><span class="sxs-lookup"><span data-stu-id="a9a55-276">Apply the <xref:System.AddIn.AddInAttribute> attribute to the `AddInCalcV1` class, to identify the class as an add-in.</span></span>  
  
7.  <span data-ttu-id="a9a55-277">Ujistěte se, `AddInCalcV1` třída implementovat rozhraní, které představuje zobrazení doplňku: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a9a55-277">Make the `AddInCalcV1` class implement the interface that represents the add-in view: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` in Visual Basic).</span></span>  
  
8.  <span data-ttu-id="a9a55-278">Implementace členů `ICalculator` vrácením výsledky odpovídající výpočtů.</span><span class="sxs-lookup"><span data-stu-id="a9a55-278">Implement the members of `ICalculator` by returning the results of the appropriate calculations.</span></span>  
  
     <span data-ttu-id="a9a55-279">Následující kód ukazuje dokončené doplňku.</span><span class="sxs-lookup"><span data-stu-id="a9a55-279">The following code shows the completed add-in.</span></span>  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. <span data-ttu-id="a9a55-280">Volitelně můžete sestavte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9a55-280">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="deploying-the-pipeline"></a><span data-ttu-id="a9a55-281">Nasazení kanálu</span><span class="sxs-lookup"><span data-stu-id="a9a55-281">Deploying the Pipeline</span></span>  
 <span data-ttu-id="a9a55-282">Nyní jste připraveni k sestavení a nasazení segmenty doplněk do struktury adresářů požadované kanálu.</span><span class="sxs-lookup"><span data-stu-id="a9a55-282">You are now ready to build and deploy the add-in segments to the required pipeline directory structure.</span></span>  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a><span data-ttu-id="a9a55-283">K nasazení segmentů do kanálu</span><span class="sxs-lookup"><span data-stu-id="a9a55-283">To deploy the segments to the pipeline</span></span>  
  
1.  <span data-ttu-id="a9a55-284">Pro každý projekt v řešení použít **sestavení** kartě **vlastnosti projektu** ( **zkompilovat** karta v jazyce Visual Basic) nastavit hodnotu **výstupní cesta**  ( **výstupní cesta sestavení** v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a9a55-284">For each project in the solution, use the **Build** tab of **Project Properties** (the **Compile** tab in Visual Basic) to set the value of the **Output path** (the **Build output path** in Visual Basic).</span></span> <span data-ttu-id="a9a55-285">Pokud název vaší aplikace složky `MyApp`, například by vašich projektů sestavení do následující složky:</span><span class="sxs-lookup"><span data-stu-id="a9a55-285">If you named your application folder `MyApp`, for example, your projects would build into the following folders:</span></span>  
  
    |<span data-ttu-id="a9a55-286">Projekt</span><span class="sxs-lookup"><span data-stu-id="a9a55-286">Project</span></span>|<span data-ttu-id="a9a55-287">Cesta</span><span class="sxs-lookup"><span data-stu-id="a9a55-287">Path</span></span>|  
    |-------------|----------|  
    |<span data-ttu-id="a9a55-288">AddInCalcV1</span><span class="sxs-lookup"><span data-stu-id="a9a55-288">AddInCalcV1</span></span>|<span data-ttu-id="a9a55-289">MyApp\Pipeline\AddIns\CalcV1</span><span class="sxs-lookup"><span data-stu-id="a9a55-289">MyApp\Pipeline\AddIns\CalcV1</span></span>|  
    |<span data-ttu-id="a9a55-290">Calc1AddInSideAdapter</span><span class="sxs-lookup"><span data-stu-id="a9a55-290">Calc1AddInSideAdapter</span></span>|<span data-ttu-id="a9a55-291">MyApp\Pipeline\AddInSideAdapters</span><span class="sxs-lookup"><span data-stu-id="a9a55-291">MyApp\Pipeline\AddInSideAdapters</span></span>|  
    |<span data-ttu-id="a9a55-292">Calc1AddInView</span><span class="sxs-lookup"><span data-stu-id="a9a55-292">Calc1AddInView</span></span>|<span data-ttu-id="a9a55-293">MyApp\Pipeline\AddInViews</span><span class="sxs-lookup"><span data-stu-id="a9a55-293">MyApp\Pipeline\AddInViews</span></span>|  
    |<span data-ttu-id="a9a55-294">Calc1Contract</span><span class="sxs-lookup"><span data-stu-id="a9a55-294">Calc1Contract</span></span>|<span data-ttu-id="a9a55-295">MyApp\Pipeline\Contracts</span><span class="sxs-lookup"><span data-stu-id="a9a55-295">MyApp\Pipeline\Contracts</span></span>|  
    |<span data-ttu-id="a9a55-296">Calc1Host</span><span class="sxs-lookup"><span data-stu-id="a9a55-296">Calc1Host</span></span>|<span data-ttu-id="a9a55-297">Moje aplikace</span><span class="sxs-lookup"><span data-stu-id="a9a55-297">MyApp</span></span>|  
    |<span data-ttu-id="a9a55-298">Calc1HostSideAdapter</span><span class="sxs-lookup"><span data-stu-id="a9a55-298">Calc1HostSideAdapter</span></span>|<span data-ttu-id="a9a55-299">MyApp\Pipeline\HostSideAdapters</span><span class="sxs-lookup"><span data-stu-id="a9a55-299">MyApp\Pipeline\HostSideAdapters</span></span>|  
    |<span data-ttu-id="a9a55-300">Calc1HVA</span><span class="sxs-lookup"><span data-stu-id="a9a55-300">Calc1HVA</span></span>|<span data-ttu-id="a9a55-301">Moje aplikace</span><span class="sxs-lookup"><span data-stu-id="a9a55-301">MyApp</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="a9a55-302">Pokud jste se rozhodli vrátit strukturu kanálu složku v umístění než složce aplikace, musíte upravit cesty uvedené v tabulce odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="a9a55-302">If you decided to put your pipeline folder structure in a location other than your application folder, you must modify the paths shown in the table accordingly.</span></span> <span data-ttu-id="a9a55-303">Přečtěte si diskuzi o kanálu directory požadavky v [požadavky na vývoj kanálu](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="a9a55-303">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
2.  <span data-ttu-id="a9a55-304">Sestavte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9a55-304">Build the Visual Studio solution.</span></span>  
  
3.  <span data-ttu-id="a9a55-305">Zkontrolujte adresáře aplikace a kanál zajistit, že sestavení byly zkopírovány do adresáře správný a zda byly nainstalovány žádné další kopie sestavení v nesprávný složky.</span><span class="sxs-lookup"><span data-stu-id="a9a55-305">Check the application and pipeline directories to ensure that the assemblies were copied to the correct directories and that no extra copies of assemblies were installed in the wrong folders.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9a55-306">Pokud jste nezměnili **místní kopie** k **False** pro `Calc1AddInView` odkaz v projektu `AddInCalcV1` projektu, problémů kontextu zavaděč zabrání v doplňku by byly umístěny.</span><span class="sxs-lookup"><span data-stu-id="a9a55-306">If you did not change **Copy Local** to **False** for the `Calc1AddInView` project reference in the `AddInCalcV1` project, loader context problems will prevent the add-in from being located.</span></span>  
  
     <span data-ttu-id="a9a55-307">Informace o nasazení do kanálu najdete v tématu [požadavky na vývoj kanálu](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="a9a55-307">For information about deploying to the pipeline, see [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
## <a name="running-the-host-application"></a><span data-ttu-id="a9a55-308">Spuštění aplikace hostitele</span><span class="sxs-lookup"><span data-stu-id="a9a55-308">Running the Host Application</span></span>  
 <span data-ttu-id="a9a55-309">Nyní jste připraveni ke spuštění hostitele a interakci s doplněk.</span><span class="sxs-lookup"><span data-stu-id="a9a55-309">You are now ready to run the host and interact with the add-in.</span></span>  
  
#### <a name="to-run-the-host-application"></a><span data-ttu-id="a9a55-310">Ke spuštění aplikace hostitele</span><span class="sxs-lookup"><span data-stu-id="a9a55-310">To run the host application</span></span>  
  
1.  <span data-ttu-id="a9a55-311">Na příkazovém řádku přejděte do adresáře aplikace a spusťte aplikaci hostitele `Calc1Host.exe`.</span><span class="sxs-lookup"><span data-stu-id="a9a55-311">At the command prompt, go to the application directory and run the host application, `Calc1Host.exe`.</span></span>  
  
2.  <span data-ttu-id="a9a55-312">Hostitel vyhledá všechny add in k dispozici jeho typu a výzva k výběru doplňku.</span><span class="sxs-lookup"><span data-stu-id="a9a55-312">The host finds all available add-ins of its type and prompts you to select an add-in.</span></span> <span data-ttu-id="a9a55-313">Zadejte **1** pro k dispozici pouze v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a9a55-313">Enter **1** for the only available add-in.</span></span>  
  
3.  <span data-ttu-id="a9a55-314">Zadejte rovnici kalkulačky, jako například **2 + 2**.</span><span class="sxs-lookup"><span data-stu-id="a9a55-314">Enter an equation for the calculator, such as **2 + 2**.</span></span> <span data-ttu-id="a9a55-315">Musí existovat mezery mezi čísla a operátor.</span><span class="sxs-lookup"><span data-stu-id="a9a55-315">There must be spaces between the numbers and the operator.</span></span>  
  
4.  <span data-ttu-id="a9a55-316">Typ **ukončete** a stiskněte klávesu **Enter** klíč aplikace se zavře.</span><span class="sxs-lookup"><span data-stu-id="a9a55-316">Type **exit** and press the **Enter** key to close the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a55-317">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9a55-317">See Also</span></span>  
 [<span data-ttu-id="a9a55-318">Návod: Povolení zpětné kompatibility jako hostitele změny</span><span class="sxs-lookup"><span data-stu-id="a9a55-318">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [<span data-ttu-id="a9a55-319">Návod: Předávání kolekce mezi hostiteli a doplňky</span><span class="sxs-lookup"><span data-stu-id="a9a55-319">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [<span data-ttu-id="a9a55-320">Požadavky na vývoj kanálu</span><span class="sxs-lookup"><span data-stu-id="a9a55-320">Pipeline Development Requirements</span></span>](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [<span data-ttu-id="a9a55-321">Kontrakty, zobrazení a adaptéry</span><span class="sxs-lookup"><span data-stu-id="a9a55-321">Contracts, Views, and Adapters</span></span>](http://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [<span data-ttu-id="a9a55-322">Vývoj kanálu</span><span class="sxs-lookup"><span data-stu-id="a9a55-322">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)
