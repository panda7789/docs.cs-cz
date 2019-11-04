---
title: 'Postupy: povolení trvalosti pro pracovní postupy a služby pracovních postupů'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 5d0eeb8ad40f2f4f3349ab48487316014a561a1b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460889"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="e4975-102">Postupy: povolení trvalosti pro pracovní postupy a služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e4975-102">How to: Enable Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="e4975-103">Toto téma popisuje, jak povolit trvalost pro pracovní postupy a služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="e4975-103">This topic describes how to enable persistence for workflows and workflow services.</span></span>

## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="e4975-104">Povolit trvalost pro pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="e4975-104">Enable Persistence for Workflows</span></span>

<span data-ttu-id="e4975-105">Úložiště instancí můžete přidružit k aplikaci **WorkflowApplication** pomocí vlastnosti <xref:System.Activities.WorkflowApplication.InstanceStore%2A> třídy <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="e4975-105">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="e4975-106">Metoda <xref:System.Activities.WorkflowApplication.Persist%2A> ukládá nebo ukládá pracovní postup do úložiště instancí přidruženého k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e4975-106">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="e4975-107">Metoda <xref:System.Activities.WorkflowApplication.Unload%2A> ukládá pracovní postup do úložiště instance a poté uvolní instanci z paměti.</span><span class="sxs-lookup"><span data-stu-id="e4975-107">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="e4975-108">Metoda **Load** načte pracovní postup do paměti pomocí dat pracovního postupu uložených v úložišti trvalosti instance.</span><span class="sxs-lookup"><span data-stu-id="e4975-108">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>

<span data-ttu-id="e4975-109">Metoda **trvalosti** provádí následující kroky:</span><span class="sxs-lookup"><span data-stu-id="e4975-109">The **Persist** method performs the following steps:</span></span>

1. <span data-ttu-id="e4975-110">Pozastaví Plánovač pracovních postupů a počká, dokud pracovní postup nevstoupí do stavu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="e4975-110">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="e4975-111">Zachovává nebo ukládá pracovní postup do úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="e4975-111">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="e4975-112">Obnoví Scheduler pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e4975-112">Resumes the workflow scheduler.</span></span>

 <span data-ttu-id="e4975-113">Metoda **Unload** provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="e4975-113">The **Unload** method performs the following steps:</span></span>

1. <span data-ttu-id="e4975-114">Pozastaví Plánovač pracovních postupů a počká, dokud pracovní postup nevstoupí do stavu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="e4975-114">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="e4975-115">Zachovává nebo ukládá pracovní postup do úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="e4975-115">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="e4975-116">Odstraní instanci pracovního postupu v paměti.</span><span class="sxs-lookup"><span data-stu-id="e4975-116">Disposes the workflow instance in the memory.</span></span>

<span data-ttu-id="e4975-117">Metody **trvalého** i zrušení **zatížení** budou blokovat, pokud je pracovní postup v zóně bez trvalého uložení, dokud pracovní postup neukončí zónu bez trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="e4975-117">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="e4975-118">Metoda pokračuje v operaci trvalého nebo odnačtení po dokončení zóny bez trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="e4975-118">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="e4975-119">Pokud se zóna No-repersistent nedokončila před vypršením časového limitu, nebo pokud proces trvalosti trvá příliš dlouho, bude vyvolána výjimka TimeoutException.</span><span class="sxs-lookup"><span data-stu-id="e4975-119">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>

## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="e4975-120">Povolení trvalosti pro služby pracovních postupů v kódu</span><span class="sxs-lookup"><span data-stu-id="e4975-120">Enable Persistence for Workflow Services in Code</span></span>

<span data-ttu-id="e4975-121">Člen **DurableInstancingOptions** třídy <xref:System.ServiceModel.WorkflowServiceHost> má vlastnost s názvem **InstanceStore** , kterou můžete použít k přidružení úložiště instancí k **hostiteli**služby.</span><span class="sxs-lookup"><span data-stu-id="e4975-121">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

<span data-ttu-id="e4975-122">Když je **hostitel WorkflowServiceHost** otevřený, trvalost se automaticky povolí, pokud **DurableInstancingOptions. InstanceStore** nemá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e4975-122">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>

<span data-ttu-id="e4975-123">Chování služby obvykle poskytuje konkrétní úložiště instancí, které se má použít s hostitelem služby pracovního postupu pomocí vlastnosti **InstanceStore** .</span><span class="sxs-lookup"><span data-stu-id="e4975-123">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="e4975-124">Například SqlWorkflowInstanceStoreBehavior vytvoří instanci třídy **SqlWorkflowInstanceStore**, nakonfiguruje ji a přiřadí ji k **DurableInstancingOptions. InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="e4975-124">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="e4975-125">Povolení trvalosti pro služby pracovních postupů pomocí konfiguračního souboru aplikace</span><span class="sxs-lookup"><span data-stu-id="e4975-125">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>

<span data-ttu-id="e4975-126">Trvalost lze povolit pomocí konfiguračního souboru aplikace přidáním následujícího kódu do souboru App. config nebo Web. config:</span><span class="sxs-lookup"><span data-stu-id="e4975-126">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```
