---
title: Element <disableCommitThreadStack>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5852579758e85bb033af9b6d036fe76444bb8e4
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583853"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="e07af-102">\<disableCommitThreadStack> Element</span><span class="sxs-lookup"><span data-stu-id="e07af-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="e07af-103">Určuje, zda je zásobníku úplného vlákna potvrzeny při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="e07af-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="e07af-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="e07af-104">\<configuration></span></span>  
<span data-ttu-id="e07af-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="e07af-105">\<runtime></span></span>  
<span data-ttu-id="e07af-106">\<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="e07af-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e07af-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e07af-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e07af-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e07af-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e07af-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e07af-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e07af-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e07af-110">Attributes</span></span>  
  
|<span data-ttu-id="e07af-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e07af-111">Attribute</span></span>|<span data-ttu-id="e07af-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e07af-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e07af-113">enabled</span><span class="sxs-lookup"><span data-stu-id="e07af-113">enabled</span></span>|<span data-ttu-id="e07af-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="e07af-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e07af-115">Určuje, zda je zakázaný potvrzení zásobníku úplného vlákna při spuštění vlákna (výchozí chování).</span><span class="sxs-lookup"><span data-stu-id="e07af-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e07af-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="e07af-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="e07af-117">Value</span><span class="sxs-lookup"><span data-stu-id="e07af-117">Value</span></span>|<span data-ttu-id="e07af-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e07af-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e07af-119">0</span><span class="sxs-lookup"><span data-stu-id="e07af-119">0</span></span>|<span data-ttu-id="e07af-120">Nezakazujte výchozí chování modulu common language runtime, který je pro potvrzení zásobníku úplného vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="e07af-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="e07af-121">1</span><span class="sxs-lookup"><span data-stu-id="e07af-121">1</span></span>|<span data-ttu-id="e07af-122">Zakážete výchozí chování modulu common language runtime, který je pro potvrzení zásobníku úplného vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="e07af-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e07af-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e07af-123">Child Elements</span></span>  
 <span data-ttu-id="e07af-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="e07af-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e07af-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e07af-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e07af-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="e07af-126">Element</span></span>|<span data-ttu-id="e07af-127">Popis</span><span class="sxs-lookup"><span data-stu-id="e07af-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e07af-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e07af-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e07af-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="e07af-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e07af-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e07af-130">Remarks</span></span>  
 <span data-ttu-id="e07af-131">Výchozí chování modulu common language runtime je potvrzení změn zásobníku úplného vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="e07af-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="e07af-132">Pokud velký počet vláken musí být vytvořen na serveru, který má omezené paměti a většina tato vlákna budou používat velmi málo místa zásobníku, server může být lepší provedeno, zda modul common language runtime nesměrují zásobníku úplného vlákna ihned po vlákno st uštění.</span><span class="sxs-lookup"><span data-stu-id="e07af-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e07af-133">Můžete použít nespravovaným hostitelům `STARTUP_DISABLE_COMMITTHREADSTACK` příznak spuštění v [startup_flags –](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčet k dosažení stejného výsledku.</span><span class="sxs-lookup"><span data-stu-id="e07af-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e07af-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="e07af-134">Example</span></span>  
 <span data-ttu-id="e07af-135">Následující příklad ukazuje, jak zakázat výchozí chování modulu common language runtime, což je potvrzení změn zásobníku úplného vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="e07af-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e07af-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e07af-136">See also</span></span>

- [<span data-ttu-id="e07af-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="e07af-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="e07af-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="e07af-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
