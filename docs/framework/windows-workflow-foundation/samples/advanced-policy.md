---
title: "Rozšířené zásady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c83f4167ce1947b10f97e0cab5b5ddd2f8e00c76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-policy"></a><span data-ttu-id="640f5-102">Rozšířené zásady</span><span class="sxs-lookup"><span data-stu-id="640f5-102">Advanced Policy</span></span>
<span data-ttu-id="640f5-103">Tato ukázka rozšiřuje ukázka jednoduché zásady.</span><span class="sxs-lookup"><span data-stu-id="640f5-103">This sample extends the Simple Policy sample.</span></span> <span data-ttu-id="640f5-104">Kromě domácí slevu a obchodní pravidla slevu z příkladu jednoduché zásady bylo přidáno několik nové pravidel.</span><span class="sxs-lookup"><span data-stu-id="640f5-104">In addition to the residential discount and business discount rules from the Simple Policy example, several new rules have been added.</span></span>  
  
 <span data-ttu-id="640f5-105">Je přidáno pravidlo vysoké hodnoty, který nabízí větší slevu objednávky vysoké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="640f5-105">A high-value rule is added, which provides a bigger discount for high-value orders.</span></span> <span data-ttu-id="640f5-106">Hodnota priority je vydáno menší než předchozí dvě pravidla tak, aby se přepsat pole slevu a zásada přednost přes obě domácí a obchodní pravidla slevu.</span><span class="sxs-lookup"><span data-stu-id="640f5-106">It is given a priority value less than the previous two rules so that it will overwrite the discount field and take precedence over both the residential and business discount rules.</span></span>  
  
 <span data-ttu-id="640f5-107">Celkový počet pravidlo calculate je taky přidaná, která vypočítá celkové založená na úrovni slevy.</span><span class="sxs-lookup"><span data-stu-id="640f5-107">A calculate total rule is also added, which computes the total based on the discount level.</span></span> <span data-ttu-id="640f5-108">Zobrazuje, jak odkazovat na aktivitu pracovního postupu je definován metodu, jakož i způsob použití jiného akce.</span><span class="sxs-lookup"><span data-stu-id="640f5-108">It shows how to reference a method defined on the workflow activity, as well as how to use else actions.</span></span> <span data-ttu-id="640f5-109">Toto pravidlo také ukazuje, řetězení chování vzhledem k tomu, že bude vyhodnocen kdykoli změny pole slevy.</span><span class="sxs-lookup"><span data-stu-id="640f5-109">This rule also demonstrates chaining behavior since it will be evaluated anytime the discount field changes.</span></span> <span data-ttu-id="640f5-110">Kromě toho metoda zapisujících se zobrazí s RuleWriteAttribute na metodě CalculateTotal.</span><span class="sxs-lookup"><span data-stu-id="640f5-110">Furthermore, method attributing is shown with the RuleWriteAttribute on the CalculateTotal method.</span></span> <span data-ttu-id="640f5-111">To způsobí, že dopad pravidla (ErrorTotalRule), který se má znovu vyhodnotit vždy, když se provede metodu.</span><span class="sxs-lookup"><span data-stu-id="640f5-111">This causes impacted rules (ErrorTotalRule) to be re-evaluated whenever the method gets executed.</span></span>  
  
 <span data-ttu-id="640f5-112">Poslední přidat pravidlo je ten, který zjistí chyby (v tomto případě celkem menší než 0).</span><span class="sxs-lookup"><span data-stu-id="640f5-112">The last rule added is one that detects errors (in this case, Total less than 0).</span></span> <span data-ttu-id="640f5-113">Pokud k tomu dojde, je zastavit zpracování zásad.</span><span class="sxs-lookup"><span data-stu-id="640f5-113">If this occurs, the policy execution is halted.</span></span>  
  
 <span data-ttu-id="640f5-114">Nakonec `Console.Writeline` volání jsou přidány jako akce pro každé pravidlo zajistit další přehled spuštění pravidla, a současně zobrazit, že je možné odkazovat k přístupu ke statické metody na typy.</span><span class="sxs-lookup"><span data-stu-id="640f5-114">Finally, `Console.Writeline` calls are added as actions to each rule to provide more visibility into rule execution, while also showing that it is possible to access static methods on referenced types.</span></span> <span data-ttu-id="640f5-115">Můžete také použít sledování získáte tak přehled do pravidla, které jsou spouštěny.</span><span class="sxs-lookup"><span data-stu-id="640f5-115">You could also use tracking to get visibility into the rules that are executed.</span></span>  
  
 <span data-ttu-id="640f5-116">Pravidla používaná v této ukázce jsou:</span><span class="sxs-lookup"><span data-stu-id="640f5-116">The rules used in this sample are:</span></span>  
  
 <span data-ttu-id="640f5-117">**ResidentialDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="640f5-117">**ResidentialDiscountRule:**</span></span>  
  
 <span data-ttu-id="640f5-118">Pokud OrderValue > 500 a CustomerType = domácí</span><span class="sxs-lookup"><span data-stu-id="640f5-118">IF OrderValue > 500 AND CustomerType = Residential</span></span>  
  
 <span data-ttu-id="640f5-119">PAK slevu = 5 %</span><span class="sxs-lookup"><span data-stu-id="640f5-119">THEN Discount = 5%</span></span>  
  
 <span data-ttu-id="640f5-120">**BusinessDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="640f5-120">**BusinessDiscountRule:**</span></span>  
  
 <span data-ttu-id="640f5-121">Pokud OrderValue > 10000 a CustomerType = firmy</span><span class="sxs-lookup"><span data-stu-id="640f5-121">IF OrderValue > 10000 AND CustomerType = Business</span></span>  
  
 <span data-ttu-id="640f5-122">PAK slevu = 10 %</span><span class="sxs-lookup"><span data-stu-id="640f5-122">THEN Discount = 10%</span></span>  
  
 <span data-ttu-id="640f5-123">**HighValueDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="640f5-123">**HighValueDiscountRule:**</span></span>  
  
 <span data-ttu-id="640f5-124">Pokud OrderValue > 20000</span><span class="sxs-lookup"><span data-stu-id="640f5-124">IF OrderValue > 20000</span></span>  
  
 <span data-ttu-id="640f5-125">PAK slevu = 15 %</span><span class="sxs-lookup"><span data-stu-id="640f5-125">THEN Discount = 15%</span></span>  
  
 <span data-ttu-id="640f5-126">**TotalRule:**</span><span class="sxs-lookup"><span data-stu-id="640f5-126">**TotalRule:**</span></span>  
  
 <span data-ttu-id="640f5-127">Pokud slevách > 0</span><span class="sxs-lookup"><span data-stu-id="640f5-127">IF Discount > 0</span></span>  
  
 <span data-ttu-id="640f5-128">PAK CalculateTotal (OrderValue, slevy)</span><span class="sxs-lookup"><span data-stu-id="640f5-128">THEN CalculateTotal(OrderValue, Discount)</span></span>  
  
 <span data-ttu-id="640f5-129">ELSE celkem = OrderValue</span><span class="sxs-lookup"><span data-stu-id="640f5-129">ELSE Total = OrderValue</span></span>  
  
 <span data-ttu-id="640f5-130">**ErrorTotalRule:**</span><span class="sxs-lookup"><span data-stu-id="640f5-130">**ErrorTotalRule:**</span></span>  
  
 <span data-ttu-id="640f5-131">Pokud celkový počet \< 0</span><span class="sxs-lookup"><span data-stu-id="640f5-131">IF Total \< 0</span></span>  
  
 <span data-ttu-id="640f5-132">POTOM chyba = "Aktivováno ErrorTotalRule"; Zastavení</span><span class="sxs-lookup"><span data-stu-id="640f5-132">THEN Error = "Fired ErrorTotalRule"; Halt</span></span>  
  
 <span data-ttu-id="640f5-133">Vyhodnocení pravidla a provádění můžete zobrazit také prostřednictvím trasování a sledování.</span><span class="sxs-lookup"><span data-stu-id="640f5-133">Rule evaluation and execution can also be seen through tracing and tracking.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="640f5-134">Chcete-li sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="640f5-134">To build the sample</span></span>  
  
