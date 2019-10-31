---
title: Element <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: bae4aa39f9c43480ac2ef984f78834b68646742d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118233"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="0bf47-102">\<element > appDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="0bf47-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="0bf47-103">Určuje typ, který slouží jako správce aplikační domény pro výchozí doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0bf47-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
<span data-ttu-id="0bf47-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0bf47-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0bf47-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="0bf47-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="0bf47-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerType >**</span><span class="sxs-lookup"><span data-stu-id="0bf47-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf47-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bf47-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bf47-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0bf47-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0bf47-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0bf47-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bf47-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0bf47-110">Attributes</span></span>  
  
|<span data-ttu-id="0bf47-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="0bf47-111">Attribute</span></span>|<span data-ttu-id="0bf47-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0bf47-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="0bf47-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0bf47-113">Required attribute.</span></span> <span data-ttu-id="0bf47-114">Určuje název typu, včetně oboru názvů, který slouží jako správce aplikační domény pro výchozí doménu aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="0bf47-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0bf47-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0bf47-115">Child Elements</span></span>  
 <span data-ttu-id="0bf47-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="0bf47-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0bf47-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0bf47-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0bf47-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="0bf47-118">Element</span></span>|<span data-ttu-id="0bf47-119">Popis</span><span class="sxs-lookup"><span data-stu-id="0bf47-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0bf47-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0bf47-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0bf47-121">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0bf47-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bf47-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bf47-122">Remarks</span></span>  
 <span data-ttu-id="0bf47-123">Chcete-li zadat typ Správce aplikační domény, je nutné zadat jak tento prvek, tak [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="0bf47-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="0bf47-124">Pokud některý z těchto prvků není zadán, druhá je ignorována.</span><span class="sxs-lookup"><span data-stu-id="0bf47-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="0bf47-125">Když je načtena výchozí doména aplikace, <xref:System.TypeLoadException> je vyvolána, pokud zadaný typ neexistuje v sestavení určeném [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) elementu; a proces se nepodařilo spustit.</span><span class="sxs-lookup"><span data-stu-id="0bf47-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="0bf47-126">Když zadáte typ Správce aplikační domény pro výchozí doménu aplikace, ostatní domény aplikace vytvořené z výchozí domény aplikace zdědí typ Správce aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="0bf47-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="0bf47-127">Pomocí vlastností <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> určete jiný typ Správce aplikační domény pro novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0bf47-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="0bf47-128">Zadání typu správce aplikační domény vyžaduje, aby aplikace měla úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="0bf47-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="0bf47-129">(Například aplikace spuštěná na ploše má úplný vztah důvěryhodnosti.) Pokud aplikace nemá úplný vztah důvěryhodnosti, je vyvolána <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="0bf47-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="0bf47-130">Formát typu a oboru názvů je stejný formát, který se používá pro vlastnost <xref:System.Type.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0bf47-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="0bf47-131">Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="0bf47-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bf47-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="0bf47-132">Example</span></span>  
 <span data-ttu-id="0bf47-133">Následující příklad ukazuje, jak určit, že správce aplikační domény pro výchozí doménu aplikace v procesu je typ `MyMgr` v sestavení `AdMgrExample`.</span><span class="sxs-lookup"><span data-stu-id="0bf47-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0bf47-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bf47-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0bf47-135">\<element > appDomainManagerAssembly</span><span class="sxs-lookup"><span data-stu-id="0bf47-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="0bf47-136">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="0bf47-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0bf47-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0bf47-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0bf47-138">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="0bf47-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
