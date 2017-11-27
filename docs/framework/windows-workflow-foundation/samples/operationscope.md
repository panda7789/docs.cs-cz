---
title: OperationScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d1e2738e8cdb546a1dcbb00689e5b4c360ddd04
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="operationscope"></a><span data-ttu-id="06527-102">OperationScope</span><span class="sxs-lookup"><span data-stu-id="06527-102">OperationScope</span></span>
<span data-ttu-id="06527-103">Tento příklad ukazuje, jak aktivity, zasílání zpráv <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> můžete použít k vystavení existující vlastní aktivity jako operaci v služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="06527-103">This sample demonstrates how the messaging activities, <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> can be used to expose an existing custom activity as an operation in a workflow service.</span></span> <span data-ttu-id="06527-104">Tato ukázka obsahuje novou vlastní aktivitu volána `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="06527-104">This sample includes a new custom activity called an `OperationScope`.</span></span> <span data-ttu-id="06527-105">Je určena k usnadnění vývoje služby pracovního postupu tak, že umožníte uživatelům vytvářet text činnosti samostatně jako vlastní aktivity a pak je snadno vystavení jako operací služby pomocí `OperationScope` aktivity.</span><span class="sxs-lookup"><span data-stu-id="06527-105">It is intended to ease the development of a workflow service by allowing users to author the body of their operations separately as custom activities and then easily exposing them as service operations using the `OperationScope` activity.</span></span> <span data-ttu-id="06527-106">Například vlastní `Add` aktivity, která přebírá dva `in` argumentů a vrátí jeden `out` může dojít k vystavení argument jako `Add` provozní stav služby pracovního postupu umístěním do `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="06527-106">For example, a custom `Add` activity that takes two `in` arguments and returns one `out` argument could be exposed as an `Add` operation on the workflow service by dropping it into an `OperationScope`.</span></span>  
  
 <span data-ttu-id="06527-107">Obor funguje tak, že zkontrolujete aktivity zadaný jako její text.</span><span class="sxs-lookup"><span data-stu-id="06527-107">The scope works by inspecting the activity provided as its body.</span></span> <span data-ttu-id="06527-108">Žádné nevázaných `in` argumenty se předpokládá, že vstupy z příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="06527-108">Any unbound `in` arguments are assumed to be inputs from the incoming message.</span></span> <span data-ttu-id="06527-109">Všechny `out` argumenty, bez ohledu na to, jestli je vázána, se předpokládá, že výstupy v následných odpovědi.</span><span class="sxs-lookup"><span data-stu-id="06527-109">All `out` arguments, regardless of whether they are bound, are assumed to be outputs in the subsequent reply message.</span></span> <span data-ttu-id="06527-110">Název zveřejněné operace jsou převzaty z zobrazovaný název `OperationScope` aktivity.</span><span class="sxs-lookup"><span data-stu-id="06527-110">The exposed operation’s name is taken from the display name of the `OperationScope` activity.</span></span> <span data-ttu-id="06527-111">Konečným výsledkem je, že aktivita textu je uzavřen do <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> s parametry ze zprávy vázána na argumenty aktivity.</span><span class="sxs-lookup"><span data-stu-id="06527-111">The end result is that the body activity is wrapped in a <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> with the parameters from the messages bound to the arguments of the activity.</span></span>  
  
 <span data-ttu-id="06527-112">Tato ukázka zpřístupní služby pracovního postupu pomocí koncových bodů protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="06527-112">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="06527-113">Pokud chcete spustit, je nutné přidat seznamy ACL správnou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="06527-113">To run, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="06527-114">[Konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="06527-114"> [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="06527-115">Provádění řádku se zvýšenými oprávněními následující příkaz přidá příslušné seznamy ACL (zajistit, aby uživatelské jméno a doména jsou nahrazována pro domény %\\% UserName %).</span><span class="sxs-lookup"><span data-stu-id="06527-115">Executing the following command at an elevated prompt adds the appropriate ACLs (ensure that your Domain and Username are substituted for %DOMAIN%\\%UserName%).</span></span>  
  
 <span data-ttu-id="06527-116">**netsh http přidejte adresu url urlacl = http: / / +: 8000 / uživatele domény % =\\% UserName %**</span><span class="sxs-lookup"><span data-stu-id="06527-116">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="06527-117">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="06527-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="06527-118">Otevřete řešení OperationScope.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06527-118">Open the OperationScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="06527-119">V Průzkumníku řešení kliknete pravým tlačítkem a výběrem nastavit více projektů spuštění **nastavit projekty po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="06527-119">Set multiple start-up projects by right-clicking the solution in Solution Explorer and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="06527-120">Přidejte jako více projektů spuštění scénář a Scenario_Client (v tomto pořadí).</span><span class="sxs-lookup"><span data-stu-id="06527-120">Add Scenario and Scenario_Client (in that order) as multiple start-up projects.</span></span>  
  
3.  <span data-ttu-id="06527-121">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="06527-121">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="06527-122">Tento krok je nutný k zobrazení z důvodu vlastní aktivity pracovního postupu BankService.xaml `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="06527-122">This step is required to view the BankService.xaml workflow due to the custom activity `OperationScope`.</span></span>  
  
4.  <span data-ttu-id="06527-123">Stisknutím kombinace kláves CTRL + F5 a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="06527-123">Press CTRL+F5 to run the application.</span></span> <span data-ttu-id="06527-124">Konzole Scenario_Client vás vyzve k zadání vstupy a odpovídající výstup je vidět v konzole pro scénář.</span><span class="sxs-lookup"><span data-stu-id="06527-124">The Scenario_Client console prompts you for inputs and the corresponding output is seen in the Scenario console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06527-125">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="06527-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="06527-126">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="06527-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06527-127">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="06527-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06527-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="06527-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`  
  
## <a name="see-also"></a><span data-ttu-id="06527-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="06527-129">See Also</span></span>