1.  <span data-ttu-id="640f5-135">Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="640f5-135">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="640f5-136">Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="640f5-136">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="640f5-137">Spustíte řešení bez ladění stisknutím kombinace kláves CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="640f5-137">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="640f5-138">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="640f5-138">To run the sample</span></span>  
  
-   <span data-ttu-id="640f5-139">V okně příkazového řádku sady SDK spusťte soubor .exe ve složce AdvancedPolicy\bin\debug (nebo složky \bin AdvancedPolicy pro verzi ukázky jazyka Visual Basic), který se nachází pod hlavní složku pro ukázku.</span><span class="sxs-lookup"><span data-stu-id="640f5-139">In the SDK Command Prompt window, run the .exe file in the AdvancedPolicy\bin\debug folder (or the AdvancedPolicy \bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="640f5-140">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="640f5-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="640f5-141">Před pokračováním zkontrolovat na následující adresář (výchozí):</span><span class="sxs-lookup"><span data-stu-id="640f5-141">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="640f5-142">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="640f5-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="640f5-143">Tato ukázka se nachází v následujícím adresáři:</span><span class="sxs-lookup"><span data-stu-id="640f5-143">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a><span data-ttu-id="640f5-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="640f5-144">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="640f5-145">Jednoduché zásady</span><span class="sxs-lookup"><span data-stu-id="640f5-145">Simple Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
