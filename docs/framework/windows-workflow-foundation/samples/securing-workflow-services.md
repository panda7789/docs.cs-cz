---
title: Zabezpečení služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
ms.openlocfilehash: 5dbd724f3a2f8febfc74719584f4d69cbf75b567
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="securing-workflow-services"></a><span data-ttu-id="7b4fd-102">Zabezpečení služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="7b4fd-102">Securing Workflow Services</span></span>
<span data-ttu-id="7b4fd-103">Ukázka zabezpečené služby pracovního postupu ukazuje následujících postupů:</span><span class="sxs-lookup"><span data-stu-id="7b4fd-103">The Secured Workflow Service sample shows the following procedures:</span></span>  
  
-   <span data-ttu-id="7b4fd-104">Vytváření s použitím služby základní pracovní postup <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-104">Creating a basic workflow service using the <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
-   <span data-ttu-id="7b4fd-105">Pomocí konfigurace Windows Communication Foundation (WCF), abyste definovali zabezpečení koncových bodů pro použití službou pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-105">Using Windows Communication Foundation (WCF) configuration to define secure endpoints for use by the workflow service.</span></span>  
  
-   <span data-ttu-id="7b4fd-106">Deklarace identity uvnitř vlastní zásady pro vytváření a používání <xref:System.ServiceModel.ServiceAuthorizationManager> ověřit deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-106">Creating claims inside a custom policy and using the <xref:System.ServiceModel.ServiceAuthorizationManager> to validate claims.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7b4fd-107">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="7b4fd-107">Demonstrates</span></span>  
 <span data-ttu-id="7b4fd-108">Pomocí zabezpečení WCF pro zabezpečení komunikace mezi klientem a službou pracovního postupu, na základě deklarací autorizace</span><span class="sxs-lookup"><span data-stu-id="7b4fd-108">Using WCF security to secure communication between client and Workflow service, Claims based authorization</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="7b4fd-109">Diskusní</span><span class="sxs-lookup"><span data-stu-id="7b4fd-109">Discussion</span></span>  
 <span data-ttu-id="7b4fd-110">Tento příklad znázorňuje použití Infrastruktura zabezpečení WCF pro zabezpečení služby pracovního postupu, stejně jako normální službou WCF.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-110">This sample demonstrates the use of WCF security infrastructure to secure a workflow service just like you would with a normal WCF service.</span></span> <span data-ttu-id="7b4fd-111">Konkrétně používá vlastních deklarací identity pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-111">Specifically, it uses a custom claim for authorization.</span></span> <span data-ttu-id="7b4fd-112">V takovém případě se použije <xref:System.ServiceModel.WSHttpBinding> a zpráv režim zabezpečení pomocí pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-112">In this case, it uses <xref:System.ServiceModel.WSHttpBinding> and message mode security with Windows credentials.</span></span>  
  
 <span data-ttu-id="7b4fd-113">Vlastní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) ověří uživatelské jméno systému Windows klienta a pro konkrétní znak.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-113">The custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) checks the client's Windows username and for a specific character.</span></span> <span data-ttu-id="7b4fd-114">Pokud se nachází tento znak, vytvoří a přidá se <xref:System.IdentityModel.Policy.EvaluationContext>.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-114">If that character is present, it creates and adds the claim to the <xref:System.IdentityModel.Policy.EvaluationContext>.</span></span> <span data-ttu-id="7b4fd-115">Díky tomu vlastní zásady je provedení příkazu, klient má tento znak v uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-115">By doing this, the custom policy is making the statement that the client has this character in the username.</span></span> <span data-ttu-id="7b4fd-116">Tento požadavek můžete položit dotaz na po celou dobu volání.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-116">This claim can be queried throughout the lifetime of the call.</span></span> <span data-ttu-id="7b4fd-117">Můžete najít tento znak v `Constants.cs`.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-117">You can find that character in `Constants.cs`.</span></span>  
  
 <span data-ttu-id="7b4fd-118">Zásady autorizace hledá deklarace identity uvnitř `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-118">The authorization policy looks for the claim inside the `SecureWorkFlowAuthZManager`.</span></span> <span data-ttu-id="7b4fd-119">Pokud najde ho, vrátí `true` a povolit v pracovním postupu pokračovat.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-119">If it finds it, it returns `true` and allow the workflow to proceed.</span></span> <span data-ttu-id="7b4fd-120">Funkce `false`, což způsobí, že zpráva o odepření přístupu má být vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-120">Otherwise, it returns `false`, which causes an 'Access Denied' message to be returned to the client.</span></span> <span data-ttu-id="7b4fd-121">Další deklarace identity jsou k dispozici v kontextu a může být prověřen také uvnitř `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-121">Other claims are present in the context and can be examined as well inside the `SecureWorkFlowAuthZManager`.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="7b4fd-122">Chcete tuto ukázku spustit</span><span class="sxs-lookup"><span data-stu-id="7b4fd-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="7b4fd-123">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-123">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="7b4fd-124">Načíst SecuringWorkflowServices.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b4fd-124">Load SecuringWorkflowServices.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="7b4fd-125">Stisknutím kombinace kláves CTRL + SHIFT + B řešení zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-125">Press CTRL+SHIFT+B to compile the solution.</span></span>  
  
4.  <span data-ttu-id="7b4fd-126">Nastavte projekt služby jako spuštění projektu pro řešení.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-126">Set the Service project as the start-up project for the solution.</span></span>  
  
5.  <span data-ttu-id="7b4fd-127">Stisknutím CTRL + F5 a spusťte službu bez ladění.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-127">Press CTRL+F5 to start the service without debugging.</span></span>  
  
6.  <span data-ttu-id="7b4fd-128">Nastavte klientského projektu jako spuštění projektu pro řešení.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-128">Set the Client project as the start-up project for the solution.</span></span>  
  
7.  <span data-ttu-id="7b4fd-129">Stisknutím CTRL + F5 a spusťte službu klienta bez ladění.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-129">Press CTRL+F5 to start the client without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b4fd-130">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b4fd-131">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="7b4fd-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7b4fd-132">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b4fd-133">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7b4fd-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
