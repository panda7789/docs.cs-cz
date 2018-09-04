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
ms.openlocfilehash: 5d2aaeaffaf3abbe1e8efcdb57d40e6ae60f89b5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552332"
---
# <a name="walkthrough-creating-an-extensible-application"></a><span data-ttu-id="34d9a-102">Návod: Vytváření rozšiřitelné aplikace</span><span class="sxs-lookup"><span data-stu-id="34d9a-102">Walkthrough: Creating an Extensible Application</span></span>
<span data-ttu-id="34d9a-103">Tento návod popisuje, jak vytvořit kanál pro doplněk, který provádí funkce jednoduchou kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-103">This walkthrough describes how to create a pipeline for an add-in that performs simple calculator functions.</span></span> <span data-ttu-id="34d9a-104">Nepředvádí reálný scénář; Místo toho ukazuje základní funkce kanálu a jak doplněk může poskytovat služby hostitele.</span><span class="sxs-lookup"><span data-stu-id="34d9a-104">It does not demonstrate a real-world scenario; rather, it demonstrates the basic functionality of a pipeline and how an add-in can provide services for a host.</span></span>  
  
 <span data-ttu-id="34d9a-105">Tento návod popisuje následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="34d9a-105">This walkthrough describes the following tasks:</span></span>  
  
-   <span data-ttu-id="34d9a-106">Vytváření řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34d9a-106">Creating a Visual Studio solution.</span></span>  
  
-   <span data-ttu-id="34d9a-107">Vytvoření adresářové struktury kanálu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-107">Creating the pipeline directory structure.</span></span>  
  
-   <span data-ttu-id="34d9a-108">Vytvoření kontraktu a zobrazení.</span><span class="sxs-lookup"><span data-stu-id="34d9a-108">Creating the contract and views.</span></span>  
  
-   <span data-ttu-id="34d9a-109">Vytvoření adaptéru add-na straně.</span><span class="sxs-lookup"><span data-stu-id="34d9a-109">Creating the add-in-side adapter.</span></span>  
  
-   <span data-ttu-id="34d9a-110">Vytváří se adaptér na straně hostitele.</span><span class="sxs-lookup"><span data-stu-id="34d9a-110">Creating the host-side adapter.</span></span>  
  
-   <span data-ttu-id="34d9a-111">Vytváření hostitele.</span><span class="sxs-lookup"><span data-stu-id="34d9a-111">Creating the host.</span></span>  
  
-   <span data-ttu-id="34d9a-112">Vytvoření doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-112">Creating the add-in.</span></span>  
  
-   <span data-ttu-id="34d9a-113">Nasazení kanálu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-113">Deploying the pipeline.</span></span>  
  
