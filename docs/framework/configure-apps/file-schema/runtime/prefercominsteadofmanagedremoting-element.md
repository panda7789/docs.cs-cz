---
title: "&lt;Prefercominsteadofmanagedremoting –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7aed6baa227b2bdf90c26f02d38ee67c1ffbbda1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a><span data-ttu-id="8af43-102">&lt;Prefercominsteadofmanagedremoting –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="8af43-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span></span>
<span data-ttu-id="8af43-103">Určuje, zda modul runtime bude používat zprostředkovatel komunikace s objekty COM místo vzdálenou komunikaci pro všechna volání napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="8af43-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="8af43-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="8af43-104">\<configuration></span></span>  
<span data-ttu-id="8af43-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="8af43-105">\<runtime></span></span>  
<span data-ttu-id="8af43-106">\<Prefercominsteadofmanagedremoting – ></span><span class="sxs-lookup"><span data-stu-id="8af43-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8af43-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8af43-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8af43-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8af43-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8af43-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8af43-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8af43-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8af43-110">Attributes</span></span>  
  
|<span data-ttu-id="8af43-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8af43-111">Attribute</span></span>|<span data-ttu-id="8af43-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8af43-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8af43-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8af43-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8af43-114">Znamená, zda modul runtime použije zprostředkovatel komunikace s objekty COM místo vzdálenou komunikaci napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="8af43-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8af43-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="8af43-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="8af43-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8af43-116">Value</span></span>|<span data-ttu-id="8af43-117">Popis</span><span class="sxs-lookup"><span data-stu-id="8af43-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="8af43-118">Modul runtime použije vzdálenou komunikaci napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="8af43-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="8af43-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="8af43-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="8af43-120">Modul runtime použije zprostředkovatel komunikace s objekty COM napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="8af43-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8af43-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8af43-121">Child Elements</span></span>  
 <span data-ttu-id="8af43-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="8af43-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8af43-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8af43-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8af43-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="8af43-124">Element</span></span>|<span data-ttu-id="8af43-125">Popis</span><span class="sxs-lookup"><span data-stu-id="8af43-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8af43-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8af43-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8af43-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8af43-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8af43-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8af43-128">Remarks</span></span>  
 <span data-ttu-id="8af43-129">Když nastavíte `enabled` atribut `true`, modul runtime chová následovně:</span><span class="sxs-lookup"><span data-stu-id="8af43-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="8af43-130">Modul runtime nevyvolá [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) pro [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) rozhraní, kdy [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) rozhraní zadá domény prostřednictvím rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="8af43-130">The runtime does not call [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="8af43-131">Místo toho vytvoří [obálka volatelná za běhu](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) kolem objektu.</span><span class="sxs-lookup"><span data-stu-id="8af43-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="8af43-132">Modul runtime vrátí E_NOINTERFACE při přijetí `QueryInterface` volání pro [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) rozhraní pro všechny [obálka volatelná aplikacemi COM](../../../../../docs/framework/interop/com-callable-wrapper.md) (doleva), byl vytvořen v této doméně.</span><span class="sxs-lookup"><span data-stu-id="8af43-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="8af43-133">Tyto dvě chování Ujistěte se, že všechna volání přes COM rozhraní mezi spravovaných objektů mezi použijte hranice domény aplikace modelu COM a zprostředkovatel komunikace s objekty COM místo vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="8af43-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8af43-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="8af43-134">Example</span></span>  
 <span data-ttu-id="8af43-135">Následující příklad ukazuje, jak určit, že modul runtime by měl používat COM spolupráce napříč hranicemi izolace:</span><span class="sxs-lookup"><span data-stu-id="8af43-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8af43-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="8af43-136">See Also</span></span>  
 [<span data-ttu-id="8af43-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="8af43-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="8af43-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="8af43-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
