---
title: Element <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c7a558af17493c955b4f148d0abf7f42c9dd6f8
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629432"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="2214f-102">\<PreferComInsteadOfManagedRemoting> Element</span><span class="sxs-lookup"><span data-stu-id="2214f-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="2214f-103">Určuje, zda modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace pro všechna volání napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2214f-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="2214f-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="2214f-104">\<configuration></span></span>  
<span data-ttu-id="2214f-105">\<> modulu runtime</span><span class="sxs-lookup"><span data-stu-id="2214f-105">\<runtime></span></span>  
<span data-ttu-id="2214f-106">\<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="2214f-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2214f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2214f-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2214f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2214f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2214f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2214f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2214f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2214f-110">Attributes</span></span>  
  
|<span data-ttu-id="2214f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2214f-111">Attribute</span></span>|<span data-ttu-id="2214f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2214f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2214f-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2214f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2214f-114">Určuje, zda modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace napříč hranicemi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="2214f-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2214f-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="2214f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2214f-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2214f-116">Value</span></span>|<span data-ttu-id="2214f-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2214f-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2214f-118">Modul runtime bude používat vzdálenou komunikaci napříč hranicemi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="2214f-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="2214f-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="2214f-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="2214f-120">Modul runtime bude používat zprostředkovatele komunikace s objekty COM napříč hranicemi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="2214f-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2214f-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2214f-121">Child Elements</span></span>  
 <span data-ttu-id="2214f-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="2214f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2214f-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2214f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2214f-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="2214f-124">Element</span></span>|<span data-ttu-id="2214f-125">Popis</span><span class="sxs-lookup"><span data-stu-id="2214f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2214f-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2214f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2214f-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="2214f-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2214f-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2214f-128">Remarks</span></span>  
 <span data-ttu-id="2214f-129">Při nastavení `enabled` atributu na `true`se modul runtime chová takto:</span><span class="sxs-lookup"><span data-stu-id="2214f-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="2214f-130">Modul runtime nevolá [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) pro rozhraní [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) , když rozhraní [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) vstoupí do domény prostřednictvím rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="2214f-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="2214f-131">Místo toho vytvoří obálku webRCW ( [za běhu](../../../../../docs/standard/native-interop/runtime-callable-wrapper.md) ) kolem objektu.</span><span class="sxs-lookup"><span data-stu-id="2214f-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="2214f-132">Modul runtime vrátí E_NOINTERFACE, když přijme `QueryInterface` volání rozhraní [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) pro libovolný obálku s voláním [modelu COM](../../../../../docs/standard/native-interop/com-callable-wrapper.md) (doleva), která byla vytvořena v této doméně.</span><span class="sxs-lookup"><span data-stu-id="2214f-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="2214f-133">Tato dvě chování zajišťují, že všechna volání rozhraní COM mezi spravovanými objekty napříč hranicemi aplikační domény používají místo vzdálené komunikace COM a COM Interop.</span><span class="sxs-lookup"><span data-stu-id="2214f-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2214f-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="2214f-134">Example</span></span>  
 <span data-ttu-id="2214f-135">Následující příklad ukazuje, jak určit, že modul runtime má používat zprostředkovatele komunikace s objekty COM přes hranice izolace:</span><span class="sxs-lookup"><span data-stu-id="2214f-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2214f-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2214f-136">See also</span></span>

- [<span data-ttu-id="2214f-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="2214f-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="2214f-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2214f-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
