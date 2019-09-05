---
title: Element <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ffb297cc38f20917e720b216607e9ccfc966866
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252834"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="db009-102">\<appDomainManagerType> Element</span><span class="sxs-lookup"><span data-stu-id="db009-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="db009-103">Určuje typ, který slouží jako správce aplikační domény pro výchozí doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="db009-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
<span data-ttu-id="db009-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="db009-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="db009-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="db009-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="db009-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerType>**</span><span class="sxs-lookup"><span data-stu-id="db009-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db009-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db009-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db009-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="db009-108">Attributes and Elements</span></span>  
 <span data-ttu-id="db009-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="db009-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db009-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="db009-110">Attributes</span></span>  
  
|<span data-ttu-id="db009-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="db009-111">Attribute</span></span>|<span data-ttu-id="db009-112">Popis</span><span class="sxs-lookup"><span data-stu-id="db009-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="db009-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="db009-113">Required attribute.</span></span> <span data-ttu-id="db009-114">Určuje název typu, včetně oboru názvů, který slouží jako správce aplikační domény pro výchozí doménu aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="db009-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db009-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="db009-115">Child Elements</span></span>  
 <span data-ttu-id="db009-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="db009-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db009-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="db009-117">Parent Elements</span></span>  
  
|<span data-ttu-id="db009-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="db009-118">Element</span></span>|<span data-ttu-id="db009-119">Popis</span><span class="sxs-lookup"><span data-stu-id="db009-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="db009-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db009-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="db009-121">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="db009-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db009-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db009-122">Remarks</span></span>  
 <span data-ttu-id="db009-123">Chcete-li zadat typ Správce aplikační domény, je nutné zadat jak tento prvek, tak [ \<i prvek appDomainManagerAssembly >](appdomainmanagerassembly-element.md) .</span><span class="sxs-lookup"><span data-stu-id="db009-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="db009-124">Pokud některý z těchto prvků není zadán, druhá je ignorována.</span><span class="sxs-lookup"><span data-stu-id="db009-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="db009-125">Pokud je výchozí aplikační doména načtena, <xref:System.TypeLoadException> je vyvolána, pokud zadaný typ neexistuje v sestavení určeném [ \<prvkem appDomainManagerAssembly >](appdomainmanagerassembly-element.md) ; a proces se nespustí.</span><span class="sxs-lookup"><span data-stu-id="db009-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="db009-126">Když zadáte typ Správce aplikační domény pro výchozí doménu aplikace, ostatní domény aplikace vytvořené z výchozí domény aplikace zdědí typ Správce aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="db009-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="db009-127">Pomocí vlastností <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> a určete jiný typ Správce aplikační domény pro novou doménu aplikace. <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="db009-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="db009-128">Zadání typu správce aplikační domény vyžaduje, aby aplikace měla úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="db009-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="db009-129">(Například aplikace spuštěná na ploše má úplný vztah důvěryhodnosti.) Pokud aplikace nemá úplný vztah důvěryhodnosti, <xref:System.TypeLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="db009-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="db009-130">Formát typu a oboru názvů je stejný formát, který se používá pro <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="db009-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="db009-131">Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="db009-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db009-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="db009-132">Example</span></span>  
 <span data-ttu-id="db009-133">Následující příklad ukazuje, jak určit, že správce aplikační domény pro výchozí doménu aplikace v procesu je `MyMgr` typ `AdMgrExample` v sestavení.</span><span class="sxs-lookup"><span data-stu-id="db009-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="db009-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db009-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="db009-135">\<appDomainManagerAssembly – element ></span><span class="sxs-lookup"><span data-stu-id="db009-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="db009-136">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="db009-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="db009-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="db009-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="db009-138">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="db009-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
