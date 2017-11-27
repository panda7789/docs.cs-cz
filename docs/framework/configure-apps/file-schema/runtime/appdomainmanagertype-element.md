---
title: "&lt;appdomainmanagertype –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 56d68efe176540ba82ec7b86f35678905ebc970b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltappdomainmanagertypegt-element"></a><span data-ttu-id="f4c47-102">&lt;appdomainmanagertype –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="f4c47-102">&lt;appDomainManagerType&gt; Element</span></span>
<span data-ttu-id="f4c47-103">Určuje typ, který slouží jako správce domény aplikace pro výchozí doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4c47-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
 <span data-ttu-id="f4c47-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="f4c47-104">\<configuration></span></span>  
<span data-ttu-id="f4c47-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="f4c47-105">\<runtime></span></span>  
<span data-ttu-id="f4c47-106">\<appdomainmanagertype – ></span><span class="sxs-lookup"><span data-stu-id="f4c47-106">\<appDomainManagerType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4c47-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4c47-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4c47-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f4c47-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f4c47-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f4c47-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4c47-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f4c47-110">Attributes</span></span>  
  
|<span data-ttu-id="f4c47-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f4c47-111">Attribute</span></span>|<span data-ttu-id="f4c47-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f4c47-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="f4c47-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f4c47-113">Required attribute.</span></span> <span data-ttu-id="f4c47-114">Určuje název typu včetně oboru názvů, který slouží jako správce domény aplikace pro výchozí doméně aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="f4c47-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4c47-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f4c47-115">Child Elements</span></span>  
 <span data-ttu-id="f4c47-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="f4c47-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4c47-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f4c47-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f4c47-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="f4c47-118">Element</span></span>|<span data-ttu-id="f4c47-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f4c47-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f4c47-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4c47-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f4c47-121">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f4c47-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4c47-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4c47-122">Remarks</span></span>  
 <span data-ttu-id="f4c47-123">Zadejte typ správce domény aplikace, je nutné zadat obě tento prvek a [ \<appdomainmanagerassembly – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="f4c47-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="f4c47-124">Pokud některý z těchto elementů není zadán, dalších ignorovat.</span><span class="sxs-lookup"><span data-stu-id="f4c47-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="f4c47-125">Při načítání výchozí doméně aplikace <xref:System.TypeLoadException> je vyvolána, pokud zadaný typ neexistuje v sestavení, která je zadána [ \<appdomainmanagerassembly – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element; a nepodaří procesu spustíte.</span><span class="sxs-lookup"><span data-stu-id="f4c47-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="f4c47-126">Když zadáte typ správce domény aplikace pro výchozí doménu aplikace, dědí jiných domén aplikace vytvořena z výchozí doméně aplikace typ správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4c47-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="f4c47-127">Použití <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> vlastnosti, které chcete zadat jinou aplikaci typ správce domény pro novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4c47-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="f4c47-128">Určení typu správce domény aplikace vyžaduje aplikací mít úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="f4c47-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="f4c47-129">(Například aplikace běžící v desktopovém má úplný vztah důvěryhodnosti.) Pokud aplikace nemá úplný vztah důvěryhodnosti, <xref:System.TypeLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="f4c47-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="f4c47-130">Formát typu a obor názvů je stejný formát, který se používá pro <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f4c47-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="f4c47-131">Tento element konfigurace je k dispozici pouze v [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] a novější.</span><span class="sxs-lookup"><span data-stu-id="f4c47-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4c47-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4c47-132">Example</span></span>  
 <span data-ttu-id="f4c47-133">Následující příklad ukazuje, jak určit, že je správce domény aplikace pro doménu aplikace výchozí procesu `MyMgr` zadejte `AdMgrExample` sestavení.</span><span class="sxs-lookup"><span data-stu-id="f4c47-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4c47-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4c47-134">See Also</span></span>  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f4c47-135">\<appdomainmanagerassembly – > elementu</span><span class="sxs-lookup"><span data-stu-id="f4c47-135">\<appDomainManagerAssembly> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)  
 [<span data-ttu-id="f4c47-136">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="f4c47-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="f4c47-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f4c47-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f4c47-138">Setappdomainmanagertype – metoda</span><span class="sxs-lookup"><span data-stu-id="f4c47-138">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
