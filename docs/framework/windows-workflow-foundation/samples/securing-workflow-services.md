---
title: Zabezpečení služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
ms.openlocfilehash: 28c34ecf7d6d781bfa461b2737cb9325a657f47e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524332"
---
# <a name="securing-workflow-services"></a><span data-ttu-id="4defd-102">Zabezpečení služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="4defd-102">Securing Workflow Services</span></span>
<span data-ttu-id="4defd-103">V ukázce Zabezpečená služba pracovního postupu najdete v následujících postupech:</span><span class="sxs-lookup"><span data-stu-id="4defd-103">The Secured Workflow Service sample shows the following procedures:</span></span>  
  
-   <span data-ttu-id="4defd-104">Vytváření s použitím služby základní pracovní postup <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity.</span><span class="sxs-lookup"><span data-stu-id="4defd-104">Creating a basic workflow service using the <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
-   <span data-ttu-id="4defd-105">Chcete-li definovat zabezpečené koncové body pro použití službou pracovního postupu pomocí konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4defd-105">Using Windows Communication Foundation (WCF) configuration to define secure endpoints for use by the workflow service.</span></span>  
  
-   <span data-ttu-id="4defd-106">Deklarace identity uvnitř vlastní zásady pro vytváření a používání <xref:System.ServiceModel.ServiceAuthorizationManager> k ověřování deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="4defd-106">Creating claims inside a custom policy and using the <xref:System.ServiceModel.ServiceAuthorizationManager> to validate claims.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4defd-107">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="4defd-107">Demonstrates</span></span>  
 <span data-ttu-id="4defd-108">Pomocí zabezpečení WCF pro zabezpečení komunikace mezi klientem a služby pracovních postupů, autorizace deklarovaných identit</span><span class="sxs-lookup"><span data-stu-id="4defd-108">Using WCF security to secure communication between client and Workflow service, Claims based authorization</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4defd-109">Diskuse</span><span class="sxs-lookup"><span data-stu-id="4defd-109">Discussion</span></span>  
 <span data-ttu-id="4defd-110">Tento příklad znázorňuje používání infrastruktury zabezpečení WCF pro zabezpečení služby pracovního postupu, stejně jako normální službou WCF.</span><span class="sxs-lookup"><span data-stu-id="4defd-110">This sample demonstrates the use of WCF security infrastructure to secure a workflow service just like you would with a normal WCF service.</span></span> <span data-ttu-id="4defd-111">Konkrétně používá vlastní deklarace identity pro autorizaci.</span><span class="sxs-lookup"><span data-stu-id="4defd-111">Specifically, it uses a custom claim for authorization.</span></span> <span data-ttu-id="4defd-112">V tomto případě používá <xref:System.ServiceModel.WSHttpBinding> a zprávu režim zabezpečení pomocí přihlašovacích údajů Windows.</span><span class="sxs-lookup"><span data-stu-id="4defd-112">In this case, it uses <xref:System.ServiceModel.WSHttpBinding> and message mode security with Windows credentials.</span></span>  
  
 <span data-ttu-id="4defd-113">Vlastní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) ověří uživatelské jméno klienta Windows a pro konkrétní znak.</span><span class="sxs-lookup"><span data-stu-id="4defd-113">The custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) checks the client's Windows username and for a specific character.</span></span> <span data-ttu-id="4defd-114">Pokud tento znak je k dispozici, vytvoří a přidá deklaraci do <xref:System.IdentityModel.Policy.EvaluationContext>.</span><span class="sxs-lookup"><span data-stu-id="4defd-114">If that character is present, it creates and adds the claim to the <xref:System.IdentityModel.Policy.EvaluationContext>.</span></span> <span data-ttu-id="4defd-115">Tímto způsobem, vlastní zásady provádí příkaz, který má klient tento znak uživatelské jméno.</span><span class="sxs-lookup"><span data-stu-id="4defd-115">By doing this, the custom policy is making the statement that the client has this character in the username.</span></span> <span data-ttu-id="4defd-116">Tato deklarace identity může být dotazována v celém životním volání.</span><span class="sxs-lookup"><span data-stu-id="4defd-116">This claim can be queried throughout the lifetime of the call.</span></span> <span data-ttu-id="4defd-117">Můžete najít znaku v `Constants.cs`.</span><span class="sxs-lookup"><span data-stu-id="4defd-117">You can find that character in `Constants.cs`.</span></span>  
  
 <span data-ttu-id="4defd-118">Zásady autorizace hledá deklarace identity uvnitř `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="4defd-118">The authorization policy looks for the claim inside the `SecureWorkFlowAuthZManager`.</span></span> <span data-ttu-id="4defd-119">Pokud se ho najde, vrátí `true` a povolit pracovní postup, aby bylo možné pokračovat.</span><span class="sxs-lookup"><span data-stu-id="4defd-119">If it finds it, it returns `true` and allow the workflow to proceed.</span></span> <span data-ttu-id="4defd-120">V opačném případě vrátí `false`, což způsobí, že zprávu "Přístup byl odepřen" má být vrácena klientovi.</span><span class="sxs-lookup"><span data-stu-id="4defd-120">Otherwise, it returns `false`, which causes an 'Access Denied' message to be returned to the client.</span></span> <span data-ttu-id="4defd-121">Další deklarace identity jsou k dispozici v kontextu a lze jej prozkoumat také uvnitř `SecureWorkFlowAuthZManager`.</span><span class="sxs-lookup"><span data-stu-id="4defd-121">Other claims are present in the context and can be examined as well inside the `SecureWorkFlowAuthZManager`.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="4defd-122">Tuto ukázku spustit</span><span class="sxs-lookup"><span data-stu-id="4defd-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="4defd-123">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="4defd-123">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="4defd-124">Načíst SecuringWorkflowServices.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4defd-124">Load SecuringWorkflowServices.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="4defd-125">Stiskněte kombinaci kláves CTRL + SHIFT + B pro kompilaci řešení.</span><span class="sxs-lookup"><span data-stu-id="4defd-125">Press CTRL+SHIFT+B to compile the solution.</span></span>  
  
4.  <span data-ttu-id="4defd-126">Nastavte jako spouštěcí projekt pro řešení projekt služby.</span><span class="sxs-lookup"><span data-stu-id="4defd-126">Set the Service project as the start-up project for the solution.</span></span>  
  
5.  <span data-ttu-id="4defd-127">Stisknutím kláves CTRL + F5 ke spuštění služby bez ladění.</span><span class="sxs-lookup"><span data-stu-id="4defd-127">Press CTRL+F5 to start the service without debugging.</span></span>  
  
6.  <span data-ttu-id="4defd-128">Nastavte klientský projekt jako projekt spuštění pro řešení.</span><span class="sxs-lookup"><span data-stu-id="4defd-128">Set the Client project as the start-up project for the solution.</span></span>  
  
7.  <span data-ttu-id="4defd-129">Stisknutím kláves CTRL + F5 spusťte klienta bez ladění.</span><span class="sxs-lookup"><span data-stu-id="4defd-129">Press CTRL+F5 to start the client without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4defd-130">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="4defd-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4defd-131">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4defd-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4defd-132">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4defd-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4defd-133">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4defd-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
