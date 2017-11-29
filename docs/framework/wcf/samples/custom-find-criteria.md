---
title: "Vlastní kritérium hledání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d49661ff91477f2f53d180a10ae1c9b3b632461f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-find-criteria"></a><span data-ttu-id="4a56c-102">Vlastní kritérium hledání</span><span class="sxs-lookup"><span data-stu-id="4a56c-102">Custom Find Criteria</span></span>
<span data-ttu-id="4a56c-103">Tento příklad znázorňuje, jak vytvořit vlastní rozsah odpovídající pomocí logiky a jak implementovat vlastní zjišťování služby.</span><span class="sxs-lookup"><span data-stu-id="4a56c-103">This sample demonstrates how to create a custom scope match using logic and how to implement a custom discovery service.</span></span> <span data-ttu-id="4a56c-104">Klienti používají k zpřesnění a další sestavení nad funkce poskytované systémem najít zjišťování WCF vlastní rozsah odpovídající funkce.</span><span class="sxs-lookup"><span data-stu-id="4a56c-104">Clients use custom scope matching functionality to refine and further build on top of the system-provided find functionality of WCF Discovery.</span></span> <span data-ttu-id="4a56c-105">Scénáře, který popisuje tato ukázka je následující:</span><span class="sxs-lookup"><span data-stu-id="4a56c-105">The scenario this sample covers is as follows:</span></span>  
  
1.  <span data-ttu-id="4a56c-106">Klient hledá službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="4a56c-106">A client is looking for a calculator service.</span></span>  
  
2.  <span data-ttu-id="4a56c-107">Upřesněte hledání, klient musí použít obor vlastní pravidlo pro porovnávání.</span><span class="sxs-lookup"><span data-stu-id="4a56c-107">To refine its search, the client must use a custom scope matching rule.</span></span>  
  
3.  <span data-ttu-id="4a56c-108">Podle tohoto pravidla odpoví služby zpět do klienta, pokud svůj koncový bod odpovídá některému z rozsahy určené klientem.</span><span class="sxs-lookup"><span data-stu-id="4a56c-108">According to this rule, a service responds back to the client if its endpoint matches any of the scopes specified by the client.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4a56c-109">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="4a56c-109">Demonstrates</span></span>  
  
-   <span data-ttu-id="4a56c-110">Vytvoření vlastní zjišťování služby.</span><span class="sxs-lookup"><span data-stu-id="4a56c-110">Creating a custom discovery service.</span></span>  
  
