---
title: '&lt;Prefercominsteadofmanagedremoting –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cac4ebb46fabad49e2e4e6a7d566522ca027094
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a><span data-ttu-id="677b8-102">&lt;Prefercominsteadofmanagedremoting –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="677b8-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span></span>
<span data-ttu-id="677b8-103">Určuje, zda modul runtime bude používat zprostředkovatel komunikace s objekty COM místo vzdálenou komunikaci pro všechna volání napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="677b8-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="677b8-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="677b8-104">\<configuration></span></span>  
<span data-ttu-id="677b8-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="677b8-105">\<runtime></span></span>  
<span data-ttu-id="677b8-106">\<Prefercominsteadofmanagedremoting – ></span><span class="sxs-lookup"><span data-stu-id="677b8-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677b8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="677b8-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="677b8-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="677b8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="677b8-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="677b8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="677b8-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="677b8-110">Attributes</span></span>  
  
|<span data-ttu-id="677b8-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="677b8-111">Attribute</span></span>|<span data-ttu-id="677b8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="677b8-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="677b8-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="677b8-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="677b8-114">Znamená, zda modul runtime použije zprostředkovatel komunikace s objekty COM místo vzdálenou komunikaci napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="677b8-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="677b8-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="677b8-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="677b8-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="677b8-116">Value</span></span>|<span data-ttu-id="677b8-117">Popis</span><span class="sxs-lookup"><span data-stu-id="677b8-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="677b8-118">Modul runtime použije vzdálenou komunikaci napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="677b8-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="677b8-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="677b8-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="677b8-120">Modul runtime použije zprostředkovatel komunikace s objekty COM napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="677b8-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="677b8-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="677b8-121">Child Elements</span></span>  
 <span data-ttu-id="677b8-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="677b8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="677b8-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="677b8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="677b8-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="677b8-124">Element</span></span>|<span data-ttu-id="677b8-125">Popis</span><span class="sxs-lookup"><span data-stu-id="677b8-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="677b8-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="677b8-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="677b8-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="677b8-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="677b8-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="677b8-128">Remarks</span></span>  
 <span data-ttu-id="677b8-129">Když nastavíte `enabled` atribut `true`, modul runtime chová následovně:</span><span class="sxs-lookup"><span data-stu-id="677b8-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="677b8-130">Modul runtime nevyvolá [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) pro [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) rozhraní, kdy [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) rozhraní zadá domény prostřednictvím rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="677b8-130">The runtime does not call [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="677b8-131">Místo toho vytvoří [obálka volatelná za běhu](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) kolem objektu.</span><span class="sxs-lookup"><span data-stu-id="677b8-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="677b8-132">Modul runtime vrátí E_NOINTERFACE při přijetí `QueryInterface` volání pro [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) rozhraní pro všechny [obálka volatelná aplikacemi COM](../../../../../docs/framework/interop/com-callable-wrapper.md) (doleva), byl vytvořen v této doméně.</span><span class="sxs-lookup"><span data-stu-id="677b8-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="677b8-133">Tyto dvě chování Ujistěte se, že všechna volání přes COM rozhraní mezi spravovaných objektů mezi použijte hranice domény aplikace modelu COM a zprostředkovatel komunikace s objekty COM místo vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="677b8-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="677b8-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="677b8-134">Example</span></span>  
 <span data-ttu-id="677b8-135">Následující příklad ukazuje, jak určit, že modul runtime by měl používat COM spolupráce napříč hranicemi izolace:</span><span class="sxs-lookup"><span data-stu-id="677b8-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="677b8-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="677b8-136">See Also</span></span>  
 [<span data-ttu-id="677b8-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="677b8-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="677b8-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="677b8-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
