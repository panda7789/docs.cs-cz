---
title: Podpora pro dotazy
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 30695fcd791a0d69c31a897068d69838c80c3957
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307948"
---
# <a name="support-for-queries"></a><span data-ttu-id="f0cb3-102">Podpora pro dotazy</span><span class="sxs-lookup"><span data-stu-id="f0cb3-102">Support for Queries</span></span>
<span data-ttu-id="f0cb3-103">Store Instance pracovního postupu SQL zaznamenává sadu dobře známé vlastnosti v úložišti.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="f0cb3-104">Uživatelé mohou odesílat dotazy na instance založené na těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="f0cb3-105">Následující seznam obsahuje některé z těchto dobře známé vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f0cb3-105">The following list contains some of these well-known properties:</span></span>  
  
-   **<span data-ttu-id="f0cb3-106">Název webu.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-106">Site Name.</span></span>** <span data-ttu-id="f0cb3-107">Název webu, který obsahuje službu.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-107">Name of the Web site that contains the service.</span></span>  
  
-   **<span data-ttu-id="f0cb3-108">Cesta relativní aplikace.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-108">Relative Application Path.</span></span>** <span data-ttu-id="f0cb3-109">Cesta k aplikaci vzhledem k webu.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-109">Path of the application relative to the Web site.</span></span>  
  
-   **<span data-ttu-id="f0cb3-110">Cesta relativní služby.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-110">Relative Service Path.</span></span>** <span data-ttu-id="f0cb3-111">Cesta ke službě vzhledem k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-111">Path of the service relative to the application.</span></span>  
  
-   **<span data-ttu-id="f0cb3-112">Název služby.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-112">Service Name.</span></span>** <span data-ttu-id="f0cb3-113">Název služby</span><span class="sxs-lookup"><span data-stu-id="f0cb3-113">Name of the service.</span></span>  
  
-   **<span data-ttu-id="f0cb3-114">Služba Namespace.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-114">Service Namespace.</span></span>** <span data-ttu-id="f0cb3-115">Název oboru názvů, který služba používá.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-115">Name of the namespace that the service uses.</span></span>  
  
-   **<span data-ttu-id="f0cb3-116">Aktuálním počítači.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-116">Current Machine.</span></span>**  
  