-   <span data-ttu-id="34d9a-114">Spuštění aplikace hostitele.</span><span class="sxs-lookup"><span data-stu-id="34d9a-114">Running the host application.</span></span>  
  
 <span data-ttu-id="34d9a-115">Tento kanál předá pouze Serializovatelné typy (<xref:System.Double> a <xref:System.String>), mezi hostitelem a doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-115">This pipeline passes only serializable types (<xref:System.Double> and <xref:System.String>), between the host and the add-in.</span></span> <span data-ttu-id="34d9a-116">Příklad, který ukazuje, jak předat kolekce komplexních datových typů, najdete v části [návod: předávání kolekcí mezi hostiteli a doplňky](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span><span class="sxs-lookup"><span data-stu-id="34d9a-116">For an example that shows how to pass collections of complex data types, see [Walkthrough: Passing Collections Between Hosts and Add-Ins](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span></span>  
  
 <span data-ttu-id="34d9a-117">Definuje smlouvu pro tento kanál objektový model, čtyři aritmetických operací: Přidání, odečíst, násobení a dělení.</span><span class="sxs-lookup"><span data-stu-id="34d9a-117">The contract for this pipeline defines an object model of four arithmetic operations: add, subtract, multiply, and divide.</span></span> <span data-ttu-id="34d9a-118">Hostitel poskytuje doplněk rovnice k výpočtu, jako je například 2 + 2, a doplněk vrátí výsledek do hostitele.</span><span class="sxs-lookup"><span data-stu-id="34d9a-118">The host provides the add-in with an equation to calculate, such as 2 + 2, and the add-in returns the result to the host.</span></span>  
  
 <span data-ttu-id="34d9a-119">Verze 2-in Kalkulačka poskytuje více výpočtu možnosti a ukazuje, správu verzí.</span><span class="sxs-lookup"><span data-stu-id="34d9a-119">Version 2 of the calculator add-in provides more calculating possibilities and demonstrates versioning.</span></span> <span data-ttu-id="34d9a-120">Je popsána v [návod: povolení zpětné kompatibility při změně vašeho hostitele](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="34d9a-120">It is described in [Walkthrough: Enabling Backward Compatibility as Your Host Changes](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="34d9a-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34d9a-121">Prerequisites</span></span>  
 <span data-ttu-id="34d9a-122">Budete potřebovat k dokončení tohoto návodu:</span><span class="sxs-lookup"><span data-stu-id="34d9a-122">You need the following to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="34d9a-123">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34d9a-123">Visual Studio.</span></span>  
  
## <a name="creating-a-visual-studio-solution"></a><span data-ttu-id="34d9a-124">Vytváření řešení sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="34d9a-124">Creating a Visual Studio Solution</span></span>  
 <span data-ttu-id="34d9a-125">Pomocí řešení obsahující projekty segmentů kanálu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34d9a-125">Use a solution in Visual Studio to contain the projects of your pipeline segments.</span></span>  
  
#### <a name="to-create-the-pipeline-solution"></a><span data-ttu-id="34d9a-126">Chcete-li vytvořit kanál řešení</span><span class="sxs-lookup"><span data-stu-id="34d9a-126">To create the pipeline solution</span></span>  
  
1.  <span data-ttu-id="34d9a-127">V sadě Visual Studio vytvořte nový projekt s názvem `Calc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-127">In Visual Studio, create a new project named `Calc1Contract`.</span></span> <span data-ttu-id="34d9a-128">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="34d9a-128">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="34d9a-129">Pojmenujte řešení `CalculatorV1`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-129">Name the solution `CalculatorV1`.</span></span>  
  
## <a name="creating-the-pipeline-directory-structure"></a><span data-ttu-id="34d9a-130">Vytvoření adresářové struktury kanálu</span><span class="sxs-lookup"><span data-stu-id="34d9a-130">Creating the Pipeline Directory Structure</span></span>  
 <span data-ttu-id="34d9a-131">Model doplňku vyžaduje sestavení segment kanálu umístěny ve struktuře zadaný adresář.</span><span class="sxs-lookup"><span data-stu-id="34d9a-131">The add-in model requires the pipeline segment assemblies to be placed in a specified directory structure.</span></span> <span data-ttu-id="34d9a-132">Další informace o struktuře kanálu najdete v tématu [požadavky na vývoj kanálu](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="34d9a-132">For more information about the pipeline structure, see [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
#### <a name="to-create-the-pipeline-directory-structure"></a><span data-ttu-id="34d9a-133">Chcete-li vytvořit strukturu adresářů kanálu</span><span class="sxs-lookup"><span data-stu-id="34d9a-133">To create the pipeline directory structure</span></span>  
  
1.  <span data-ttu-id="34d9a-134">Vytvořte složku s aplikace kdekoli ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="34d9a-134">Create an application folder anywhere on your computer.</span></span>  
  
2.  <span data-ttu-id="34d9a-135">V této složce vytvořte následující strukturu:</span><span class="sxs-lookup"><span data-stu-id="34d9a-135">In that folder, create the following structure:</span></span>  
  
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
  
     <span data-ttu-id="34d9a-136">Není nutné do kanálu strukturu složek ve složce vaší aplikace. Zde je použito pouze ke zvýšení pohodlí.</span><span class="sxs-lookup"><span data-stu-id="34d9a-136">It is not necessary to put the pipeline folder structure in your application folder; it is done here only for convenience.</span></span> <span data-ttu-id="34d9a-137">Na příslušný krok průvodce vysvětluje, jak změnit kód v případě strukturu složek kanálu je v jiném umístění.</span><span class="sxs-lookup"><span data-stu-id="34d9a-137">At the appropriate step, the walkthrough explains how to change the code if the pipeline folder structure is in a different location.</span></span> <span data-ttu-id="34d9a-138">Viz diskuze požadavky adresáře kanálu v [požadavky na vývoj kanálu](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="34d9a-138">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="34d9a-139">`CalcV2` Složky se nepoužívá v tomto názorném postupu; je zástupný symbol pro [návod: povolení zpětné kompatibility při změně vašeho hostitele](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="34d9a-139">The `CalcV2` folder is not used in this walkthrough; it is a placeholder for [Walkthrough: Enabling Backward Compatibility as Your Host Changes](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="creating-the-contract-and-views"></a><span data-ttu-id="34d9a-140">Vytvoření kontraktu a zobrazení</span><span class="sxs-lookup"><span data-stu-id="34d9a-140">Creating the Contract and Views</span></span>  
 <span data-ttu-id="34d9a-141">Definuje kontrakt segmentu pro tento kanál `ICalc1Contract` rozhraní, která definuje čtyři metody: `add`, `subtract`, `multiply`, a `divide`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-141">The contract segment for this pipeline defines the `ICalc1Contract` interface, which defines four methods: `add`, `subtract`, `multiply`, and `divide`.</span></span>  
  
#### <a name="to-create-the-contract"></a><span data-ttu-id="34d9a-142">Vytvoření kontraktu</span><span class="sxs-lookup"><span data-stu-id="34d9a-142">To create the contract</span></span>  
  
1.  <span data-ttu-id="34d9a-143">V řešení sady Visual Studio s názvem `CalculatorV1`, otevřete `Calc1Contract` projektu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-143">In the Visual Studio solution named `CalculatorV1`, open the `Calc1Contract` project.</span></span>  
  
2.  <span data-ttu-id="34d9a-144">V **Průzkumníka řešení**, přidejte odkazy na následující sestavení, které chcete `Calc1Contract` projektu:</span><span class="sxs-lookup"><span data-stu-id="34d9a-144">In **Solution Explorer**, add references to the following assemblies to the `Calc1Contract` project:</span></span>  
  
     <span data-ttu-id="34d9a-145">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="34d9a-145">System.AddIn.Contract.dll</span></span>  
  
     <span data-ttu-id="34d9a-146">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="34d9a-146">System.AddIn.dll</span></span>  
  
3.  <span data-ttu-id="34d9a-147">V **Průzkumníka řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty.</span><span class="sxs-lookup"><span data-stu-id="34d9a-147">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects.</span></span>  
  
4.  <span data-ttu-id="34d9a-148">V **Průzkumníka řešení**, přidat novou položku do projektu, použití **rozhraní** šablony.</span><span class="sxs-lookup"><span data-stu-id="34d9a-148">In **Solution Explorer**, add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="34d9a-149">V **přidat novou položku** dialogové okno, název rozhraní `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-149">In the **Add New Item** dialog box, name the interface `ICalc1Contract`.</span></span>  
  
5.  <span data-ttu-id="34d9a-150">V souboru rozhraní, přidejte odkazy na obor názvů pro <xref:System.AddIn.Contract> a <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="34d9a-150">In the interface file, add namespace references to <xref:System.AddIn.Contract> and <xref:System.AddIn.Pipeline>.</span></span>  
  
6.  <span data-ttu-id="34d9a-151">Použijte následující kód pro dokončení této smlouvy segmentu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-151">Use the following code to complete this contract segment.</span></span> <span data-ttu-id="34d9a-152">Všimněte si, že toto rozhraní musí mít <xref:System.AddIn.Pipeline.AddInContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="34d9a-152">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  <span data-ttu-id="34d9a-153">Volitelně můžete vytvářejte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34d9a-153">Optionally, build the Visual Studio solution.</span></span> <span data-ttu-id="34d9a-154">Řešení nelze spustit, dokud posledním kroku, ale jeho sestavení po každý postup zajistí, že každý projekt je opravit.</span><span class="sxs-lookup"><span data-stu-id="34d9a-154">The solution cannot be run until the final procedure, but building it after each procedure ensures that each project is correct.</span></span>  
  
 <span data-ttu-id="34d9a-155">Vzhledem k tomu, že zobrazení doplňku a hostitelem zobrazení doplňku mají obvykle stejný kód, zejména v první verzi doplňku, můžete snadno vytvořit zobrazení ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-155">Because the add-in view and the host view of the add-in usually have the same code, especially in the first version of an add-in, you can easily create the views at the same time.</span></span> <span data-ttu-id="34d9a-156">Se liší pouze jediný faktor: vyžaduje zobrazení doplňku <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut, zatímco zobrazení hostitele doplňku nevyžaduje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="34d9a-156">They differ by only one factor: the add-in view requires the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute, while the host view of the add-in does not require any attributes.</span></span>  
  
#### <a name="to-create-the-add-in-view"></a><span data-ttu-id="34d9a-157">Vytvoření zobrazení doplňku</span><span class="sxs-lookup"><span data-stu-id="34d9a-157">To create the add-in view</span></span>  
  
1.  <span data-ttu-id="34d9a-158">Přidat nový projekt s názvem `Calc1AddInView` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="34d9a-158">Add a new project named `Calc1AddInView` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="34d9a-159">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="34d9a-159">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="34d9a-160">V **Průzkumníka řešení**, přidejte odkaz na System.AddIn.dll k `Calc1AddInView` projektu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-160">In **Solution Explorer**, add a reference to System.AddIn.dll to the `Calc1AddInView` project.</span></span>  
  
3.  <span data-ttu-id="34d9a-161">V **Průzkumníka řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty a přidat novou položku do projektu, použití **rozhraní** šablony.</span><span class="sxs-lookup"><span data-stu-id="34d9a-161">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="34d9a-162">V **přidat novou položku** dialogové okno, název rozhraní `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-162">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
4.  <span data-ttu-id="34d9a-163">V souboru rozhraní, přidejte odkaz na obor názvů <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="34d9a-163">In the interface file, add a namespace reference to <xref:System.AddIn.Pipeline>.</span></span>  
  
5.  <span data-ttu-id="34d9a-164">Použijte následující kód k dokončení tohoto doplňku v zobrazení.</span><span class="sxs-lookup"><span data-stu-id="34d9a-164">Use the following code to complete this add-in view.</span></span> <span data-ttu-id="34d9a-165">Všimněte si, že toto rozhraní musí mít <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="34d9a-165">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  <span data-ttu-id="34d9a-166">Volitelně můžete vytvářejte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34d9a-166">Optionally, build the Visual Studio solution.</span></span>  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a><span data-ttu-id="34d9a-167">Chcete-li vytvořit zobrazení hostitele doplňku</span><span class="sxs-lookup"><span data-stu-id="34d9a-167">To create the host view of the add-in</span></span>  
  
1.  <span data-ttu-id="34d9a-168">Přidat nový projekt s názvem `Calc1HVA` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="34d9a-168">Add a new project named `Calc1HVA` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="34d9a-169">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="34d9a-169">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="34d9a-170">V **Průzkumníka řešení**, vyloučit výchozí třídu, která je přidána do nové **knihovny tříd** projekty a přidat novou položku do projektu, použití **rozhraní** šablony.</span><span class="sxs-lookup"><span data-stu-id="34d9a-170">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="34d9a-171">V **přidat novou položku** dialogové okno, název rozhraní `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-171">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
3.  <span data-ttu-id="34d9a-172">V souboru rozhraní použijte následující kód k dokončení zobrazení hostitele doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-172">In the interface file, use the following code to complete the host view of the add-in.</span></span>  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  <span data-ttu-id="34d9a-173">Volitelně můžete vytvářejte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34d9a-173">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in-side-adapter"></a><span data-ttu-id="34d9a-174">Vytvoření adaptéru přidat v straně</span><span class="sxs-lookup"><span data-stu-id="34d9a-174">Creating the Add-in-side Adapter</span></span>  
 <span data-ttu-id="34d9a-175">Tento adaptér přidat – na straně se skládá z jednoho adaptéru zobrazení smlouvy.</span><span class="sxs-lookup"><span data-stu-id="34d9a-175">This add-in-side adapter consists of one view-to-contract adapter.</span></span> <span data-ttu-id="34d9a-176">Tento segment kanálu převede typy ze zobrazení doplňku na kontrakt.</span><span class="sxs-lookup"><span data-stu-id="34d9a-176">This pipeline segment converts the types from the add-in view to the contract.</span></span>  
  
 <span data-ttu-id="34d9a-177">V tomto kanálu doplňku poskytuje službu na hostiteli a typy směrovat z doplňku do hostitele.</span><span class="sxs-lookup"><span data-stu-id="34d9a-177">In this pipeline, the add-in provides a service to the host, and the types flow from the add-in to the host.</span></span> <span data-ttu-id="34d9a-178">Vzhledem k tomu, že žádné typy tok z hostitele do doplňku, nemají obsahovat zobrazení smlouvy adaptér na straně doplňku tohoto kanálu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-178">Because no types flow from the host to the add-in, you do not have to include a contract-to-view adapter on the add-in side of this pipeline.</span></span>  
  
#### <a name="to-create-the-add-in-side-adapter"></a><span data-ttu-id="34d9a-179">Chcete-li vytvořit adaptér přidat v na straně</span><span class="sxs-lookup"><span data-stu-id="34d9a-179">To create the add-in-side adapter</span></span>  
  
1.  <span data-ttu-id="34d9a-180">Přidat nový projekt s názvem `Calc1AddInSideAdapter` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="34d9a-180">Add a new project named `Calc1AddInSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="34d9a-181">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="34d9a-181">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="34d9a-182">V **Průzkumníka řešení**, přidejte odkazy na následující sestavení, které chcete `Calc1AddInSideAdapter` projektu:</span><span class="sxs-lookup"><span data-stu-id="34d9a-182">In **Solution Explorer**, add references to the following assemblies to the `Calc1AddInSideAdapter` project:</span></span>  
  
     <span data-ttu-id="34d9a-183">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="34d9a-183">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="34d9a-184">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="34d9a-184">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="34d9a-185">Přidejte odkazy na projekty segmentů sousední kanálu:</span><span class="sxs-lookup"><span data-stu-id="34d9a-185">Add project references to the projects for the adjacent pipeline segments:</span></span>  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  <span data-ttu-id="34d9a-186">Vyberte každý odkaz na projekt a v **vlastnosti** nastavit **Kopírovat místně** k **False**.</span><span class="sxs-lookup"><span data-stu-id="34d9a-186">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="34d9a-187">V jazyce Visual Basic použijte **odkazy** kartě **vlastnosti projektu** nastavit **Kopírovat místně** k **False** dva odkazy projektu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-187">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="34d9a-188">Přejmenování projektu výchozí třídu `CalculatorViewToContractAddInSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-188">Rename the project's default class `CalculatorViewToContractAddInSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="34d9a-189">V souboru třídy přidejte odkazy na obor názvů pro <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="34d9a-189">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="34d9a-190">V souboru třídy přidejte odkazy na obor názvů pro sousedící segmenty: `CalcAddInViews` a `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-190">In the class file, add namespace references for the adjacent segments: `CalcAddInViews` and `CalculatorContracts`.</span></span> <span data-ttu-id="34d9a-191">(V jazyce Visual Basic, jsou tyto odkazy na obor názvů `Calc1AddInView.CalcAddInViews` a `Calc1Contract.CalculatorContracts`, pokud jste nevypnuli výchozích názvových prostorů v projektech Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="34d9a-191">(In Visual Basic, these namespace references are `Calc1AddInView.CalcAddInViews` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="34d9a-192">Použít <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atribut `CalculatorViewToContractAddInSideAdapter` třídy k jeho identifikaci jako adaptéru add-na straně.</span><span class="sxs-lookup"><span data-stu-id="34d9a-192">Apply the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute to the `CalculatorViewToContractAddInSideAdapter` class, to identify it as the add-in-side adapter.</span></span>  
  
9. <span data-ttu-id="34d9a-193">Ujistěte se, `CalculatorViewToContractAddInSideAdapter` dědit třídy <xref:System.AddIn.Pipeline.ContractBase>, která poskytuje výchozí implementaci třídy <xref:System.AddIn.Contract.IContract> rozhraní a implementují rozhraní kontraktu kanálu `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-193">Make the `CalculatorViewToContractAddInSideAdapter` class inherit <xref:System.AddIn.Pipeline.ContractBase>, which provides a default implementation of the <xref:System.AddIn.Contract.IContract> interface, and implement the contract interface for the pipeline, `ICalc1Contract`.</span></span>  
  
10. <span data-ttu-id="34d9a-194">Přidat veřejný konstruktor, který přijímá `ICalculator`ukládá do mezipaměti v soukromé pole a volá konstruktor základní třídy.</span><span class="sxs-lookup"><span data-stu-id="34d9a-194">Add a public constructor that accepts an `ICalculator`, caches it in a private field, and calls the base class constructor.</span></span>  
  
11. <span data-ttu-id="34d9a-195">K implementaci členů `ICalc1Contract`, jednoduše zavolejte odpovídající členů `ICalculator` instanci, která je předána do konstruktoru a vrátí výsledky.</span><span class="sxs-lookup"><span data-stu-id="34d9a-195">To implement the members of `ICalc1Contract`, simply call the corresponding members of the `ICalculator` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="34d9a-196">To se přizpůsobí zobrazení (`ICalculator`) pro kontrakt (`ICalc1Contract`).</span><span class="sxs-lookup"><span data-stu-id="34d9a-196">This adapts the view (`ICalculator`) to the contract (`ICalc1Contract`).</span></span>  
  
     <span data-ttu-id="34d9a-197">Následující kód ukazuje dokončené adaptér přidat v straně.</span><span class="sxs-lookup"><span data-stu-id="34d9a-197">The following code shows the completed add-in-side adapter.</span></span>  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. <span data-ttu-id="34d9a-198">Volitelně můžete vytvářejte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34d9a-198">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host-side-adapter"></a><span data-ttu-id="34d9a-199">Vytvoření adaptéru hostitelské</span><span class="sxs-lookup"><span data-stu-id="34d9a-199">Creating the Host-side Adapter</span></span>  
 <span data-ttu-id="34d9a-200">Tento adaptér hostitelské se skládá z jednoho adaptéru zobrazení smlouvy.</span><span class="sxs-lookup"><span data-stu-id="34d9a-200">This host-side adapter consists of one contract-to-view adapter.</span></span> <span data-ttu-id="34d9a-201">Tento segment se přizpůsobí smlouvy na zobrazení hostitele doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-201">This segment adapts the contract to the host view of the add-in.</span></span>  
  
 <span data-ttu-id="34d9a-202">V tomto kanálu doplňku poskytuje službu na hostiteli a flow typy z doplňku na hostitele.</span><span class="sxs-lookup"><span data-stu-id="34d9a-202">In this pipeline, the add-in provides a service to the host and the types flow from the add-in to the host.</span></span> <span data-ttu-id="34d9a-203">Vzhledem k tomu, že žádné typy tok z hostitele do doplňku, nemají obsahovat adaptér zobrazení smlouvy.</span><span class="sxs-lookup"><span data-stu-id="34d9a-203">Because no types flow from the host to the add-in, you do not have to include a view-to-contract adapter.</span></span>  
  
 <span data-ttu-id="34d9a-204">Implementace správy životního cyklu, použijte <xref:System.AddIn.Pipeline.ContractHandle> objektu, který chcete připojit ke kontraktu token doby života.</span><span class="sxs-lookup"><span data-stu-id="34d9a-204">To implement lifetime management, use a <xref:System.AddIn.Pipeline.ContractHandle> object to attach a lifetime token to the contract.</span></span> <span data-ttu-id="34d9a-205">Odkaz na tento ovladač je nutné zachovat v pořadí pro správu životního cyklu pro práci.</span><span class="sxs-lookup"><span data-stu-id="34d9a-205">You must keep a reference to this handle in order for lifetime management to work.</span></span> <span data-ttu-id="34d9a-206">Po použití tokenu není zapotřebí žádné další programování, protože v systému může uvolnila objekty když již nejsou déle používány a zpřístupnit je pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="34d9a-206">After the token is applied, no additional programming is required because the add-in system can dispose of objects when they are no longer being used and make them available for garbage collection.</span></span> <span data-ttu-id="34d9a-207">Další informace najdete v tématu [Správa životního cyklu](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="34d9a-207">For more information, see [Lifetime Management](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
#### <a name="to-create-the-host-side-adapter"></a><span data-ttu-id="34d9a-208">Chcete-li vytvořit adaptér na straně hostitele</span><span class="sxs-lookup"><span data-stu-id="34d9a-208">To create the host-side adapter</span></span>  
  
1.  <span data-ttu-id="34d9a-209">Přidat nový projekt s názvem `Calc1HostSideAdapter` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="34d9a-209">Add a new project named `Calc1HostSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="34d9a-210">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="34d9a-210">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="34d9a-211">V **Průzkumníka řešení**, přidejte odkazy na následující sestavení, které chcete `Calc1HostSideAdapter` projektu:</span><span class="sxs-lookup"><span data-stu-id="34d9a-211">In **Solution Explorer**, add references to the following assemblies to the `Calc1HostSideAdapter` project:</span></span>  
  
     <span data-ttu-id="34d9a-212">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="34d9a-212">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="34d9a-213">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="34d9a-213">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="34d9a-214">Přidejte odkazy na projekty sousední segmentů:</span><span class="sxs-lookup"><span data-stu-id="34d9a-214">Add project references to the projects for the adjacent segments:</span></span>  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  <span data-ttu-id="34d9a-215">Vyberte každý odkaz na projekt a v **vlastnosti** nastavit **Kopírovat místně** k **False**.</span><span class="sxs-lookup"><span data-stu-id="34d9a-215">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="34d9a-216">V jazyce Visual Basic použijte **odkazy** kartě **vlastnosti projektu** nastavit **Kopírovat místně** k **False** dva odkazy projektu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-216">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="34d9a-217">Přejmenování projektu výchozí třídu `CalculatorContractToViewHostSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-217">Rename the project's default class `CalculatorContractToViewHostSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="34d9a-218">V souboru třídy přidejte odkazy na obor názvů pro <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="34d9a-218">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="34d9a-219">V souboru třídy přidejte odkazy na obor názvů pro sousedící segmenty: `CalcHVAs` a `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-219">In the class file, add namespace references for the adjacent segments: `CalcHVAs` and `CalculatorContracts`.</span></span> <span data-ttu-id="34d9a-220">(V jazyce Visual Basic, jsou tyto odkazy na obor názvů `Calc1HVA.CalcHVAs` a `Calc1Contract.CalculatorContracts`, pokud jste nevypnuli výchozích názvových prostorů v projektech Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="34d9a-220">(In Visual Basic, these namespace references are `Calc1HVA.CalcHVAs` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="34d9a-221">Použít <xref:System.AddIn.Pipeline.HostAdapterAttribute> atribut `CalculatorContractToViewHostSideAdapter` třídy k jeho identifikaci jako adaptéru hostitelské segmentu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-221">Apply the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute to the `CalculatorContractToViewHostSideAdapter` class, to identify it as the host-side adapter segment.</span></span>  
  
9. <span data-ttu-id="34d9a-222">Ujistěte se, `CalculatorContractToViewHostSideAdapter` třída implementovat rozhraní, které představuje zobrazení hostitele doplňku: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="34d9a-222">Make the `CalculatorContractToViewHostSideAdapter` class implement the interface that represents the host view of the add-in: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` in Visual Basic).</span></span>  
  
10. <span data-ttu-id="34d9a-223">Přidat veřejný konstruktor, který přijímá typ kontraktu kanálu `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-223">Add a public constructor that accepts the pipeline contract type, `ICalc1Contract`.</span></span> <span data-ttu-id="34d9a-224">Konstruktor musí ukládat do mezipaměti odkaz na kontrakt.</span><span class="sxs-lookup"><span data-stu-id="34d9a-224">The constructor must cache the reference to the contract.</span></span> <span data-ttu-id="34d9a-225">Musíte také vytvořit a mezipaměti nový <xref:System.AddIn.Pipeline.ContractHandle> pro kontrakt, ke správě životnosti doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-225">It must also create and cache a new <xref:System.AddIn.Pipeline.ContractHandle> for the contract, to manage the lifetime of the add-in.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="34d9a-226"><xref:System.AddIn.Pipeline.ContractHandle> Je důležité pro správu životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-226">The <xref:System.AddIn.Pipeline.ContractHandle> is critical to lifetime management.</span></span> <span data-ttu-id="34d9a-227">Pokud selže zachovat odkaz na <xref:System.AddIn.Pipeline.ContractHandle> uvolňování paměti obnoví a kanál vypne, pokud váš program neočekává objektů.</span><span class="sxs-lookup"><span data-stu-id="34d9a-227">If you fail to keep a reference to the <xref:System.AddIn.Pipeline.ContractHandle> object, garbage collection will reclaim it, and the pipeline will shut down when your program does not expect it.</span></span> <span data-ttu-id="34d9a-228">To může vést k chybám, které je obtížné diagnostikovat, jako například <xref:System.AppDomainUnloadedException>.</span><span class="sxs-lookup"><span data-stu-id="34d9a-228">This can lead to errors that are difficult to diagnose, such as <xref:System.AppDomainUnloadedException>.</span></span> <span data-ttu-id="34d9a-229">Vypnutí je normální fázi běžný kanál, takže neexistuje žádný způsob, jak kód pro správu životního cyklu ke zjištění, že tato podmínka nastane chyba.</span><span class="sxs-lookup"><span data-stu-id="34d9a-229">Shutdown is a normal stage in the life of a pipeline, so there is no way for the lifetime management code to detect that this condition is an error.</span></span>  
  
11. <span data-ttu-id="34d9a-230">K implementaci členů `ICalculator`, jednoduše zavolejte odpovídající členů `ICalc1Contract` instanci, která je předána do konstruktoru a vrátí výsledky.</span><span class="sxs-lookup"><span data-stu-id="34d9a-230">To implement the members of `ICalculator`, simply call the corresponding members of the `ICalc1Contract` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="34d9a-231">To se přizpůsobí kontrakt (`ICalc1Contract`) k zobrazení (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="34d9a-231">This adapts the contract (`ICalc1Contract`) to the view (`ICalculator`).</span></span>  
  
     <span data-ttu-id="34d9a-232">Následující kód ukazuje dokončené adaptér na straně hostitele.</span><span class="sxs-lookup"><span data-stu-id="34d9a-232">The following code shows the completed host-side adapter.</span></span>  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. <span data-ttu-id="34d9a-233">Volitelně můžete vytvářejte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34d9a-233">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host"></a><span data-ttu-id="34d9a-234">Vytvoření hostitele</span><span class="sxs-lookup"><span data-stu-id="34d9a-234">Creating the Host</span></span>  
 <span data-ttu-id="34d9a-235">Hostitelská aplikace komunikuje s doplněk prostřednictvím zobrazení hostitele doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-235">A host application interacts with the add-in through the host view of the add-in.</span></span> <span data-ttu-id="34d9a-236">Používá doplněk zjišťování a aktivaci metody poskytované objektem <xref:System.AddIn.Hosting.AddInStore> a <xref:System.AddIn.Hosting.AddInToken> třídy můžete provádět následující:</span><span class="sxs-lookup"><span data-stu-id="34d9a-236">It uses add-in discovery and activation methods provided by the <xref:System.AddIn.Hosting.AddInStore> and <xref:System.AddIn.Hosting.AddInToken> classes to do the following:</span></span>  
  
-   <span data-ttu-id="34d9a-237">Aktualizace mezipaměti informace o kanálu a doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-237">Update the cache of pipeline and add-in information.</span></span>  
  
-   <span data-ttu-id="34d9a-238">Hledání doplňků typu zobrazení hostitele `ICalculator`, v kořenovém adresáři zadané kanálu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-238">Find add-ins of the host view type, `ICalculator`, under the specified pipeline root directory.</span></span>  
  
-   <span data-ttu-id="34d9a-239">Výzva k zadání která doplněk používat.</span><span class="sxs-lookup"><span data-stu-id="34d9a-239">Prompt the user to specify which add-in to use.</span></span>  
  
-   <span data-ttu-id="34d9a-240">Aktivujte vybrané doplněk v nové doméně aplikace se zadaným zabezpečením úrovně důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="34d9a-240">Activate the selected add-in in a new application domain with a specified security trust level.</span></span>  
  
-   <span data-ttu-id="34d9a-241">Spuštění vlastního `RunCalculator` metodu, která volá metody doplňku podle zobrazení hostitele doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-241">Run the custom `RunCalculator` method, which calls the add-in's methods as specified by the host view of the add-in.</span></span>  
  
#### <a name="to-create-the-host"></a><span data-ttu-id="34d9a-242">Chcete-li vytvořit hostitele</span><span class="sxs-lookup"><span data-stu-id="34d9a-242">To create the host</span></span>  
  
1.  <span data-ttu-id="34d9a-243">Přidat nový projekt s názvem `Calc1Host` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="34d9a-243">Add a new project named `Calc1Host` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="34d9a-244">Založit na **konzolovou aplikaci** šablony.</span><span class="sxs-lookup"><span data-stu-id="34d9a-244">Base it on the **Console Application** template.</span></span>  
  
2.  <span data-ttu-id="34d9a-245">V **Průzkumníka řešení**, přidejte odkaz na sestavení System.AddIn.dll `Calc1Host` projektu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-245">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the `Calc1Host` project.</span></span>  
  
3.  <span data-ttu-id="34d9a-246">Přidat odkaz na projekt `Calc1HVA` projektu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-246">Add a project reference to the `Calc1HVA` project.</span></span> <span data-ttu-id="34d9a-247">Vyberte odkaz na projekt a v **vlastnosti** nastavit **Kopírovat místně** k **False**.</span><span class="sxs-lookup"><span data-stu-id="34d9a-247">Select the project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="34d9a-248">V jazyce Visual Basic použijte **odkazy** kartě **vlastnosti projektu** nastavit **Kopírovat místně** k **False**.</span><span class="sxs-lookup"><span data-stu-id="34d9a-248">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False**.</span></span>  
  
4.  <span data-ttu-id="34d9a-249">Přejmenování souboru třídy (modulu v jazyce Visual Basic) `MathHost1`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-249">Rename the class file (module in Visual Basic) `MathHost1`.</span></span>  
  
5.  <span data-ttu-id="34d9a-250">V jazyce Visual Basic použijte **aplikace** karty **vlastnosti projektu** dialogové okno nastavit **spouštěcí objekt** k **Sub Main**.</span><span class="sxs-lookup"><span data-stu-id="34d9a-250">In Visual Basic, use the **Application** tab of the **Project Properties** dialog box to set **Startup object** to **Sub Main**.</span></span>  
  
6.  <span data-ttu-id="34d9a-251">V souboru třídu nebo modul, přidejte odkaz na obor názvů <xref:System.AddIn.Hosting>.</span><span class="sxs-lookup"><span data-stu-id="34d9a-251">In the class or module file, add a namespace reference to <xref:System.AddIn.Hosting>.</span></span>  
  
7.  <span data-ttu-id="34d9a-252">V souboru třídu nebo modul, přidejte odkaz na obor názvů pro zobrazení hostitele doplňku: `CalcHVAs`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-252">In the class or module file, add a namespace reference for the host view of the add-in: `CalcHVAs`.</span></span> <span data-ttu-id="34d9a-253">(V jazyce Visual Basic, tento odkaz na obor názvů je `Calc1HVA.CalcHVAs`, pokud jste nevypnuli výchozích názvových prostorů v projektech Visual Basic.)</span><span class="sxs-lookup"><span data-stu-id="34d9a-253">(In Visual Basic, this namespace reference is `Calc1HVA.CalcHVAs`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="34d9a-254">V **Průzkumníku řešení**, vyberte řešení a od **projektu** nabídku zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="34d9a-254">In **Solution Explorer**, select the solution and from the **Project** menu choose **Properties**.</span></span> <span data-ttu-id="34d9a-255">V **stránek vlastností řešení** dialogové okno, nastavte **jeden spouštěný projekt** na tomto projektu hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="34d9a-255">In the **Solution Property Pages** dialog box, set the **Single Startup Project** to be this host application project.</span></span>  
  
9. <span data-ttu-id="34d9a-256">V souboru třídu nebo modul, použijte <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> způsob aktualizace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="34d9a-256">In the class or module file, use the <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> method to update the cache.</span></span> <span data-ttu-id="34d9a-257">Použít <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> metodu pro získání kolekce tokeny a použít <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> metoda aktivovat doplněk.</span><span class="sxs-lookup"><span data-stu-id="34d9a-257">Use the <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> method to get a collection of tokens, and use the <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> method to activate an add-in.</span></span>  
  
     <span data-ttu-id="34d9a-258">Následující kód ukazuje dokončené hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="34d9a-258">The following code shows the completed host application.</span></span>  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="34d9a-259">Tento kód předpokládá, že struktura složek kanál se nachází ve složce aplikace.</span><span class="sxs-lookup"><span data-stu-id="34d9a-259">This code assumes that the pipeline folder structure is located in the application folder.</span></span> <span data-ttu-id="34d9a-260">Pokud jste ho jinde, změňte řádek kódu, který nastaví `addInRoot` proměnné, tak, že proměnná obsahuje cestu k strukturu kanálu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-260">If you located it elsewhere, change the line of code that sets the `addInRoot` variable, so that the variable contains the path to your pipeline directory structure.</span></span>  
  
     <span data-ttu-id="34d9a-261">Tento kód použije `ChooseCalculator` metoda seznam tokenů a výzva k výběru doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-261">The code uses a `ChooseCalculator` method to list the tokens and to prompt the user to choose an add-in.</span></span> <span data-ttu-id="34d9a-262">`RunCalculator` Metody vyzve uživatele k jednoduché matematické výrazy, analyzuje výrazů pomocí `Parser` třídy a zobrazí výsledky vracené pomocí doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-262">The `RunCalculator` method prompts the user for simple math expressions, parses the expressions using the `Parser` class, and displays the results returned by the add-in.</span></span>  
  
10. <span data-ttu-id="34d9a-263">Volitelně můžete vytvářejte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34d9a-263">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in"></a><span data-ttu-id="34d9a-264">Vytváření v aplikaci</span><span class="sxs-lookup"><span data-stu-id="34d9a-264">Creating the Add-In</span></span>  
 <span data-ttu-id="34d9a-265">Doplněk implementuje metody určené v zobrazení.</span><span class="sxs-lookup"><span data-stu-id="34d9a-265">An add-in implements the methods specified by the add-in view.</span></span> <span data-ttu-id="34d9a-266">Tento doplněk implementuje `Add`, `Subtract`, `Multiply`, a `Divide` operace a vrací výsledky do hostitele.</span><span class="sxs-lookup"><span data-stu-id="34d9a-266">This add-in implements the `Add`, `Subtract`, `Multiply`, and `Divide` operations and returns the results to the host.</span></span>  
  
#### <a name="to-create-the-add-in"></a><span data-ttu-id="34d9a-267">Chcete-li vytvořit doplněk</span><span class="sxs-lookup"><span data-stu-id="34d9a-267">To create the add-in</span></span>  
  
1.  <span data-ttu-id="34d9a-268">Přidat nový projekt s názvem `AddInCalcV1` k `CalculatorV1` řešení.</span><span class="sxs-lookup"><span data-stu-id="34d9a-268">Add a new project named `AddInCalcV1` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="34d9a-269">Založit na **knihovny tříd** šablony.</span><span class="sxs-lookup"><span data-stu-id="34d9a-269">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="34d9a-270">V **Průzkumníka řešení**, přidejte odkaz na sestavení System.AddIn.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-270">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the project.</span></span>  
  
3.  <span data-ttu-id="34d9a-271">Přidat odkaz na projekt `Calc1AddInView` projektu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-271">Add a project reference to the `Calc1AddInView` project.</span></span> <span data-ttu-id="34d9a-272">Vyberte odkaz na projekt a v **vlastnosti**, nastavte **Kopírovat místně** k **False**.</span><span class="sxs-lookup"><span data-stu-id="34d9a-272">Select the project reference, and in **Properties**, set **Copy Local** to **False**.</span></span> <span data-ttu-id="34d9a-273">V jazyce Visual Basic použijte **odkazy** kartě **vlastnosti projektu** nastavit **Kopírovat místně** k **False** pro odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="34d9a-273">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the project reference.</span></span>  
  
4.  <span data-ttu-id="34d9a-274">Tuto třídu přejmenovat `AddInCalcV1`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-274">Rename the class `AddInCalcV1`.</span></span>  
  
5.  <span data-ttu-id="34d9a-275">V souboru třídy přidejte odkaz na obor názvů <xref:System.AddIn> a segment zobrazení doplňku: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="34d9a-275">In the class file, add a namespace reference to <xref:System.AddIn> and the add-in view segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` in Visual Basic).</span></span>  
  
6.  <span data-ttu-id="34d9a-276">Použít <xref:System.AddIn.AddInAttribute> atribut `AddInCalcV1` třídy k identifikaci třídy jako doplněk.</span><span class="sxs-lookup"><span data-stu-id="34d9a-276">Apply the <xref:System.AddIn.AddInAttribute> attribute to the `AddInCalcV1` class, to identify the class as an add-in.</span></span>  
  
7.  <span data-ttu-id="34d9a-277">Ujistěte se, `AddInCalcV1` třída implementovat rozhraní, které představuje zobrazení doplňku: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="34d9a-277">Make the `AddInCalcV1` class implement the interface that represents the add-in view: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` in Visual Basic).</span></span>  
  
8.  <span data-ttu-id="34d9a-278">Implementovat členy `ICalculator` tak, že vrací výsledky odpovídající výpočtů.</span><span class="sxs-lookup"><span data-stu-id="34d9a-278">Implement the members of `ICalculator` by returning the results of the appropriate calculations.</span></span>  
  
     <span data-ttu-id="34d9a-279">Následující kód ukazuje dokončené doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-279">The following code shows the completed add-in.</span></span>  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. <span data-ttu-id="34d9a-280">Volitelně můžete vytvářejte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34d9a-280">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="deploying-the-pipeline"></a><span data-ttu-id="34d9a-281">Nasazení kanálu</span><span class="sxs-lookup"><span data-stu-id="34d9a-281">Deploying the Pipeline</span></span>  
 <span data-ttu-id="34d9a-282">Nyní jste připraveni k sestavení a nasazení segmenty doplňku do struktury adresářů požadované kanálu.</span><span class="sxs-lookup"><span data-stu-id="34d9a-282">You are now ready to build and deploy the add-in segments to the required pipeline directory structure.</span></span>  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a><span data-ttu-id="34d9a-283">K nasazení segmenty kanálu</span><span class="sxs-lookup"><span data-stu-id="34d9a-283">To deploy the segments to the pipeline</span></span>  
  
1.  <span data-ttu-id="34d9a-284">Pro každý projekt v řešení, použijte **sestavení** kartě **vlastnosti projektu** ( **kompilaci** kartu v jazyce Visual Basic) k nastavení hodnoty **výstupní cesta**  ( **výstupní cesta sestavení** v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="34d9a-284">For each project in the solution, use the **Build** tab of **Project Properties** (the **Compile** tab in Visual Basic) to set the value of the **Output path** (the **Build output path** in Visual Basic).</span></span> <span data-ttu-id="34d9a-285">Pokud název složky aplikace `MyApp`, například by vaše projekty sestavení do následující složky:</span><span class="sxs-lookup"><span data-stu-id="34d9a-285">If you named your application folder `MyApp`, for example, your projects would build into the following folders:</span></span>  
  
    |<span data-ttu-id="34d9a-286">Projekt</span><span class="sxs-lookup"><span data-stu-id="34d9a-286">Project</span></span>|<span data-ttu-id="34d9a-287">Cesta</span><span class="sxs-lookup"><span data-stu-id="34d9a-287">Path</span></span>|  
    |-------------|----------|  
    |<span data-ttu-id="34d9a-288">AddInCalcV1</span><span class="sxs-lookup"><span data-stu-id="34d9a-288">AddInCalcV1</span></span>|<span data-ttu-id="34d9a-289">MyApp\Pipeline\AddIns\CalcV1</span><span class="sxs-lookup"><span data-stu-id="34d9a-289">MyApp\Pipeline\AddIns\CalcV1</span></span>|  
    |<span data-ttu-id="34d9a-290">Calc1AddInSideAdapter</span><span class="sxs-lookup"><span data-stu-id="34d9a-290">Calc1AddInSideAdapter</span></span>|<span data-ttu-id="34d9a-291">MyApp\Pipeline\AddInSideAdapters</span><span class="sxs-lookup"><span data-stu-id="34d9a-291">MyApp\Pipeline\AddInSideAdapters</span></span>|  
    |<span data-ttu-id="34d9a-292">Calc1AddInView</span><span class="sxs-lookup"><span data-stu-id="34d9a-292">Calc1AddInView</span></span>|<span data-ttu-id="34d9a-293">MyApp\Pipeline\AddInViews</span><span class="sxs-lookup"><span data-stu-id="34d9a-293">MyApp\Pipeline\AddInViews</span></span>|  
    |<span data-ttu-id="34d9a-294">Calc1Contract</span><span class="sxs-lookup"><span data-stu-id="34d9a-294">Calc1Contract</span></span>|<span data-ttu-id="34d9a-295">MyApp\Pipeline\Contracts</span><span class="sxs-lookup"><span data-stu-id="34d9a-295">MyApp\Pipeline\Contracts</span></span>|  
    |<span data-ttu-id="34d9a-296">Calc1Host</span><span class="sxs-lookup"><span data-stu-id="34d9a-296">Calc1Host</span></span>|<span data-ttu-id="34d9a-297">Moje aplikace</span><span class="sxs-lookup"><span data-stu-id="34d9a-297">MyApp</span></span>|  
    |<span data-ttu-id="34d9a-298">Calc1HostSideAdapter</span><span class="sxs-lookup"><span data-stu-id="34d9a-298">Calc1HostSideAdapter</span></span>|<span data-ttu-id="34d9a-299">MyApp\Pipeline\HostSideAdapters</span><span class="sxs-lookup"><span data-stu-id="34d9a-299">MyApp\Pipeline\HostSideAdapters</span></span>|  
    |<span data-ttu-id="34d9a-300">Calc1HVA</span><span class="sxs-lookup"><span data-stu-id="34d9a-300">Calc1HVA</span></span>|<span data-ttu-id="34d9a-301">Moje aplikace</span><span class="sxs-lookup"><span data-stu-id="34d9a-301">MyApp</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="34d9a-302">Pokud jste se rozhodli umístit vaše struktura složky kanálu do jiného umístění než složce vaší aplikace, je nutné upravit cesty uvedené v tabulce odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="34d9a-302">If you decided to put your pipeline folder structure in a location other than your application folder, you must modify the paths shown in the table accordingly.</span></span> <span data-ttu-id="34d9a-303">Viz diskuze požadavky adresáře kanálu v [požadavky na vývoj kanálu](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="34d9a-303">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
2.  <span data-ttu-id="34d9a-304">Sestavte řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34d9a-304">Build the Visual Studio solution.</span></span>  
  
3.  <span data-ttu-id="34d9a-305">Zkontrolujte aplikaci a kanál adresáře pro zajištění, že sestavení byly zkopírovány do správného adresáře a, zda byly nainstalovány žádné další kopie sestavení ve složce nesprávné.</span><span class="sxs-lookup"><span data-stu-id="34d9a-305">Check the application and pipeline directories to ensure that the assemblies were copied to the correct directories and that no extra copies of assemblies were installed in the wrong folders.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="34d9a-306">Pokud jste nezměnili **Kopírovat místně** k **False** pro `Calc1AddInView` odkaz v projektu `AddInCalcV1` projektu, zavaděč zamezili problémům zabrání doplněk se nachází.</span><span class="sxs-lookup"><span data-stu-id="34d9a-306">If you did not change **Copy Local** to **False** for the `Calc1AddInView` project reference in the `AddInCalcV1` project, loader context problems will prevent the add-in from being located.</span></span>  
  
     <span data-ttu-id="34d9a-307">Informace o nasazení do tohoto kanálu najdete v tématu [požadavky na vývoj kanálu](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="34d9a-307">For information about deploying to the pipeline, see [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
## <a name="running-the-host-application"></a><span data-ttu-id="34d9a-308">Spuštění aplikace hostitele</span><span class="sxs-lookup"><span data-stu-id="34d9a-308">Running the Host Application</span></span>  
 <span data-ttu-id="34d9a-309">Nyní jste připraveni spustit hostiteli a interakci s doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-309">You are now ready to run the host and interact with the add-in.</span></span>  
  
#### <a name="to-run-the-host-application"></a><span data-ttu-id="34d9a-310">Ke spuštění aplikace hostitele</span><span class="sxs-lookup"><span data-stu-id="34d9a-310">To run the host application</span></span>  
  
1.  <span data-ttu-id="34d9a-311">Na příkazovém řádku přejděte do adresáře aplikace a spuštění aplikace hostitele `Calc1Host.exe`.</span><span class="sxs-lookup"><span data-stu-id="34d9a-311">At the command prompt, go to the application directory and run the host application, `Calc1Host.exe`.</span></span>  
  
2.  <span data-ttu-id="34d9a-312">Hostitel najde všechny dostupné doplňky jeho typu a výzva k výběru doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-312">The host finds all available add-ins of its type and prompts you to select an add-in.</span></span> <span data-ttu-id="34d9a-313">Zadejte **1** pro pouze dostupnému doplňku.</span><span class="sxs-lookup"><span data-stu-id="34d9a-313">Enter **1** for the only available add-in.</span></span>  
  
3.  <span data-ttu-id="34d9a-314">Zadejte rovnice pro kalkulačky, jako například **2 + 2**.</span><span class="sxs-lookup"><span data-stu-id="34d9a-314">Enter an equation for the calculator, such as **2 + 2**.</span></span> <span data-ttu-id="34d9a-315">Musí existovat mezery mezi čísla a operátor.</span><span class="sxs-lookup"><span data-stu-id="34d9a-315">There must be spaces between the numbers and the operator.</span></span>  
  
4.  <span data-ttu-id="34d9a-316">Typ **ukončit** a stiskněte klávesu **Enter** zavřít aplikaci.</span><span class="sxs-lookup"><span data-stu-id="34d9a-316">Type **exit** and press the **Enter** key to close the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d9a-317">Viz také</span><span class="sxs-lookup"><span data-stu-id="34d9a-317">See Also</span></span>  
 [<span data-ttu-id="34d9a-318">Návod: Umožnění zpětné kompatibility při změně vašeho hostitele</span><span class="sxs-lookup"><span data-stu-id="34d9a-318">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [<span data-ttu-id="34d9a-319">Návod: Předávání kolekcí mezi hostiteli a doplňky</span><span class="sxs-lookup"><span data-stu-id="34d9a-319">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [<span data-ttu-id="34d9a-320">Požadavky na vývoj kanálu</span><span class="sxs-lookup"><span data-stu-id="34d9a-320">Pipeline Development Requirements</span></span>](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [<span data-ttu-id="34d9a-321">Kontrakty, zobrazení a adaptéry</span><span class="sxs-lookup"><span data-stu-id="34d9a-321">Contracts, Views, and Adapters</span></span>](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [<span data-ttu-id="34d9a-322">Vývoj kanálu</span><span class="sxs-lookup"><span data-stu-id="34d9a-322">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)