-   <span data-ttu-id="4a56c-111">Implementace odpovídající vlastní rozsah algoritmem.</span><span class="sxs-lookup"><span data-stu-id="4a56c-111">Implementing a custom scope match by algorithm.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4a56c-112">Diskusní</span><span class="sxs-lookup"><span data-stu-id="4a56c-112">Discussion</span></span>  
 <span data-ttu-id="4a56c-113">Klient hledá "Nebo" typ odpovídající kritériím.</span><span class="sxs-lookup"><span data-stu-id="4a56c-113">The client is looking for "OR" type matching criteria.</span></span> <span data-ttu-id="4a56c-114">Služby zpět odpoví, je-li obory na své koncové body odpovídat oborů zadaných klientem.</span><span class="sxs-lookup"><span data-stu-id="4a56c-114">A service responds back if the scopes on its endpoints match any of the scopes provided by the client.</span></span> <span data-ttu-id="4a56c-115">V tomto případě klient hledá službu kalkulačky, která obsahuje některý z oborů v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="4a56c-115">In this case, the client is looking for a calculator service that has any of the scopes in the following list:</span></span>  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 <span data-ttu-id="4a56c-116">K tomu, přesměruje klienta pro použití obor vlastní pravidlo pro porovnávání předáním porovnání vlastní rozsah identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="4a56c-116">To accomplish this, the client directs services to use a custom scope matching rule by passing in a custom scope match by URI.</span></span> <span data-ttu-id="4a56c-117">Usnadňuje odpovídající vlastní rozsah služby musíte použít vlastní zjišťování služba, která jste srozuměni s tím pravidla shody vlastní rozsah a přidružené logiky odpovídající implementuje.</span><span class="sxs-lookup"><span data-stu-id="4a56c-117">To facilitate the custom scope matching, the service must use a custom discovery service that understands the custom scope match rule and implements the associated matching logic.</span></span>  
  
 <span data-ttu-id="4a56c-118">V projektu klienta otevřete soubor Program.cs.</span><span class="sxs-lookup"><span data-stu-id="4a56c-118">In the client project, open the Program.cs file.</span></span> <span data-ttu-id="4a56c-119">Všimněte si, že `ScopeMatchBy` pole z `FindCriteria` je nastavena na konkrétní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="4a56c-119">Note that the `ScopeMatchBy` field of the `FindCriteria` object is set to a specific URI.</span></span> <span data-ttu-id="4a56c-120">Tento identifikátor se odešle do služby.</span><span class="sxs-lookup"><span data-stu-id="4a56c-120">This identifier is sent to the service.</span></span> <span data-ttu-id="4a56c-121">Pokud službu nerozumí toto pravidlo, ignoruje požadavek klienta najít.</span><span class="sxs-lookup"><span data-stu-id="4a56c-121">If the service does not understand this rule, it ignores the client’s find request.</span></span>  
  
 <span data-ttu-id="4a56c-122">Otevřete projekt služby.</span><span class="sxs-lookup"><span data-stu-id="4a56c-122">Open the service project.</span></span> <span data-ttu-id="4a56c-123">Tři soubory se používají k implementaci vlastních zjišťování služby:</span><span class="sxs-lookup"><span data-stu-id="4a56c-123">Three files are used to implement the Custom Discovery Service:</span></span>  
  
1.  <span data-ttu-id="4a56c-124">**AsyncResult.cs**: Toto je implementace `AsyncResult` který je vyžadován na základě metody zjišťování.</span><span class="sxs-lookup"><span data-stu-id="4a56c-124">**AsyncResult.cs**: This is the implementation of the `AsyncResult` that is required by Discovery methods.</span></span>  
  
2.  <span data-ttu-id="4a56c-125">**CustomDiscoveryService.cs**: Tento soubor implementuje vlastní zjišťování služby.</span><span class="sxs-lookup"><span data-stu-id="4a56c-125">**CustomDiscoveryService.cs**: This file implements the custom discovery service.</span></span> <span data-ttu-id="4a56c-126">Implementace rozšiřuje <xref:System.ServiceModel.Discovery.DiscoveryService> třídy a přepíše nezbytné metody.</span><span class="sxs-lookup"><span data-stu-id="4a56c-126">The implementation extends the <xref:System.ServiceModel.Discovery.DiscoveryService> class and overrides the necessary methods.</span></span> <span data-ttu-id="4a56c-127">Poznámka: implementace <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4a56c-127">Note the implementation of the <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> method.</span></span> <span data-ttu-id="4a56c-128">Metoda zkontroluje, zda byl zadán vlastní rozsah shody pravidlem klientem.</span><span class="sxs-lookup"><span data-stu-id="4a56c-128">The method checks to see whether the custom scope match by rule was specified by the client.</span></span> <span data-ttu-id="4a56c-129">Toto je stejný vlastní identifikátor URI, který klient zadali dřív.</span><span class="sxs-lookup"><span data-stu-id="4a56c-129">This is the same custom URI that the client specified previously.</span></span> <span data-ttu-id="4a56c-130">Pokud je zadán vlastní pravidlo, je následovaný kódová cesta, který implementuje logiku shodu "Nebo".</span><span class="sxs-lookup"><span data-stu-id="4a56c-130">If the custom rule is specified, the code path that implements the "OR" match logic is followed.</span></span>  
  
     <span data-ttu-id="4a56c-131">Tato vlastní logiky projde všechny obory ve všech koncových bodů, které má služba.</span><span class="sxs-lookup"><span data-stu-id="4a56c-131">This custom logic goes through all of the scopes on each of the endpoints that the service has.</span></span> <span data-ttu-id="4a56c-132">Pokud se žádné rozsahy pro koncový bod shodují oborů poskytnutý klientem, přidá službu zjišťování tohoto koncového bodu do odpovědi, která je odeslána zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="4a56c-132">If any of the endpoint's scopes match any of the scopes provided by the client, the discovery service adds that endpoint to the response that is sent back to the client.</span></span>  
  
