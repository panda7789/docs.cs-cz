---
title: Element <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 1376df4efd56734f2b8da9bd76033afcce8a285b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452250"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="40b78-102">\<element > PreferComInsteadOfManagedRemoting</span><span class="sxs-lookup"><span data-stu-id="40b78-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="40b78-103">Určuje, zda modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace pro všechna volání napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="40b78-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
<span data-ttu-id="40b78-104">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="40b78-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="40b78-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="40b78-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="40b78-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<PreferComInsteadOfManagedRemoting >**</span><span class="sxs-lookup"><span data-stu-id="40b78-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40b78-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40b78-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40b78-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="40b78-108">Attributes and Elements</span></span>  
 <span data-ttu-id="40b78-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="40b78-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40b78-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="40b78-110">Attributes</span></span>  
  
|<span data-ttu-id="40b78-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="40b78-111">Attribute</span></span>|<span data-ttu-id="40b78-112">Popis</span><span class="sxs-lookup"><span data-stu-id="40b78-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="40b78-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="40b78-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="40b78-114">Určuje, zda modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace napříč hranicemi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="40b78-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="40b78-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="40b78-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="40b78-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="40b78-116">Value</span></span>|<span data-ttu-id="40b78-117">Popis</span><span class="sxs-lookup"><span data-stu-id="40b78-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="40b78-118">Modul runtime bude používat vzdálenou komunikaci napříč hranicemi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="40b78-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="40b78-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="40b78-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="40b78-120">Modul runtime bude používat zprostředkovatele komunikace s objekty COM napříč hranicemi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="40b78-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40b78-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="40b78-121">Child Elements</span></span>  
 <span data-ttu-id="40b78-122">Žádné.</span><span class="sxs-lookup"><span data-stu-id="40b78-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40b78-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="40b78-123">Parent Elements</span></span>  
  
|<span data-ttu-id="40b78-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="40b78-124">Element</span></span>|<span data-ttu-id="40b78-125">Popis</span><span class="sxs-lookup"><span data-stu-id="40b78-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="40b78-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40b78-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="40b78-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="40b78-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40b78-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40b78-128">Remarks</span></span>  
 <span data-ttu-id="40b78-129">Při nastavení atributu `enabled` na `true`se modul runtime chová takto:</span><span class="sxs-lookup"><span data-stu-id="40b78-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="40b78-130">Modul runtime nevolá [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) pro rozhraní [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) , když rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) vstoupí do domény prostřednictvím rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="40b78-130">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="40b78-131">Místo toho vytvoří obálku webRCW ( [za běhu](../../../../standard/native-interop/runtime-callable-wrapper.md) ) kolem objektu.</span><span class="sxs-lookup"><span data-stu-id="40b78-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="40b78-132">Modul runtime vrátí E_NOINTERFACE, když obdrží `QueryInterface` volání rozhraní [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) pro libovolný [obálku](../../../../standard/native-interop/com-callable-wrapper.md) (doleva) typu com, která byla vytvořena v této doméně.</span><span class="sxs-lookup"><span data-stu-id="40b78-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="40b78-133">Tato dvě chování zajišťují, že všechna volání rozhraní COM mezi spravovanými objekty napříč hranicemi aplikační domény používají místo vzdálené komunikace COM a COM Interop.</span><span class="sxs-lookup"><span data-stu-id="40b78-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40b78-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="40b78-134">Example</span></span>  
 <span data-ttu-id="40b78-135">Následující příklad ukazuje, jak určit, že modul runtime má používat zprostředkovatele komunikace s objekty COM přes hranice izolace:</span><span class="sxs-lookup"><span data-stu-id="40b78-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="40b78-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="40b78-136">See also</span></span>

- [<span data-ttu-id="40b78-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="40b78-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="40b78-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="40b78-138">Configuration File Schema</span></span>](../index.md)
