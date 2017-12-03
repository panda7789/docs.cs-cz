---
title: "Postupy: povolení trvalosti pro pracovní postupy a služeb pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1db45ecad833c4c05ba240569da9c85271e0b69e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="e579f-102">Postupy: povolení trvalosti pro pracovní postupy a služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e579f-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="e579f-103">Toto téma popisuje, jak povolit trvalost pro pracovní postupy a služeb pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="e579f-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>  
  
## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="e579f-104">Zapnout stálost pro pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="e579f-104">Enable Persistence for Workflows</span></span>  
 <span data-ttu-id="e579f-105">Můžete přidružit ukládání instance s **WorkflowApplication** pomocí <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost <xref:System.Activities.WorkflowApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="e579f-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="e579f-106"><xref:System.Activities.WorkflowApplication.Persist%2A> Metoda uloží nebo potrvají pracovního postupu do instance úložiště přidružené k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e579f-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="e579f-107"><xref:System.Activities.WorkflowApplication.Unload%2A> Metoda potrvají pracovního postupu do úložiště instance a poté uvolní instanci z paměti.</span><span class="sxs-lookup"><span data-stu-id="e579f-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="e579f-108">**Zatížení** metoda načte do paměti pomocí pracovního postupu data uložená v úložišti trvalost instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e579f-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>  
  
 <span data-ttu-id="e579f-109">**Zachovat** metoda provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="e579f-109">The **Persist** method performs the following steps:</span></span>  
  
1.  <span data-ttu-id="e579f-110">Pozastaví Plánovač pracovního postupu a čeká na pracovním postupu vstupuje do stavu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="e579f-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2.  <span data-ttu-id="e579f-111">Potrvají nebo uloží do úložiště trvalosti pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e579f-111">Persists or saves the workflow into the persistence store.</span></span>  
  
3.  <span data-ttu-id="e579f-112">Obnoví Plánovač pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e579f-112">Resumes the workflow scheduler.</span></span>  
  
 <span data-ttu-id="e579f-113">**Uvolnění** metoda provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="e579f-113">The **Unload** method performs the following steps:</span></span>  
  
1.  <span data-ttu-id="e579f-114">Pozastaví Plánovač pracovního postupu a čeká na pracovním postupu vstupuje do stavu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="e579f-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2.  <span data-ttu-id="e579f-115">Potrvají nebo uloží do úložiště trvalosti pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e579f-115">Persists or saves the workflow into the persistence store.</span></span>  
  
3.  <span data-ttu-id="e579f-116">Uvolní instanci pracovního postupu v paměti.</span><span class="sxs-lookup"><span data-stu-id="e579f-116">Disposes the workflow instance in the memory.</span></span>  
  
 <span data-ttu-id="e579f-117">Obě **zachovat** a **uvolnění** metody bude blokovat, když pracovní postup je v zóně no-persist až do konce zóny no-persist pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e579f-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="e579f-118">Metoda pokračuje v operaci zachovat nebo uvolnění po dokončení ne zachovat zóny.</span><span class="sxs-lookup"><span data-stu-id="e579f-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="e579f-119">Pokud zóna no-persist nedokončí předtím, než uplyne časový limit, nebo pokud proces trvalost trvá příliš dlouho, bude vyvolána TimeoutException.</span><span class="sxs-lookup"><span data-stu-id="e579f-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="e579f-120">Zapnout stálost pro pracovní postup služby v kódu</span><span class="sxs-lookup"><span data-stu-id="e579f-120">Enable Persistence for Workflow Services in Code</span></span>  
 <span data-ttu-id="e579f-121">**DurableInstancingOptions** členem <xref:System.ServiceModel.WorkflowServiceHost> třída má vlastnost s názvem **InstanceStore** používané pro přidružení ukládání instance s **hostitele služby pracovního postupu** .</span><span class="sxs-lookup"><span data-stu-id="e579f-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 <span data-ttu-id="e579f-122">Když **hostitele služby pracovního postupu** je otevřené, je automaticky povolena trvalost Pokud **DurableInstancingOptions.InstanceStore** není null.</span><span class="sxs-lookup"><span data-stu-id="e579f-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>  
  
 <span data-ttu-id="e579f-123">Obvykle chování služby poskytuje konkrétní instance úložiště pro použití s hostitele služby pracovního postupu pomocí **InstanceStore** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e579f-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="e579f-124">Například SqlWorkflowInstanceStoreBehavior vytvoří instanci **SqlWorkflowInstanceStore**, nakonfiguruje jej a přiřadí ji k **DurableInstancingOptions.InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="e579f-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="e579f-125">Zapnout stálost pro pracovní postup služby pomocí konfiguračního souboru aplikace</span><span class="sxs-lookup"><span data-stu-id="e579f-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>  
 <span data-ttu-id="e579f-126">Trvalost můžete povolit pomocí konfiguračního souboru aplikace přidáním následující kód do souboru app.config nebo web.config:</span><span class="sxs-lookup"><span data-stu-id="e579f-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```
