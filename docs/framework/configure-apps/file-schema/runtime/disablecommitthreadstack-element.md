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
ms.openlocfilehash: 2fa32d64f3ce440981c5f26d731051a118ed9254
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252672"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="cadc6-102">\<disableCommitThreadStack – element ></span><span class="sxs-lookup"><span data-stu-id="cadc6-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="cadc6-103">Určuje, zda je plný zásobník vláken potvrzen při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="cadc6-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
<span data-ttu-id="cadc6-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cadc6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cadc6-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="cadc6-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="cadc6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCommitThreadStack>**</span><span class="sxs-lookup"><span data-stu-id="cadc6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cadc6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cadc6-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cadc6-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cadc6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cadc6-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cadc6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cadc6-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="cadc6-110">Attributes</span></span>  
  
|<span data-ttu-id="cadc6-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="cadc6-111">Attribute</span></span>|<span data-ttu-id="cadc6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="cadc6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cadc6-113">enabled</span><span class="sxs-lookup"><span data-stu-id="cadc6-113">enabled</span></span>|<span data-ttu-id="cadc6-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="cadc6-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="cadc6-115">Určuje, zda je potvrzování zásobníku úplného vlákna při spuštění vlákna (výchozí chování) zakázáno.</span><span class="sxs-lookup"><span data-stu-id="cadc6-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="cadc6-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="cadc6-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="cadc6-117">Value</span><span class="sxs-lookup"><span data-stu-id="cadc6-117">Value</span></span>|<span data-ttu-id="cadc6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="cadc6-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cadc6-119">0</span><span class="sxs-lookup"><span data-stu-id="cadc6-119">0</span></span>|<span data-ttu-id="cadc6-120">Nepovolujte výchozí chování modulu CLR (Common Language Runtime), který je při spuštění vlákna potvrzování celého zásobníku vláken.</span><span class="sxs-lookup"><span data-stu-id="cadc6-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="cadc6-121">1</span><span class="sxs-lookup"><span data-stu-id="cadc6-121">1</span></span>|<span data-ttu-id="cadc6-122">Zakáže výchozí chování modulu CLR (Common Language Runtime), který je při spuštění vlákna potvrzování celého zásobníku vláken.</span><span class="sxs-lookup"><span data-stu-id="cadc6-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cadc6-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cadc6-123">Child Elements</span></span>  
 <span data-ttu-id="cadc6-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="cadc6-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cadc6-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cadc6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cadc6-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="cadc6-126">Element</span></span>|<span data-ttu-id="cadc6-127">Popis</span><span class="sxs-lookup"><span data-stu-id="cadc6-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cadc6-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cadc6-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="cadc6-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="cadc6-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cadc6-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cadc6-130">Remarks</span></span>  
 <span data-ttu-id="cadc6-131">Výchozím chováním modulu CLR (Common Language Runtime) je zápis úplného zásobníku vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="cadc6-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="cadc6-132">Pokud je třeba vytvořit velký počet vláken na serveru, který má omezené množství paměti, a většina těchto vláken bude používat velmi málo prostoru zásobníku, server může být lepší, pokud modul CLR (Common Language Runtime) nepotvrdí plný zásobník vláken okamžitě, když je vlákno St. arted.</span><span class="sxs-lookup"><span data-stu-id="cadc6-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cadc6-133">Nespravované hostitele můžou použít `STARTUP_DISABLE_COMMITTHREADSTACK` příznak spuštění ve výčtu [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) k dosažení stejného výsledku.</span><span class="sxs-lookup"><span data-stu-id="cadc6-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cadc6-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="cadc6-134">Example</span></span>  
 <span data-ttu-id="cadc6-135">Následující příklad ukazuje, jak zakázat výchozí chování modulu CLR (Common Language Runtime), který slouží k potvrzení zásobníku úplného vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="cadc6-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cadc6-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cadc6-136">See also</span></span>

- [<span data-ttu-id="cadc6-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="cadc6-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cadc6-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="cadc6-138">Configuration File Schema</span></span>](../index.md)
