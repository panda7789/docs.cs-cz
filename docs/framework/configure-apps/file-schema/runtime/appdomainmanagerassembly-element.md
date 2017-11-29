---
title: "&lt;appdomainmanagerassembly –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e07b7bd18f19439f64ed8eaef5bda3bad5cef77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltappdomainmanagerassemblygt-element"></a><span data-ttu-id="9676a-102">&lt;appdomainmanagerassembly –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="9676a-102">&lt;appDomainManagerAssembly&gt; Element</span></span>
<span data-ttu-id="9676a-103">Určuje sestavení, které poskytuje správce domény aplikace pro výchozí doméně aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="9676a-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
 <span data-ttu-id="9676a-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="9676a-104">\<configuration></span></span>  
<span data-ttu-id="9676a-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="9676a-105">\<runtime></span></span>  
<span data-ttu-id="9676a-106">\<appdomainmanagerassembly – ></span><span class="sxs-lookup"><span data-stu-id="9676a-106">\<appDomainManagerAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9676a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9676a-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9676a-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9676a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9676a-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9676a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9676a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="9676a-110">Attributes</span></span>  
  
|<span data-ttu-id="9676a-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="9676a-111">Attribute</span></span>|<span data-ttu-id="9676a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9676a-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="9676a-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9676a-113">Required attribute.</span></span> <span data-ttu-id="9676a-114">Určuje zobrazovaný název sestavení, které poskytuje správce domény aplikace pro výchozí doméně aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="9676a-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9676a-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9676a-115">Child Elements</span></span>  
 <span data-ttu-id="9676a-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="9676a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9676a-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9676a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9676a-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="9676a-118">Element</span></span>|<span data-ttu-id="9676a-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9676a-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9676a-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9676a-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9676a-121">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9676a-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9676a-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9676a-122">Remarks</span></span>  
 <span data-ttu-id="9676a-123">Zadejte typ správce domény aplikace, je nutné zadat obě tento prvek a [ \<appdomainmanagertype – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="9676a-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="9676a-124">Pokud některý z těchto elementů není zadán, dalších ignorovat.</span><span class="sxs-lookup"><span data-stu-id="9676a-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="9676a-125">Při načítání výchozí doméně aplikace <xref:System.TypeLoadException> je vyvolána, pokud zadané sestavení neexistuje, nebo pokud sestavení neobsahuje v typu zadaném pomocí [ \<appdomainmanagertype – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; a proces se nepodaří spustit.</span><span class="sxs-lookup"><span data-stu-id="9676a-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="9676a-126">Pokud se najde sestavení, ale informace o verzi neodpovídá, <xref:System.IO.FileLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9676a-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="9676a-127">Když zadáte typ správce domény aplikace pro výchozí doménu aplikace, dědí jiných domén aplikace vytvořena z výchozí doméně aplikace typ správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9676a-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="9676a-128">Použití <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> vlastnosti, které chcete zadat jinou aplikaci typ správce domény pro novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9676a-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="9676a-129">Určení typu správce domény aplikace vyžaduje aplikací mít úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="9676a-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="9676a-130">(Například aplikace běžící v desktopovém má úplný vztah důvěryhodnosti.) Pokud aplikace nemá úplný vztah důvěryhodnosti, <xref:System.TypeLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9676a-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="9676a-131">Formát zobrazovaný název sestavení, najdete v článku <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9676a-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="9676a-132">Tento element konfigurace je k dispozici pouze v [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] a novější.</span><span class="sxs-lookup"><span data-stu-id="9676a-132">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9676a-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="9676a-133">Example</span></span>  
 <span data-ttu-id="9676a-134">Následující příklad ukazuje, jak určit, že je správce domény aplikace pro doménu aplikace výchozí procesu `MyMgr` zadejte `AdMgrExample` sestavení.</span><span class="sxs-lookup"><span data-stu-id="9676a-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9676a-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="9676a-135">See Also</span></span>  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="9676a-136">\<appdomainmanagertype – > elementu</span><span class="sxs-lookup"><span data-stu-id="9676a-136">\<appDomainManagerType> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)  
 [<span data-ttu-id="9676a-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="9676a-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="9676a-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9676a-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="9676a-139">Setappdomainmanagertype – metoda</span><span class="sxs-lookup"><span data-stu-id="9676a-139">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
