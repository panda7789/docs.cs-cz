---
title: Podpora pro dotazy
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: e281b5ae7a41bd282f8e7c7eb9db6f99ef5487f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948940"
---
# <a name="support-for-queries"></a><span data-ttu-id="042de-102">Podpora pro dotazy</span><span class="sxs-lookup"><span data-stu-id="042de-102">Support for Queries</span></span>
<span data-ttu-id="042de-103">Úložiště instance pracovního postupu SQL zaznamenává sadu známých vlastností ve Storu.</span><span class="sxs-lookup"><span data-stu-id="042de-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="042de-104">Uživatelé se mohou dotazovat na instance na základě těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="042de-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="042de-105">Následující seznam obsahuje některé z těchto dobře známých vlastností:</span><span class="sxs-lookup"><span data-stu-id="042de-105">The following list contains some of these well-known properties:</span></span>  
  
- <span data-ttu-id="042de-106">**Název lokality**</span><span class="sxs-lookup"><span data-stu-id="042de-106">**Site Name.**</span></span> <span data-ttu-id="042de-107">Název webu, který obsahuje službu.</span><span class="sxs-lookup"><span data-stu-id="042de-107">Name of the Web site that contains the service.</span></span>  
  
- <span data-ttu-id="042de-108">**Relativní cesta k aplikaci**</span><span class="sxs-lookup"><span data-stu-id="042de-108">**Relative Application Path.**</span></span> <span data-ttu-id="042de-109">Cesta aplikace vzhledem k webu</span><span class="sxs-lookup"><span data-stu-id="042de-109">Path of the application relative to the Web site.</span></span>  
  
- <span data-ttu-id="042de-110">**Relativní cesta služby**</span><span class="sxs-lookup"><span data-stu-id="042de-110">**Relative Service Path.**</span></span> <span data-ttu-id="042de-111">Cesta ke službě vzhledem k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="042de-111">Path of the service relative to the application.</span></span>  
  
- <span data-ttu-id="042de-112">**Název služby**</span><span class="sxs-lookup"><span data-stu-id="042de-112">**Service Name.**</span></span> <span data-ttu-id="042de-113">Název služby</span><span class="sxs-lookup"><span data-stu-id="042de-113">Name of the service.</span></span>  
  
- <span data-ttu-id="042de-114">**Obor názvů služby**</span><span class="sxs-lookup"><span data-stu-id="042de-114">**Service Namespace.**</span></span> <span data-ttu-id="042de-115">Název oboru názvů, který služba používá.</span><span class="sxs-lookup"><span data-stu-id="042de-115">Name of the namespace that the service uses.</span></span>  
  
- <span data-ttu-id="042de-116">**Aktuální počítač.**</span><span class="sxs-lookup"><span data-stu-id="042de-116">**Current Machine.**</span></span>  
  
- <span data-ttu-id="042de-117">**Poslední počítač**.</span><span class="sxs-lookup"><span data-stu-id="042de-117">**Last Machine**.</span></span> <span data-ttu-id="042de-118">Počítač, ve kterém se spustila instance služby pracovního postupu naposledy.</span><span class="sxs-lookup"><span data-stu-id="042de-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="042de-119">V případě scénářů s vlastním hostováním pomocí hostitele služby pracovního postupu se naplní jenom poslední čtyři vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="042de-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="042de-120">Pro scénáře aplikace pracovního postupu se naplní jenom poslední vlastnost.</span><span class="sxs-lookup"><span data-stu-id="042de-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="042de-121">Běhové prostředí pracovního postupu poskytuje hodnoty pro první tři vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="042de-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="042de-122">Hostitel služby pracovního postupu poskytuje hodnotu pro vlastnost **důvod pozastavení** .</span><span class="sxs-lookup"><span data-stu-id="042de-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="042de-123">Vlastní úložiště instance pracovního postupu SQL poskytuje hodnoty pro **Poslední aktualizovanou vlastnost počítače** .</span><span class="sxs-lookup"><span data-stu-id="042de-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="042de-124">Funkce úložiště instance pracovního postupu SQL také umožňuje určit vlastní vlastnosti, pro které chcete ukládat hodnoty do databáze trvalosti a které chcete použít v dotazech.</span><span class="sxs-lookup"><span data-stu-id="042de-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="042de-125">Další informace o vlastních propagačních akcích najdete v tématu [rozšiřitelnost úložiště](store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="042de-125">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="042de-126">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="042de-126">Views</span></span>  
 <span data-ttu-id="042de-127">Úložiště instancí obsahuje následující zobrazení.</span><span class="sxs-lookup"><span data-stu-id="042de-127">The instance store contains the following views.</span></span> <span data-ttu-id="042de-128">Další podrobnosti najdete v tématu [schéma databáze trvalosti](persistence-database-schema.md) .</span><span class="sxs-lookup"><span data-stu-id="042de-128">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="042de-129">Zobrazení instance</span><span class="sxs-lookup"><span data-stu-id="042de-129">The Instances View</span></span>  
 <span data-ttu-id="042de-130">Zobrazení instance obsahuje následující pole:</span><span class="sxs-lookup"><span data-stu-id="042de-130">The Instances view contains the following fields:</span></span>  
  
