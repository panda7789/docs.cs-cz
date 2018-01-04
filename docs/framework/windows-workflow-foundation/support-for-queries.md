---
title: Podpora pro dotazy
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f20e9fbcad31a3924474793d9107d6a3c4aeef27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="support-for-queries"></a><span data-ttu-id="656ab-102">Podpora pro dotazy</span><span class="sxs-lookup"><span data-stu-id="656ab-102">Support for Queries</span></span>
<span data-ttu-id="656ab-103">Ukládání Instance pracovního postupu SQL zaznamenává sadu známých vlastností v úložišti.</span><span class="sxs-lookup"><span data-stu-id="656ab-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="656ab-104">Uživatelé mohou odesílat dotazy na instancí na základě těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="656ab-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="656ab-105">Následující seznam obsahuje některé z těchto známých vlastností:</span><span class="sxs-lookup"><span data-stu-id="656ab-105">The following list contains some of these well-known properties:</span></span>  
  
-   <span data-ttu-id="656ab-106">**Název lokality.**</span><span class="sxs-lookup"><span data-stu-id="656ab-106">**Site Name.**</span></span> <span data-ttu-id="656ab-107">Název webu, který obsahuje službu.</span><span class="sxs-lookup"><span data-stu-id="656ab-107">Name of the Web site that contains the service.</span></span>  
  
-   <span data-ttu-id="656ab-108">**Relativní cesta.**</span><span class="sxs-lookup"><span data-stu-id="656ab-108">**Relative Application Path.**</span></span> <span data-ttu-id="656ab-109">Cesta aplikace relativně k webu.</span><span class="sxs-lookup"><span data-stu-id="656ab-109">Path of the application relative to the Web site.</span></span>  
  
-   <span data-ttu-id="656ab-110">**Cesta relativní služby.**</span><span class="sxs-lookup"><span data-stu-id="656ab-110">**Relative Service Path.**</span></span> <span data-ttu-id="656ab-111">Cesta relativní k aplikaci služby.</span><span class="sxs-lookup"><span data-stu-id="656ab-111">Path of the service relative to the application.</span></span>  
  
-   <span data-ttu-id="656ab-112">**Název služby.**</span><span class="sxs-lookup"><span data-stu-id="656ab-112">**Service Name.**</span></span> <span data-ttu-id="656ab-113">Název služby</span><span class="sxs-lookup"><span data-stu-id="656ab-113">Name of the service.</span></span>  
  
-   <span data-ttu-id="656ab-114">**Namespace služby.**</span><span class="sxs-lookup"><span data-stu-id="656ab-114">**Service Namespace.**</span></span> <span data-ttu-id="656ab-115">Název oboru názvů, který služba používá.</span><span class="sxs-lookup"><span data-stu-id="656ab-115">Name of the namespace that the service uses.</span></span>  
  
-   <span data-ttu-id="656ab-116">**Aktuálního počítače.**</span><span class="sxs-lookup"><span data-stu-id="656ab-116">**Current Machine.**</span></span>  
  
