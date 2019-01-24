---
title: '&lt;disableCommitThreadStack&gt; Element'
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
ms.openlocfilehash: 3b02a5365aa2dc2292b0917820782405ba35ad92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534066"
---
# <a name="ltdisablecommitthreadstackgt-element"></a><span data-ttu-id="8093a-102">&lt;disableCommitThreadStack&gt; Element</span><span class="sxs-lookup"><span data-stu-id="8093a-102">&lt;disableCommitThreadStack&gt; Element</span></span>
<span data-ttu-id="8093a-103">Určuje, zda je zásobníku úplného vlákna potvrzeny při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="8093a-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="8093a-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="8093a-104">\<configuration></span></span>  
<span data-ttu-id="8093a-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="8093a-105">\<runtime></span></span>  
<span data-ttu-id="8093a-106">\<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="8093a-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8093a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8093a-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8093a-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8093a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8093a-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8093a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8093a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8093a-110">Attributes</span></span>  
  
|<span data-ttu-id="8093a-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8093a-111">Attribute</span></span>|<span data-ttu-id="8093a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8093a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8093a-113">Povoleno</span><span class="sxs-lookup"><span data-stu-id="8093a-113">enabled</span></span>|<span data-ttu-id="8093a-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8093a-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="8093a-115">Určuje, zda je zakázaný potvrzení zásobníku úplného vlákna při spuštění vlákna (výchozí chování).</span><span class="sxs-lookup"><span data-stu-id="8093a-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8093a-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="8093a-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="8093a-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8093a-117">Value</span></span>|<span data-ttu-id="8093a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8093a-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8093a-119">0</span><span class="sxs-lookup"><span data-stu-id="8093a-119">0</span></span>|<span data-ttu-id="8093a-120">Nezakazujte výchozí chování modulu common language runtime, který je pro potvrzení zásobníku úplného vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="8093a-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="8093a-121">1</span><span class="sxs-lookup"><span data-stu-id="8093a-121">1</span></span>|<span data-ttu-id="8093a-122">Zakážete výchozí chování modulu common language runtime, který je pro potvrzení zásobníku úplného vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="8093a-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8093a-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8093a-123">Child Elements</span></span>  
 <span data-ttu-id="8093a-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="8093a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8093a-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8093a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8093a-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="8093a-126">Element</span></span>|<span data-ttu-id="8093a-127">Popis</span><span class="sxs-lookup"><span data-stu-id="8093a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8093a-128">Kořenový element v každém konfiguračním souboru, který používá modul common language runtime a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="8093a-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="8093a-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8093a-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8093a-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8093a-130">Remarks</span></span>  
 <span data-ttu-id="8093a-131">Výchozí chování modulu common language runtime je potvrzení změn zásobníku úplného vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="8093a-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="8093a-132">Pokud velký počet vláken musí být vytvořen na serveru, který má omezené paměti a většina tato vlákna budou používat velmi málo místa zásobníku, server může být lepší provedeno, zda modul common language runtime nesměrují zásobníku úplného vlákna ihned po vlákno st uštění.</span><span class="sxs-lookup"><span data-stu-id="8093a-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8093a-133">Můžete použít nespravovaným hostitelům `STARTUP_DISABLE_COMMITTHREADSTACK` příznak spuštění v [startup_flags –](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčet k dosažení stejného výsledku.</span><span class="sxs-lookup"><span data-stu-id="8093a-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8093a-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="8093a-134">Example</span></span>  
 <span data-ttu-id="8093a-135">Následující příklad ukazuje, jak zakázat výchozí chování modulu common language runtime, což je potvrzení změn zásobníku úplného vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="8093a-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8093a-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8093a-136">See also</span></span>
- [<span data-ttu-id="8093a-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="8093a-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="8093a-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="8093a-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