3.  <span data-ttu-id="4a56c-133">**CustomDiscoveryExtension.cs**: poslední krok při provádění zjišťování služby je připojení Tato implementace vlastní zjišťování služby na hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="4a56c-133">**CustomDiscoveryExtension.cs**: The last step in implementing the discovery service is to connect this implementation of the custom discover service to the service host.</span></span> <span data-ttu-id="4a56c-134">Pomocná třída použít zde je `CustomDiscoveryExtension` třídy.</span><span class="sxs-lookup"><span data-stu-id="4a56c-134">The helper class used here is the `CustomDiscoveryExtension` class.</span></span> <span data-ttu-id="4a56c-135">Tato třída rozšiřuje <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="4a56c-135">This class extends the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> class.</span></span> <span data-ttu-id="4a56c-136">Uživatel musí přepsat <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4a56c-136">The user must override the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> method.</span></span> <span data-ttu-id="4a56c-137">V takovém případě metoda vrací instanci třídy služby vlastní zjišťování, který byl vytvořen ještě před.</span><span class="sxs-lookup"><span data-stu-id="4a56c-137">In this case, the method returns an instance of the custom discovery service that was created before.</span></span> <span data-ttu-id="4a56c-138">`PublishedEndpoints`je <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> obsahující všechny koncové body aplikace, které jsou přidány do <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="4a56c-138">`PublishedEndpoints` is a <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> that contains all of the application endpoints that are added to the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="4a56c-139">Služba vlastní zjišťování to používá k naplnění svůj vnitřní seznam.</span><span class="sxs-lookup"><span data-stu-id="4a56c-139">The custom discovery service uses this to populate its internal list.</span></span> <span data-ttu-id="4a56c-140">Uživatel může přidat další koncový bod metadata.</span><span class="sxs-lookup"><span data-stu-id="4a56c-140">A user can to add other endpoint metadata as well.</span></span>  
  
 <span data-ttu-id="4a56c-141">Nakonec otevřete Program.cs.</span><span class="sxs-lookup"><span data-stu-id="4a56c-141">Lastly, open Program.cs.</span></span> <span data-ttu-id="4a56c-142">Všimněte si, že jak <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a `CustomDiscoveryExtension` jsou přidány do hostitele.</span><span class="sxs-lookup"><span data-stu-id="4a56c-142">Note that both the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and `CustomDiscoveryExtension` are added to the host.</span></span> <span data-ttu-id="4a56c-143">Jakmile to provádí a hostitele má koncový bod pro které bude přijímat zprávy zjišťování, aplikace můžete použít vlastní zjišťování služby.</span><span class="sxs-lookup"><span data-stu-id="4a56c-143">Once this is done and the host has an endpoint over which to receive discovery messages, the application can use the custom discovery service.</span></span>  
  
 <span data-ttu-id="4a56c-144">Zkontrolujte, že klient je možné najít službu, aniž by věděly, jeho adresy.</span><span class="sxs-lookup"><span data-stu-id="4a56c-144">Observe that the client is able to find the service without knowing its address.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4a56c-145">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="4a56c-145">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4a56c-146">Otevřete řešení obsahující projekt.</span><span class="sxs-lookup"><span data-stu-id="4a56c-146">Open the solution that contains the project.</span></span>  
  
2.  <span data-ttu-id="4a56c-147">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="4a56c-147">Build the project.</span></span>  
  
3.  <span data-ttu-id="4a56c-148">Spusťte aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="4a56c-148">Run the service application.</span></span>  
  
4.  <span data-ttu-id="4a56c-149">Spusťte klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4a56c-149">Run the client application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4a56c-150">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="4a56c-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4a56c-151">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4a56c-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4a56c-152">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4a56c-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4a56c-153">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4a56c-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