-   <span data-ttu-id="656ab-117">**Poslední počítač**.</span><span class="sxs-lookup"><span data-stu-id="656ab-117">**Last Machine**.</span></span> <span data-ttu-id="656ab-118">Počítač, na kterém byla spuštěna instance pracovního postupu služby čas poslední.</span><span class="sxs-lookup"><span data-stu-id="656ab-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="656ab-119">Pro scénáře s vlastním hostováním pomocí hostitele služby pracovního postupu naplní se pouze poslední čtyři vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="656ab-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="656ab-120">Pro scénáře aplikace pracovního postupu se importují pouze poslední vlastnost.</span><span class="sxs-lookup"><span data-stu-id="656ab-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="656ab-121">Modul runtime pracovního postupu poskytuje hodnoty pro první tři vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="656ab-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="656ab-122">Hostitel služby pracovního postupu poskytuje hodnota **pozastavit důvod** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="656ab-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="656ab-123">Poskytuje hodnoty pro samotného úložiště Instance pracovního postupu SQL **poslední aktualizovat počítač** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="656ab-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="656ab-124">Funkce úložiště Instance pracovního postupu SQL také umožňuje určit, že vlastní vlastnosti, pro které chcete uložit hodnoty v databázi trvalosti a, které chcete použít v dotazech.</span><span class="sxs-lookup"><span data-stu-id="656ab-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="656ab-125">Další informace o vlastní povýšení najdete v tématu [rozšiřitelnost úložiště](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="656ab-125">For more information about custom promotions, see [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="656ab-126">zobrazení</span><span class="sxs-lookup"><span data-stu-id="656ab-126">Views</span></span>  
 <span data-ttu-id="656ab-127">Instance úložiště obsahuje následující zobrazení.</span><span class="sxs-lookup"><span data-stu-id="656ab-127">The instance store contains the following views.</span></span> <span data-ttu-id="656ab-128">V tématu [schéma databáze trvalost](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="656ab-128">See [Persistence Database Schema](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="656ab-129">Zobrazení instancí</span><span class="sxs-lookup"><span data-stu-id="656ab-129">The Instances View</span></span>  
 <span data-ttu-id="656ab-130">Zobrazení instancí obsahuje následující pole:</span><span class="sxs-lookup"><span data-stu-id="656ab-130">The Instances view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="656ab-131">**ID**</span><span class="sxs-lookup"><span data-stu-id="656ab-131">**Id**</span></span>  
  
2.  <span data-ttu-id="656ab-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="656ab-132">**PendingTimer**</span></span>  
  
3.  <span data-ttu-id="656ab-133">**Čas vytvoření**</span><span class="sxs-lookup"><span data-stu-id="656ab-133">**CreationTime**</span></span>  
  
4.  <span data-ttu-id="656ab-134">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="656ab-134">**LastUpdatedTime**</span></span>  
  
5.  <span data-ttu-id="656ab-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="656ab-135">**ServiceDeploymentId**</span></span>  
  
6.  <span data-ttu-id="656ab-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="656ab-136">**SuspensionExceptionName**</span></span>  
  
7.  <span data-ttu-id="656ab-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="656ab-137">**SuspensionReason**</span></span>  
  
8.  <span data-ttu-id="656ab-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="656ab-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="656ab-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="656ab-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="656ab-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="656ab-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="656ab-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="656ab-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="656ab-142">**IsInitialized.**</span><span class="sxs-lookup"><span data-stu-id="656ab-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="656ab-143">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="656ab-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="656ab-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="656ab-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="656ab-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="656ab-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="656ab-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="656ab-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="656ab-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="656ab-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="656ab-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="656ab-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="656ab-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="656ab-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="656ab-150">Zobrazení ServiceDeployments</span><span class="sxs-lookup"><span data-stu-id="656ab-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="656ab-151">Zobrazení ServiceDeployments obsahuje následující pole:</span><span class="sxs-lookup"><span data-stu-id="656ab-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="656ab-152">**Název webu**</span><span class="sxs-lookup"><span data-stu-id="656ab-152">**SiteName**</span></span>  
  
2.  <span data-ttu-id="656ab-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="656ab-153">**RelativeServicePath**</span></span>  
  
3.  <span data-ttu-id="656ab-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="656ab-154">**RelativeApplicationPath**</span></span>  
  
4.  <span data-ttu-id="656ab-155">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="656ab-155">**ServiceName**</span></span>  
  
5.  <span data-ttu-id="656ab-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="656ab-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="656ab-157">Zobrazení InstancePromotedProperties</span><span class="sxs-lookup"><span data-stu-id="656ab-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="656ab-158">Zobrazení InstancePromotedProperties obsahuje následující pole.</span><span class="sxs-lookup"><span data-stu-id="656ab-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="656ab-159">Podrobnosti propagovaných vlastností najdete v tématu [rozšiřitelnost úložiště](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="656ab-159">For details on promoted properties, see the [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) topic.</span></span>  
  
1.  <span data-ttu-id="656ab-160">**Identifikátor InstanceId**</span><span class="sxs-lookup"><span data-stu-id="656ab-160">**InstanceId**</span></span>  
  
2.  <span data-ttu-id="656ab-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="656ab-161">**EncodingOption**</span></span>  
  
3.  <span data-ttu-id="656ab-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="656ab-162">**PromotionName**</span></span>  
  
4.  <span data-ttu-id="656ab-163">**Hodnota #** (rozsah pole z **Value1** k **Value64**).</span><span class="sxs-lookup"><span data-stu-id="656ab-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
