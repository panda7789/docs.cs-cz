---
title: 'Postupy: Povolení trvalosti pro pracovní postupy a služby pracovních postupů'
description: Přečtěte si, jak nakonfigurovat úložiště instancí pracovních postupů SQL, aby se povolilo uchovávání pracovních postupů a služeb pracovních postupů programově a pomocí konfiguračního souboru.
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 31fe6e3f06989e9a42254747565342cf97e4b9f1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421511"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="99526-103">Postupy: Povolení trvalosti pro pracovní postupy a služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="99526-103">How to: Enable Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="99526-104">Toto téma popisuje, jak povolit trvalost pro pracovní postupy a služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="99526-104">This topic describes how to enable persistence for workflows and workflow services.</span></span>

## <a name="enable-persistence-for-workflows"></a><span data-ttu-id="99526-105">Povolit trvalost pro pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="99526-105">Enable Persistence for Workflows</span></span>

<span data-ttu-id="99526-106">Úložiště instancí můžete přidružit k aplikaci **WorkflowApplication** pomocí <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnosti <xref:System.Activities.WorkflowApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="99526-106">You can associate an instance store with a **WorkflowApplication** by using the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property of the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="99526-107"><xref:System.Activities.WorkflowApplication.Persist%2A>Metoda ukládá nebo ukládá pracovní postup do úložiště instancí přidruženého k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="99526-107">The <xref:System.Activities.WorkflowApplication.Persist%2A> method saves or persists a workflow into the instance store associated with the application.</span></span> <span data-ttu-id="99526-108"><xref:System.Activities.WorkflowApplication.Unload%2A>Metoda uchovává pracovní postup do úložiště instance a poté uvolní instanci z paměti.</span><span class="sxs-lookup"><span data-stu-id="99526-108">The <xref:System.Activities.WorkflowApplication.Unload%2A> method persists a workflow into the instance store and then unloads the instance from the memory.</span></span> <span data-ttu-id="99526-109">Metoda **Load** načte pracovní postup do paměti pomocí dat pracovního postupu uložených v úložišti trvalosti instance.</span><span class="sxs-lookup"><span data-stu-id="99526-109">The **Load** method loads a workflow into memory using the workflow data stored in the instance persistence store.</span></span>

<span data-ttu-id="99526-110">Metoda **trvalosti** provádí následující kroky:</span><span class="sxs-lookup"><span data-stu-id="99526-110">The **Persist** method performs the following steps:</span></span>

1. <span data-ttu-id="99526-111">Pozastaví Plánovač pracovních postupů a počká, dokud pracovní postup nevstoupí do stavu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="99526-111">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="99526-112">Zachovává nebo ukládá pracovní postup do úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="99526-112">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="99526-113">Obnoví Scheduler pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="99526-113">Resumes the workflow scheduler.</span></span>

 <span data-ttu-id="99526-114">Metoda **Unload** provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="99526-114">The **Unload** method performs the following steps:</span></span>

1. <span data-ttu-id="99526-115">Pozastaví Plánovač pracovních postupů a počká, dokud pracovní postup nevstoupí do stavu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="99526-115">Pauses the workflow scheduler and waits until the workflow enters the idle state.</span></span>

2. <span data-ttu-id="99526-116">Zachovává nebo ukládá pracovní postup do úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="99526-116">Persists or saves the workflow into the persistence store.</span></span>

3. <span data-ttu-id="99526-117">Odstraní instanci pracovního postupu v paměti.</span><span class="sxs-lookup"><span data-stu-id="99526-117">Disposes the workflow instance in the memory.</span></span>

<span data-ttu-id="99526-118">Metody **trvalého** i zrušení **zatížení** budou blokovat, pokud je pracovní postup v zóně bez trvalého uložení, dokud pracovní postup neukončí zónu bez trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="99526-118">Both the **Persist** and **Unload** methods will block while a workflow is in a no-persist zone until the workflow exits the no-persist zone.</span></span> <span data-ttu-id="99526-119">Metoda pokračuje v operaci trvalého nebo odnačtení po dokončení zóny bez trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="99526-119">The method continues with the persist or unload operation after the no-persist zone completes.</span></span> <span data-ttu-id="99526-120">Pokud se zóna No-repersistent nedokončila před vypršením časového limitu, nebo pokud proces trvalosti trvá příliš dlouho, bude vyvolána výjimka TimeoutException.</span><span class="sxs-lookup"><span data-stu-id="99526-120">If the no-persist zone does not complete before the time-out elapses, or if the persistence process takes too long, a TimeoutException will be thrown.</span></span>

## <a name="enable-persistence-for-workflow-services-in-code"></a><span data-ttu-id="99526-121">Povolení trvalosti pro služby pracovních postupů v kódu</span><span class="sxs-lookup"><span data-stu-id="99526-121">Enable Persistence for Workflow Services in Code</span></span>

<span data-ttu-id="99526-122">Člen **DurableInstancingOptions** <xref:System.ServiceModel.WorkflowServiceHost> třídy má vlastnost s názvem **InstanceStore** , kterou můžete použít k přidružení úložiště instancí k **hostiteli**služby.</span><span class="sxs-lookup"><span data-stu-id="99526-122">The **DurableInstancingOptions** member of the <xref:System.ServiceModel.WorkflowServiceHost> class has a property named **InstanceStore** that you can use to associate an instance store with the **WorkflowServiceHost**.</span></span>

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

<span data-ttu-id="99526-123">Když je **hostitel WorkflowServiceHost** otevřený, trvalost se automaticky povolí, pokud **DurableInstancingOptions. InstanceStore** nemá hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="99526-123">When the **WorkflowServiceHost** is opened, persistence is automatically enabled if the **DurableInstancingOptions.InstanceStore** is not null.</span></span>

<span data-ttu-id="99526-124">Chování služby obvykle poskytuje konkrétní úložiště instancí, které se má použít s hostitelem služby pracovního postupu pomocí vlastnosti **InstanceStore** .</span><span class="sxs-lookup"><span data-stu-id="99526-124">Typically, a service behavior provides the concrete instance store to be used with a workflow service host by using the **InstanceStore** property.</span></span> <span data-ttu-id="99526-125">Například SqlWorkflowInstanceStoreBehavior vytvoří instanci třídy **SqlWorkflowInstanceStore**, nakonfiguruje ji a přiřadí ji k **DurableInstancingOptions. InstanceStore**.</span><span class="sxs-lookup"><span data-stu-id="99526-125">For example, the SqlWorkflowInstanceStoreBehavior creates an instance of the **SqlWorkflowInstanceStore**, configures it, and assigns it to the **DurableInstancingOptions.InstanceStore**.</span></span>

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a><span data-ttu-id="99526-126">Povolení trvalosti pro služby pracovních postupů pomocí konfiguračního souboru aplikace</span><span class="sxs-lookup"><span data-stu-id="99526-126">Enable Persistence for Workflow Services Using an Application Configuration File</span></span>

<span data-ttu-id="99526-127">Trvalost lze povolit pomocí konfiguračního souboru aplikace přidáním následujícího kódu do souboru App. config nebo Web. config:</span><span class="sxs-lookup"><span data-stu-id="99526-127">Persistence can be enabled using an application configuration file by adding the following code to your app.config or web.config file:</span></span>

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
