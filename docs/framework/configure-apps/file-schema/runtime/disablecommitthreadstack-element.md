---
title: '&lt;disablecommitthreadstack –&gt; – Element'
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
ms.openlocfilehash: 4d8724d16a25cdec040fa5b1f5472da06b11f669
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752660"
---
# <a name="ltdisablecommitthreadstackgt-element"></a><span data-ttu-id="eba96-102">&lt;disablecommitthreadstack –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="eba96-102">&lt;disableCommitThreadStack&gt; Element</span></span>
<span data-ttu-id="eba96-103">Určuje, jestli je úplná vlákno zásobníku potvrzeny při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="eba96-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="eba96-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="eba96-104">\<configuration></span></span>  
<span data-ttu-id="eba96-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="eba96-105">\<runtime></span></span>  
<span data-ttu-id="eba96-106">\<disablecommitthreadstack – ></span><span class="sxs-lookup"><span data-stu-id="eba96-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba96-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eba96-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eba96-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eba96-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eba96-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eba96-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eba96-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="eba96-110">Attributes</span></span>  
  
|<span data-ttu-id="eba96-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="eba96-111">Attribute</span></span>|<span data-ttu-id="eba96-112">Popis</span><span class="sxs-lookup"><span data-stu-id="eba96-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eba96-113">povoleno</span><span class="sxs-lookup"><span data-stu-id="eba96-113">enabled</span></span>|<span data-ttu-id="eba96-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="eba96-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="eba96-115">Určuje, zda je zakázána potvrzení zásobníku úplné vlákno při spuštění vlákna (výchozí nastavení).</span><span class="sxs-lookup"><span data-stu-id="eba96-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="eba96-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="eba96-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="eba96-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="eba96-117">Value</span></span>|<span data-ttu-id="eba96-118">Popis</span><span class="sxs-lookup"><span data-stu-id="eba96-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eba96-119">0</span><span class="sxs-lookup"><span data-stu-id="eba96-119">0</span></span>|<span data-ttu-id="eba96-120">Nezakazujte výchozí chování modul common language runtime, který je při spuštění vlákna potvrzení zásobníku úplný přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="eba96-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="eba96-121">1</span><span class="sxs-lookup"><span data-stu-id="eba96-121">1</span></span>|<span data-ttu-id="eba96-122">Zakážete výchozí chování modul CLR, což je potvrzení zásobníku úplné vlákno při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="eba96-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eba96-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eba96-123">Child Elements</span></span>  
 <span data-ttu-id="eba96-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="eba96-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eba96-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eba96-125">Parent Elements</span></span>  
  
|<span data-ttu-id="eba96-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="eba96-126">Element</span></span>|<span data-ttu-id="eba96-127">Popis</span><span class="sxs-lookup"><span data-stu-id="eba96-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="eba96-128">Kořenový element v každém konfiguračním souboru, který používá modul common language runtime a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="eba96-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="eba96-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="eba96-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eba96-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eba96-130">Remarks</span></span>  
 <span data-ttu-id="eba96-131">Výchozí chování modul common language runtime je potvrzení zásobníku úplné vlákno při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="eba96-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="eba96-132">Pokud velký počet vláken, je nutné vytvořit na serveru, která má omezenou paměti a většinu těchto vláken použije velmi málo místa zásobníku, server může fungovat lépe modul common language runtime nesměrují zásobníku úplné vlákno okamžitě po vlákno st arted.</span><span class="sxs-lookup"><span data-stu-id="eba96-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eba96-133">Nespravované hostitelů můžete použít `STARTUP_DISABLE_COMMITTHREADSTACK` příznak spuštění v [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu k dosažení stejného výsledku.</span><span class="sxs-lookup"><span data-stu-id="eba96-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eba96-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="eba96-134">Example</span></span>  
 <span data-ttu-id="eba96-135">Následující příklad ukazuje, jak zakázat výchozí chování modul CLR, což je potvrzení zásobníku úplné vlákno při spuštění přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="eba96-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eba96-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="eba96-136">See Also</span></span>  
 [<span data-ttu-id="eba96-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="eba96-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="eba96-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="eba96-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
