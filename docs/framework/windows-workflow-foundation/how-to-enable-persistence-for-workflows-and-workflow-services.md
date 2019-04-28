---
title: 'Postupy: Povolení trvalosti pro pracovní postupy a služby pracovních postupů'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 6a2a8d73298e14f92f376b97b9637db91532e937
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761426"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="eaae9-102">Postupy: Povolení trvalosti pro pracovní postupy a služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="eaae9-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="eaae9-103">Toto téma popisuje postup povolení trvalosti pro pracovní postupy a služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="eaae9-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>  
  
## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="eaae9-104">Povolení trvalosti pro pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="eaae9-104">Enable Persistence for Workflows</span></span>  
 <span data-ttu-id="eaae9-105">Můžete přidružit ukládání instance s **WorkflowApplication** pomocí <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost <xref:System.Activities.WorkflowApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="eaae9-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="eaae9-106"><xref:System.Activities.WorkflowApplication.Persist%2A> Metoda uloží nebo nevyřeší pracovního postupu do úložiště instancí přidružené k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eaae9-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="eaae9-107"><xref:System.Activities.WorkflowApplication.Unload%2A> Metoda uchovává pracovního postupu do úložiště instancí a poté uvolní instanci z paměti.</span><span class="sxs-lookup"><span data-stu-id="eaae9-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="eaae9-108">**Zatížení** metoda načte do paměti pomocí pracovního postupu data uložená v úložišti stálost instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="eaae9-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>  
  
 <span data-ttu-id="eaae9-109">**Trvalého** metoda provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="eaae9-109">The **Persist** method performs the following steps:</span></span>  
  
1. <span data-ttu-id="eaae9-110">Plánovač pracovní postup se pozastaví a počká, dokud pracovního postupu přejde do stavu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="eaae9-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2. <span data-ttu-id="eaae9-111">Opakuje nebo uloží pracovní postup do trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="eaae9-111">Persists or saves the workflow into the persistence store.</span></span>  
  
3. <span data-ttu-id="eaae9-112">Obnoví Plánovač pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="eaae9-112">Resumes the workflow scheduler.</span></span>  
  
 <span data-ttu-id="eaae9-113">**Uvolnění** metoda provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="eaae9-113">The **Unload** method performs the following steps:</span></span>  
  
1. <span data-ttu-id="eaae9-114">Plánovač pracovní postup se pozastaví a počká, dokud pracovního postupu přejde do stavu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="eaae9-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>  
  
2. <span data-ttu-id="eaae9-115">Opakuje nebo uloží pracovní postup do trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="eaae9-115">Persists or saves the workflow into the persistence store.</span></span>  
  
3. <span data-ttu-id="eaae9-116">Uvolní instanci pracovního postupu v paměti.</span><span class="sxs-lookup"><span data-stu-id="eaae9-116">Disposes the workflow instance in the memory.</span></span>  
  
 <span data-ttu-id="eaae9-117">Oba **trvalého** a **uvolnění** metody budou blokovat, zatímco pracovní postup je v zóně no-persist až do ukončení pracovního postupu no-persist zóny.</span><span class="sxs-lookup"><span data-stu-id="eaae9-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="eaae9-118">Metoda pokračuje zachovat nebo uvolnit operaci po dokončení bez dočasného zóny.</span><span class="sxs-lookup"><span data-stu-id="eaae9-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="eaae9-119">Zóna no-persist nedokončí předtím, než uplyne časový limit, nebo pokud proces trvalého trvá příliš dlouho, bude vyvolána výjimka TimeoutException.</span><span class="sxs-lookup"><span data-stu-id="eaae9-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="eaae9-120">Povolení trvalosti pro pracovní postup služby v kódu</span><span class="sxs-lookup"><span data-stu-id="eaae9-120">Enable Persistence for Workflow Services in Code</span></span>  
 <span data-ttu-id="eaae9-121">**DurableInstancingOptions** člena <xref:System.ServiceModel.WorkflowServiceHost> třída nemá vlastnost s názvem **třídy InstanceStore** , můžete přidružit ukládání instance s **hostitele služby pracovního postupu** .</span><span class="sxs-lookup"><span data-stu-id="eaae9-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 <span data-ttu-id="eaae9-122">Když **hostitele služby pracovního postupu** je otevřen, je automaticky povolena trvalost Pokud **DurableInstancingOptions.InstanceStore** nemá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="eaae9-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>  
  
 <span data-ttu-id="eaae9-123">Obvykle, chování služby poskytuje úložiště konkrétní instance pro použití s hostitele služby pracovního postupu pomocí **třídy InstanceStore** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eaae9-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="eaae9-124">Například, SqlWorkflowInstanceStoreBehavior vytvoří instanci **SqlWorkflowInstanceStore**, nakonfiguruje a přiřadí ji k **DurableInstancingOptions.InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="eaae9-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="eaae9-125">Povolení trvalosti pro pracovní postup služby pomocí konfiguračního souboru aplikace</span><span class="sxs-lookup"><span data-stu-id="eaae9-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>  
 <span data-ttu-id="eaae9-126">Trvalost se dá nastavit pomocí konfiguračního souboru aplikace tak, že přidáte následující kód do souboru app.config nebo web.config:</span><span class="sxs-lookup"><span data-stu-id="eaae9-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>  
  
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