1. <span data-ttu-id="042de-131">**ID**</span><span class="sxs-lookup"><span data-stu-id="042de-131">**Id**</span></span>  
  
2. <span data-ttu-id="042de-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="042de-132">**PendingTimer**</span></span>  
  
3. <span data-ttu-id="042de-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="042de-133">**CreationTime**</span></span>  
  
4. <span data-ttu-id="042de-134">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="042de-134">**LastUpdatedTime**</span></span>  
  
5. <span data-ttu-id="042de-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="042de-135">**ServiceDeploymentId**</span></span>  
  
6. <span data-ttu-id="042de-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="042de-136">**SuspensionExceptionName**</span></span>  
  
7. <span data-ttu-id="042de-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="042de-137">**SuspensionReason**</span></span>  
  
8. <span data-ttu-id="042de-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="042de-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="042de-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="042de-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="042de-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="042de-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="042de-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="042de-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="042de-142">**IsInitialized**</span><span class="sxs-lookup"><span data-stu-id="042de-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="042de-143">**Pozastaveno**</span><span class="sxs-lookup"><span data-stu-id="042de-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="042de-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="042de-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="042de-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="042de-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="042de-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="042de-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="042de-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="042de-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="042de-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="042de-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="042de-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="042de-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="042de-150">Zobrazení ServiceDeployments</span><span class="sxs-lookup"><span data-stu-id="042de-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="042de-151">Zobrazení ServiceDeployments obsahuje následující pole:</span><span class="sxs-lookup"><span data-stu-id="042de-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1. <span data-ttu-id="042de-152">**Názvem**</span><span class="sxs-lookup"><span data-stu-id="042de-152">**SiteName**</span></span>  
  
2. <span data-ttu-id="042de-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="042de-153">**RelativeServicePath**</span></span>  
  
3. <span data-ttu-id="042de-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="042de-154">**RelativeApplicationPath**</span></span>  
  
4. <span data-ttu-id="042de-155">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="042de-155">**ServiceName**</span></span>  
  
5. <span data-ttu-id="042de-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="042de-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="042de-157">Zobrazení InstancePromotedProperties</span><span class="sxs-lookup"><span data-stu-id="042de-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="042de-158">Zobrazení InstancePromotedProperties obsahuje následující pole.</span><span class="sxs-lookup"><span data-stu-id="042de-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="042de-159">Podrobnosti o propagovaných vlastnostech najdete v tématu [rozšiřitelnost obchodu](store-extensibility.md) .</span><span class="sxs-lookup"><span data-stu-id="042de-159">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. <span data-ttu-id="042de-160">**InstanceId**</span><span class="sxs-lookup"><span data-stu-id="042de-160">**InstanceId**</span></span>  
  
2. <span data-ttu-id="042de-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="042de-161">**EncodingOption**</span></span>  
  
3. <span data-ttu-id="042de-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="042de-162">**PromotionName**</span></span>  
  
4. <span data-ttu-id="042de-163">**Hodnota #** (rozsah polí z **hodnota1** do **Value64**).</span><span class="sxs-lookup"><span data-stu-id="042de-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
