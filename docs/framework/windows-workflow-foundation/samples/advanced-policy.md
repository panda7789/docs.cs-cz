---
title: Pokročilé zásady
ms.date: 03/30/2017
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
ms.openlocfilehash: becdc28affd877239474d6f0f007a480297bccb8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083787"
---
# <a name="advanced-policy"></a><span data-ttu-id="f93d6-102">Pokročilé zásady</span><span class="sxs-lookup"><span data-stu-id="f93d6-102">Advanced Policy</span></span>
<span data-ttu-id="f93d6-103">Tento příklad rozšiřuje ukázka jednoduché zásady.</span><span class="sxs-lookup"><span data-stu-id="f93d6-103">This sample extends the Simple Policy sample.</span></span> <span data-ttu-id="f93d6-104">Kromě bydliště slevy a obchodní pravidla slevu z příkladu jednoduché zásady bylo přidáno několik nových pravidel.</span><span class="sxs-lookup"><span data-stu-id="f93d6-104">In addition to the residential discount and business discount rules from the Simple Policy example, several new rules have been added.</span></span>  
  
 <span data-ttu-id="f93d6-105">Je přidáno pravidlo vysoké hodnoty, která poskytuje větší slevy pro objednávky vysoké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f93d6-105">A high-value rule is added, which provides a bigger discount for high-value orders.</span></span> <span data-ttu-id="f93d6-106">Se klíči přiřadí hodnotu priority menší než předchozí dvě pravidla tak, aby se přepsat pole Sleva a přednost nad obou bydliště a obchodní pravidla slevy.</span><span class="sxs-lookup"><span data-stu-id="f93d6-106">It is given a priority value less than the previous two rules so that it will overwrite the discount field and take precedence over both the residential and business discount rules.</span></span>  
  
 <span data-ttu-id="f93d6-107">Vypočítat celkový pravidlo se také přidá, která vypočítá celkový počet vychází z úrovně slev.</span><span class="sxs-lookup"><span data-stu-id="f93d6-107">A calculate total rule is also added, which computes the total based on the discount level.</span></span> <span data-ttu-id="f93d6-108">Ukazuje, jak odkazovat na metody definované v aktivity pracovního postupu, jakož i jak používat ostatní akce.</span><span class="sxs-lookup"><span data-stu-id="f93d6-108">It shows how to reference a method defined on the workflow activity, as well as how to use else actions.</span></span> <span data-ttu-id="f93d6-109">Toto pravidlo také ukazuje řetězení chování, protože je vyhodnocen kdykoli změny pole slevy.</span><span class="sxs-lookup"><span data-stu-id="f93d6-109">This rule also demonstrates chaining behavior since it will be evaluated anytime the discount field changes.</span></span> <span data-ttu-id="f93d6-110">Kromě toho metoda přidělování se zobrazí s RuleWriteAttribute CalculateTotal metody.</span><span class="sxs-lookup"><span data-stu-id="f93d6-110">Furthermore, method attributing is shown with the RuleWriteAttribute on the CalculateTotal method.</span></span> <span data-ttu-id="f93d6-111">To způsobí, že ovlivněné pravidla (ErrorTotalRule), který se má vyhodnotit znovu pokaždé, když se provede metodu.</span><span class="sxs-lookup"><span data-stu-id="f93d6-111">This causes impacted rules (ErrorTotalRule) to be re-evaluated whenever the method gets executed.</span></span>  
  
 <span data-ttu-id="f93d6-112">Poslední pravidlo přidali je ten, který zjistí chyby (v tomto případě celkem menší než 0.).</span><span class="sxs-lookup"><span data-stu-id="f93d6-112">The last rule added is one that detects errors (in this case, Total less than 0).</span></span> <span data-ttu-id="f93d6-113">V tomto případě zastavení spuštění zásad.</span><span class="sxs-lookup"><span data-stu-id="f93d6-113">If this occurs, the policy execution is halted.</span></span>  
  
 <span data-ttu-id="f93d6-114">Nakonec `Console.Writeline` volání jsou přidány jako akce pro každé pravidlo, které poskytují větší přehled o tom spuštění pravidel, a současně zobrazit, že je možné pro přístup ke statické metody na odkazované typy.</span><span class="sxs-lookup"><span data-stu-id="f93d6-114">Finally, `Console.Writeline` calls are added as actions to each rule to provide more visibility into rule execution, while also showing that it is possible to access static methods on referenced types.</span></span> <span data-ttu-id="f93d6-115">Můžete také použít sledování, získat přehled o pravidla, které jsou spouštěny.</span><span class="sxs-lookup"><span data-stu-id="f93d6-115">You could also use tracking to get visibility into the rules that are executed.</span></span>  
  
 <span data-ttu-id="f93d6-116">Pravidla používaná v této ukázce jsou:</span><span class="sxs-lookup"><span data-stu-id="f93d6-116">The rules used in this sample are:</span></span>  
  
 <span data-ttu-id="f93d6-117">**ResidentialDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="f93d6-117">**ResidentialDiscountRule:**</span></span>  
  
 <span data-ttu-id="f93d6-118">Pokud OrderValue > 500 a CustomerType = bydliště</span><span class="sxs-lookup"><span data-stu-id="f93d6-118">IF OrderValue > 500 AND CustomerType = Residential</span></span>  
  
 <span data-ttu-id="f93d6-119">PAK slevy = 5 %</span><span class="sxs-lookup"><span data-stu-id="f93d6-119">THEN Discount = 5%</span></span>  
  
 <span data-ttu-id="f93d6-120">**BusinessDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="f93d6-120">**BusinessDiscountRule:**</span></span>  
  
 <span data-ttu-id="f93d6-121">Pokud OrderValue > 10000 a CustomerType = firmy</span><span class="sxs-lookup"><span data-stu-id="f93d6-121">IF OrderValue > 10000 AND CustomerType = Business</span></span>  
  
 <span data-ttu-id="f93d6-122">PAK slevy = 10 %</span><span class="sxs-lookup"><span data-stu-id="f93d6-122">THEN Discount = 10%</span></span>  
  
 <span data-ttu-id="f93d6-123">**HighValueDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="f93d6-123">**HighValueDiscountRule:**</span></span>  
  
 <span data-ttu-id="f93d6-124">Pokud OrderValue > 20000</span><span class="sxs-lookup"><span data-stu-id="f93d6-124">IF OrderValue > 20000</span></span>  
  
 <span data-ttu-id="f93d6-125">PAK slevy = 15 %</span><span class="sxs-lookup"><span data-stu-id="f93d6-125">THEN Discount = 15%</span></span>  
  
 <span data-ttu-id="f93d6-126">**TotalRule:**</span><span class="sxs-lookup"><span data-stu-id="f93d6-126">**TotalRule:**</span></span>  
  
 <span data-ttu-id="f93d6-127">Pokud slevy > 0</span><span class="sxs-lookup"><span data-stu-id="f93d6-127">IF Discount > 0</span></span>  
  
 <span data-ttu-id="f93d6-128">PAK CalculateTotal (OrderValue slevy)</span><span class="sxs-lookup"><span data-stu-id="f93d6-128">THEN CalculateTotal(OrderValue, Discount)</span></span>  
  
 <span data-ttu-id="f93d6-129">JINÉHO celkové = OrderValue</span><span class="sxs-lookup"><span data-stu-id="f93d6-129">ELSE Total = OrderValue</span></span>  
  
 <span data-ttu-id="f93d6-130">**ErrorTotalRule:**</span><span class="sxs-lookup"><span data-stu-id="f93d6-130">**ErrorTotalRule:**</span></span>  
  
 <span data-ttu-id="f93d6-131">Pokud celkový počet \< 0</span><span class="sxs-lookup"><span data-stu-id="f93d6-131">IF Total \< 0</span></span>  
  
 <span data-ttu-id="f93d6-132">PAK chyba = "Aktivuje ErrorTotalRule"; Zastavení</span><span class="sxs-lookup"><span data-stu-id="f93d6-132">THEN Error = "Fired ErrorTotalRule"; Halt</span></span>  
  
 <span data-ttu-id="f93d6-133">Vyhodnocení pravidla a spuštění je možné také prohlížet pomocí sledování a trasování.</span><span class="sxs-lookup"><span data-stu-id="f93d6-133">Rule evaluation and execution can also be seen through tracing and tracking.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="f93d6-134">K vytvoření vzorku</span><span class="sxs-lookup"><span data-stu-id="f93d6-134">To build the sample</span></span>  
  
1.  <span data-ttu-id="f93d6-135">Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f93d6-135">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="f93d6-136">Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f93d6-136">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f93d6-137">Spuštění řešení bez ladění stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f93d6-137">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="f93d6-138">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="f93d6-138">To run the sample</span></span>  
  
-   <span data-ttu-id="f93d6-139">V okně příkazového řádku sady SDK spusťte soubor .exe ve složce AdvancedPolicy\bin\debug (nebo složky \bin AdvancedPolicy pro verzi ukázky, která se týká jazyka Visual Basic), který se nachází pod hlavní složku pro vzorku.</span><span class="sxs-lookup"><span data-stu-id="f93d6-139">In the SDK Command Prompt window, run the .exe file in the AdvancedPolicy\bin\debug folder (or the AdvancedPolicy \bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f93d6-140">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="f93d6-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f93d6-141">Před pokračováním zkontrolujte následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="f93d6-141">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f93d6-142">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f93d6-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f93d6-143">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="f93d6-143">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a><span data-ttu-id="f93d6-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="f93d6-144">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="f93d6-145">Jednoduché zásady</span><span class="sxs-lookup"><span data-stu-id="f93d6-145">Simple Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
