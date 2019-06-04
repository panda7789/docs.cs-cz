---
title: Element <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff8c91680a0c3049fa9bc2f7e9c1bf3f654a19b9
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487769"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="4d0e2-102">\<appDomainManagerAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="4d0e2-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="4d0e2-103">Určuje sestavení, které poskytuje správce domény aplikace ve výchozí doméně aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
 <span data-ttu-id="4d0e2-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="4d0e2-104">\<configuration></span></span>  
<span data-ttu-id="4d0e2-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="4d0e2-105">\<runtime></span></span>  
<span data-ttu-id="4d0e2-106">\<appDomainManagerAssembly></span><span class="sxs-lookup"><span data-stu-id="4d0e2-106">\<appDomainManagerAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d0e2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d0e2-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d0e2-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4d0e2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4d0e2-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d0e2-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="4d0e2-110">Attributes</span></span>  
  
|<span data-ttu-id="4d0e2-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="4d0e2-111">Attribute</span></span>|<span data-ttu-id="4d0e2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="4d0e2-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="4d0e2-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-113">Required attribute.</span></span> <span data-ttu-id="4d0e2-114">Určuje zobrazovaný název sestavení, které poskytuje správce domény aplikace ve výchozí doméně aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d0e2-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4d0e2-115">Child Elements</span></span>  
 <span data-ttu-id="4d0e2-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="4d0e2-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d0e2-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4d0e2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4d0e2-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d0e2-118">Element</span></span>|<span data-ttu-id="4d0e2-119">Popis</span><span class="sxs-lookup"><span data-stu-id="4d0e2-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4d0e2-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4d0e2-121">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d0e2-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d0e2-122">Remarks</span></span>  
 <span data-ttu-id="4d0e2-123">Chcete-li určit typ správce domény aplikace, je nutné zadat obě tento element a [ \<appdomainmanagertype – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="4d0e2-124">Pokud některý z těchto prvků není zadán, druhý se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="4d0e2-125">Při načítání výchozí domény aplikace <xref:System.TypeLoadException> je vyvolána, pokud zadané sestavení neexistuje, nebo pokud sestavení neobsahuje typ zadaný [ \<appdomainmanagertype – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; a proces se nedaří spustit.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="4d0e2-126">Pokud je sestavení nalezeno, ale informace o verzi neodpovídá, <xref:System.IO.FileLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="4d0e2-127">Když zadáte typ správce domény aplikace výchozí aplikační domény, dědí jiných domén aplikace vytvořené z výchozí domény aplikace typ správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="4d0e2-128">Použití <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> vlastnosti zadat typ správce různých aplikační domény pro novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="4d0e2-129">Určení typu správce domény aplikace vyžaduje, aby aplikace mít plnou důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="4d0e2-130">(Například aplikace běžící v desktopovém má úplný vztah důvěryhodnosti.) Pokud aplikace nemá plnou důvěryhodnost <xref:System.TypeLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="4d0e2-131">Formát zobrazovaný název sestavení, najdete v článku <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="4d0e2-132">Tento prvek konfigurace je k dispozici pouze v rozhraní .NET Framework 4 a novější.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-132">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d0e2-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d0e2-133">Example</span></span>  
 <span data-ttu-id="4d0e2-134">Následující příklad ukazuje, jak určit, že je aplikace správce domény pro doménu aplikace výchozí procesu `MyMgr` zadejte `AdMgrExample` sestavení.</span><span class="sxs-lookup"><span data-stu-id="4d0e2-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d0e2-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d0e2-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4d0e2-136">\<appDomainManagerType> Element</span><span class="sxs-lookup"><span data-stu-id="4d0e2-136">\<appDomainManagerType> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)
- [<span data-ttu-id="4d0e2-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="4d0e2-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="4d0e2-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="4d0e2-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="4d0e2-139">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="4d0e2-139">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