-   <span data-ttu-id="f0cb3-117">**Poslední počítač**.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-117">**Last Machine**.</span></span> <span data-ttu-id="f0cb3-118">Počítač, na kterém běžel instance služby pracovního postupu posledního.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0cb3-119">Pro scénáře, v místním prostředí pomocí hostitele služby pracovního postupu naplní se pouze poslední čtyři vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="f0cb3-120">U scénářů s aplikace pracovního postupu se vyplní pouze poslední vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="f0cb3-121">Hodnoty pro první tři vlastnosti dodá modul runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="f0cb3-122">Poskytuje hodnoty pro tohoto hostitele služby pracovního postupu **pozastavit důvod** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="f0cb3-123">Určuje hodnoty pro Store Instance pracovního postupu SQL, samotný **poslední aktualizovat počítač** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="f0cb3-124">Funkce SQL Store Instance pracovního postupu také umožňuje určit, že vlastní vlastnosti, pro které chcete hodnoty uložte do databáze trvalosti a, které chcete použít v dotazech.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="f0cb3-125">Další informace o vlastních propagačních akcí, naleznete v tématu [Store rozšíření](store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="f0cb3-125">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="f0cb3-126">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="f0cb3-126">Views</span></span>  
 <span data-ttu-id="f0cb3-127">V úložišti instancí obsahuje následující zobrazení.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-127">The instance store contains the following views.</span></span> <span data-ttu-id="f0cb3-128">Zobrazit [schéma databáze trvalosti](persistence-database-schema.md) další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-128">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="f0cb3-129">Zobrazení instancí</span><span class="sxs-lookup"><span data-stu-id="f0cb3-129">The Instances View</span></span>  
 <span data-ttu-id="f0cb3-130">Zobrazení instance obsahuje následující pole:</span><span class="sxs-lookup"><span data-stu-id="f0cb3-130">The Instances view contains the following fields:</span></span>  
  
1. **<span data-ttu-id="f0cb3-131">ID</span><span class="sxs-lookup"><span data-stu-id="f0cb3-131">Id</span></span>**  
  
2. **<span data-ttu-id="f0cb3-132">PendingTimer</span><span class="sxs-lookup"><span data-stu-id="f0cb3-132">PendingTimer</span></span>**  
  
3. **<span data-ttu-id="f0cb3-133">CreationTime</span><span class="sxs-lookup"><span data-stu-id="f0cb3-133">CreationTime</span></span>**  
  
4. **<span data-ttu-id="f0cb3-134">LastUpdatedTime</span><span class="sxs-lookup"><span data-stu-id="f0cb3-134">LastUpdatedTime</span></span>**  
  
5. **<span data-ttu-id="f0cb3-135">ServiceDeploymentId</span><span class="sxs-lookup"><span data-stu-id="f0cb3-135">ServiceDeploymentId</span></span>**  
  
6. **<span data-ttu-id="f0cb3-136">SuspensionExceptionName</span><span class="sxs-lookup"><span data-stu-id="f0cb3-136">SuspensionExceptionName</span></span>**  
  
7. **<span data-ttu-id="f0cb3-137">SuspensionReason</span><span class="sxs-lookup"><span data-stu-id="f0cb3-137">SuspensionReason</span></span>**  
  
8. **<span data-ttu-id="f0cb3-138">ActiveBookmarks</span><span class="sxs-lookup"><span data-stu-id="f0cb3-138">ActiveBookmarks</span></span>**  
  
9. **<span data-ttu-id="f0cb3-139">CurrentMachine</span><span class="sxs-lookup"><span data-stu-id="f0cb3-139">CurrentMachine</span></span>**  
  
10. **<span data-ttu-id="f0cb3-140">LastMachine</span><span class="sxs-lookup"><span data-stu-id="f0cb3-140">LastMachine</span></span>**  
  
11. **<span data-ttu-id="f0cb3-141">ExecutionStatus</span><span class="sxs-lookup"><span data-stu-id="f0cb3-141">ExecutionStatus</span></span>**  
  
12. **<span data-ttu-id="f0cb3-142">IsInitialized</span><span class="sxs-lookup"><span data-stu-id="f0cb3-142">IsInitialized</span></span>**  
  
13. **<span data-ttu-id="f0cb3-143">IsSuspended</span><span class="sxs-lookup"><span data-stu-id="f0cb3-143">IsSuspended</span></span>**  
  
14. **<span data-ttu-id="f0cb3-144">IsCompleted</span><span class="sxs-lookup"><span data-stu-id="f0cb3-144">IsCompleted</span></span>**  
  
15. **<span data-ttu-id="f0cb3-145">EncodingOption</span><span class="sxs-lookup"><span data-stu-id="f0cb3-145">EncodingOption</span></span>**  
  
16. **<span data-ttu-id="f0cb3-146">ReadWritePrimitiveDataProperties</span><span class="sxs-lookup"><span data-stu-id="f0cb3-146">ReadWritePrimitiveDataProperties</span></span>**  
  
17. **<span data-ttu-id="f0cb3-147">WriteOnlyPrimitiveDataProperties</span><span class="sxs-lookup"><span data-stu-id="f0cb3-147">WriteOnlyPrimitiveDataProperties</span></span>**  
  
18. **<span data-ttu-id="f0cb3-148">ReadWriteComplexDataProperties</span><span class="sxs-lookup"><span data-stu-id="f0cb3-148">ReadWriteComplexDataProperties</span></span>**  
  
19. **<span data-ttu-id="f0cb3-149">WriteOnlyComplexDataProperties</span><span class="sxs-lookup"><span data-stu-id="f0cb3-149">WriteOnlyComplexDataProperties</span></span>**  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="f0cb3-150">Zobrazení ServiceDeployments</span><span class="sxs-lookup"><span data-stu-id="f0cb3-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="f0cb3-151">Zobrazení ServiceDeployments obsahuje následující pole:</span><span class="sxs-lookup"><span data-stu-id="f0cb3-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1. **<span data-ttu-id="f0cb3-152">SiteName</span><span class="sxs-lookup"><span data-stu-id="f0cb3-152">SiteName</span></span>**  
  
2. **<span data-ttu-id="f0cb3-153">RelativeServicePath</span><span class="sxs-lookup"><span data-stu-id="f0cb3-153">RelativeServicePath</span></span>**  
  
3. **<span data-ttu-id="f0cb3-154">RelativeApplicationPath</span><span class="sxs-lookup"><span data-stu-id="f0cb3-154">RelativeApplicationPath</span></span>**  
  
4. **<span data-ttu-id="f0cb3-155">ServiceName</span><span class="sxs-lookup"><span data-stu-id="f0cb3-155">ServiceName</span></span>**  
  
5. **<span data-ttu-id="f0cb3-156">ServiceNamespace</span><span class="sxs-lookup"><span data-stu-id="f0cb3-156">ServiceNamespace</span></span>**  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="f0cb3-157">Zobrazení InstancePromotedProperties</span><span class="sxs-lookup"><span data-stu-id="f0cb3-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="f0cb3-158">Zobrazení InstancePromotedProperties obsahuje následující pole.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="f0cb3-159">Podrobnosti o propagované vlastnosti, najdete v článku [Store rozšíření](store-extensibility.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="f0cb3-159">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. **<span data-ttu-id="f0cb3-160">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f0cb3-160">InstanceId</span></span>**  
  
2. **<span data-ttu-id="f0cb3-161">EncodingOption</span><span class="sxs-lookup"><span data-stu-id="f0cb3-161">EncodingOption</span></span>**  
  
3. **<span data-ttu-id="f0cb3-162">PromotionName</span><span class="sxs-lookup"><span data-stu-id="f0cb3-162">PromotionName</span></span>**  
  
4. <span data-ttu-id="f0cb3-163">**Hodnota #** (rozsah pole z **hodnota1** k **Value64**).</span><span class="sxs-lookup"><span data-stu-id="f0cb3-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
