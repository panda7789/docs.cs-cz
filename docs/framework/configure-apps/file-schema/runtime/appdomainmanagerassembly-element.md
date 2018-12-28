---
title: '&lt;appdomainmanagerassembly –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23c0edd99d09417c8e657045407a02a07338d7b2
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610187"
---
# <a name="ltappdomainmanagerassemblygt-element"></a><span data-ttu-id="374ac-102">&lt;appdomainmanagerassembly –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="374ac-102">&lt;appDomainManagerAssembly&gt; Element</span></span>
<span data-ttu-id="374ac-103">Určuje sestavení, které poskytuje správce domény aplikace ve výchozí doméně aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="374ac-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
 <span data-ttu-id="374ac-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="374ac-104">\<configuration></span></span>  
<span data-ttu-id="374ac-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="374ac-105">\<runtime></span></span>  
<span data-ttu-id="374ac-106">\<appdomainmanagerassembly – ></span><span class="sxs-lookup"><span data-stu-id="374ac-106">\<appDomainManagerAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="374ac-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="374ac-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="374ac-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="374ac-108">Attributes and Elements</span></span>  
 <span data-ttu-id="374ac-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="374ac-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="374ac-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="374ac-110">Attributes</span></span>  
  
|<span data-ttu-id="374ac-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="374ac-111">Attribute</span></span>|<span data-ttu-id="374ac-112">Popis</span><span class="sxs-lookup"><span data-stu-id="374ac-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="374ac-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="374ac-113">Required attribute.</span></span> <span data-ttu-id="374ac-114">Určuje zobrazovaný název sestavení, které poskytuje správce domény aplikace ve výchozí doméně aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="374ac-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="374ac-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="374ac-115">Child Elements</span></span>  
 <span data-ttu-id="374ac-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="374ac-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="374ac-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="374ac-117">Parent Elements</span></span>  
  
|<span data-ttu-id="374ac-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="374ac-118">Element</span></span>|<span data-ttu-id="374ac-119">Popis</span><span class="sxs-lookup"><span data-stu-id="374ac-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="374ac-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="374ac-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="374ac-121">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="374ac-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="374ac-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="374ac-122">Remarks</span></span>  
 <span data-ttu-id="374ac-123">Chcete-li určit typ správce domény aplikace, je nutné zadat obě tento element a [ \<appdomainmanagertype – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="374ac-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="374ac-124">Pokud některý z těchto prvků není zadán, druhý se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="374ac-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="374ac-125">Při načítání výchozí domény aplikace <xref:System.TypeLoadException> je vyvolána, pokud zadané sestavení neexistuje, nebo pokud sestavení neobsahuje typ zadaný [ \<appdomainmanagertype – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; a proces se nedaří spustit.</span><span class="sxs-lookup"><span data-stu-id="374ac-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="374ac-126">Pokud je sestavení nalezeno, ale informace o verzi neodpovídá, <xref:System.IO.FileLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="374ac-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="374ac-127">Když zadáte typ správce domény aplikace výchozí aplikační domény, dědí jiných domén aplikace vytvořené z výchozí domény aplikace typ správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="374ac-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="374ac-128">Použití <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> vlastnosti zadat typ správce různých aplikační domény pro novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="374ac-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="374ac-129">Určení typu správce domény aplikace vyžaduje, aby aplikace mít plnou důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="374ac-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="374ac-130">(Například aplikace běžící v desktopovém má úplný vztah důvěryhodnosti.) Pokud aplikace nemá plnou důvěryhodnost <xref:System.TypeLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="374ac-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="374ac-131">Formát zobrazovaný název sestavení, najdete v článku <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="374ac-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="374ac-132">Tento prvek konfigurace je k dispozici pouze v [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] a novější.</span><span class="sxs-lookup"><span data-stu-id="374ac-132">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="374ac-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="374ac-133">Example</span></span>  
 <span data-ttu-id="374ac-134">Následující příklad ukazuje, jak určit, že je aplikace správce domény pro doménu aplikace výchozí procesu `MyMgr` zadejte `AdMgrExample` sestavení.</span><span class="sxs-lookup"><span data-stu-id="374ac-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="374ac-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="374ac-135">See Also</span></span>  
- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="374ac-136">\<appdomainmanagertype – > – Element</span><span class="sxs-lookup"><span data-stu-id="374ac-136">\<appDomainManagerType> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)  
- [<span data-ttu-id="374ac-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="374ac-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="374ac-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="374ac-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="374ac-139">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="374ac-139">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
