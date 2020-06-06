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
ms.openlocfilehash: 8aefb8a20d6a95c5b8062d0c03dcb28a3557ca3d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117477"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="293df-102">Element \<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="293df-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="293df-103">Určuje, zda je plný zásobník vláken potvrzen při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="293df-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="293df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="293df-104">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="293df-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="293df-105">Attributes and Elements</span></span>  
 <span data-ttu-id="293df-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="293df-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="293df-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="293df-107">Attributes</span></span>  
  
|<span data-ttu-id="293df-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="293df-108">Attribute</span></span>|<span data-ttu-id="293df-109">Popis</span><span class="sxs-lookup"><span data-stu-id="293df-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="293df-110">enabled</span><span class="sxs-lookup"><span data-stu-id="293df-110">enabled</span></span>|<span data-ttu-id="293df-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="293df-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="293df-112">Určuje, zda je potvrzování zásobníku úplného vlákna při spuštění vlákna (výchozí chování) zakázáno.</span><span class="sxs-lookup"><span data-stu-id="293df-112">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="293df-113">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="293df-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="293df-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="293df-114">Value</span></span>|<span data-ttu-id="293df-115">Description</span><span class="sxs-lookup"><span data-stu-id="293df-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="293df-116">0</span><span class="sxs-lookup"><span data-stu-id="293df-116">0</span></span>|<span data-ttu-id="293df-117">Nepovolujte výchozí chování modulu CLR (Common Language Runtime), který je při spuštění vlákna potvrzování celého zásobníku vláken.</span><span class="sxs-lookup"><span data-stu-id="293df-117">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="293df-118">1</span><span class="sxs-lookup"><span data-stu-id="293df-118">1</span></span>|<span data-ttu-id="293df-119">Zakáže výchozí chování modulu CLR (Common Language Runtime), který je při spuštění vlákna potvrzování celého zásobníku vláken.</span><span class="sxs-lookup"><span data-stu-id="293df-119">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="293df-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="293df-120">Child Elements</span></span>  
 <span data-ttu-id="293df-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="293df-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="293df-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="293df-122">Parent Elements</span></span>  
  
|<span data-ttu-id="293df-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="293df-123">Element</span></span>|<span data-ttu-id="293df-124">Description</span><span class="sxs-lookup"><span data-stu-id="293df-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="293df-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="293df-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="293df-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="293df-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="293df-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="293df-127">Remarks</span></span>  
 <span data-ttu-id="293df-128">Výchozím chováním modulu CLR (Common Language Runtime) je zápis úplného zásobníku vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="293df-128">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="293df-129">Pokud je třeba na serveru, který má omezené množství paměti, vytvořit velký počet vláken, a většina těchto vláken bude používat velmi málo prostoru zásobníku, server může být lepší, pokud modul CLR (Common Language Runtime) nepotvrdí plný zásobník vláken okamžitě při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="293df-129">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="293df-130">Nespravované hostitele mohou použít `STARTUP_DISABLE_COMMITTHREADSTACK` Příznak spuštění ve výčtu [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) k dosažení stejného výsledku.</span><span class="sxs-lookup"><span data-stu-id="293df-130">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="293df-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="293df-131">Example</span></span>  
 <span data-ttu-id="293df-132">Následující příklad ukazuje, jak zakázat výchozí chování modulu CLR (Common Language Runtime), který slouží k potvrzení zásobníku úplného vlákna při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="293df-132">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="293df-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="293df-133">See also</span></span>

- [<span data-ttu-id="293df-134">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="293df-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="293df-135">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="293df-135">Configuration File Schema</span></span>](../index.md)
