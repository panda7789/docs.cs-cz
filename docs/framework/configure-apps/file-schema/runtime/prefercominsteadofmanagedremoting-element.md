---
title: Element <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 1376df4efd56734f2b8da9bd76033afcce8a285b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77452250"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="0d78a-102">Element \<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="0d78a-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="0d78a-103">Určuje, zda modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace pro všechna volání napříč hranicemi domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d78a-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a><span data-ttu-id="0d78a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d78a-104">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d78a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0d78a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0d78a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0d78a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d78a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="0d78a-107">Attributes</span></span>  
  
|<span data-ttu-id="0d78a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="0d78a-108">Attribute</span></span>|<span data-ttu-id="0d78a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0d78a-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0d78a-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0d78a-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="0d78a-111">Určuje, zda modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace napříč hranicemi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="0d78a-111">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0d78a-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="0d78a-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="0d78a-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0d78a-113">Value</span></span>|<span data-ttu-id="0d78a-114">Description</span><span class="sxs-lookup"><span data-stu-id="0d78a-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0d78a-115">Modul runtime bude používat vzdálenou komunikaci napříč hranicemi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="0d78a-115">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="0d78a-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="0d78a-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="0d78a-117">Modul runtime bude používat zprostředkovatele komunikace s objekty COM napříč hranicemi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="0d78a-117">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d78a-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0d78a-118">Child Elements</span></span>  
 <span data-ttu-id="0d78a-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="0d78a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d78a-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0d78a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0d78a-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="0d78a-121">Element</span></span>|<span data-ttu-id="0d78a-122">Description</span><span class="sxs-lookup"><span data-stu-id="0d78a-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0d78a-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d78a-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0d78a-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0d78a-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d78a-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d78a-125">Remarks</span></span>  
 <span data-ttu-id="0d78a-126">Při nastavení `enabled` atributu na `true` se modul runtime chová takto:</span><span class="sxs-lookup"><span data-stu-id="0d78a-126">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="0d78a-127">Modul runtime nevolá [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) pro rozhraní [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) , když rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) vstoupí do domény prostřednictvím rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0d78a-127">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="0d78a-128">Místo toho vytvoří obálku webRCW ( [za běhu](../../../../standard/native-interop/runtime-callable-wrapper.md) ) kolem objektu.</span><span class="sxs-lookup"><span data-stu-id="0d78a-128">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="0d78a-129">Modul runtime vrátí E_NOINTERFACE, když přijme `QueryInterface` volání rozhraní [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) pro libovolný obálku s voláním [modelu COM](../../../../standard/native-interop/com-callable-wrapper.md) (doleva), která byla vytvořena v této doméně.</span><span class="sxs-lookup"><span data-stu-id="0d78a-129">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="0d78a-130">Tato dvě chování zajišťují, že všechna volání rozhraní COM mezi spravovanými objekty napříč hranicemi aplikační domény používají místo vzdálené komunikace COM a COM Interop.</span><span class="sxs-lookup"><span data-stu-id="0d78a-130">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d78a-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d78a-131">Example</span></span>  
 <span data-ttu-id="0d78a-132">Následující příklad ukazuje, jak určit, že modul runtime má používat zprostředkovatele komunikace s objekty COM přes hranice izolace:</span><span class="sxs-lookup"><span data-stu-id="0d78a-132">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d78a-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d78a-133">See also</span></span>

- [<span data-ttu-id="0d78a-134">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0d78a-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0d78a-135">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0d78a-135">Configuration File Schema</span></span>](../index.md)
