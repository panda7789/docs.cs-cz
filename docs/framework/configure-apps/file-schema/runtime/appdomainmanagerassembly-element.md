---
title: Element <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154420"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="9b344-102">\<appDomainManagerAssembly> Element</span><span class="sxs-lookup"><span data-stu-id="9b344-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="9b344-103">Určuje sestavení, které poskytuje správce domény aplikace pro výchozí doménu aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="9b344-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
<span data-ttu-id="9b344-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b344-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9b344-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b344-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="9b344-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span><span class="sxs-lookup"><span data-stu-id="9b344-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b344-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b344-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b344-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9b344-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9b344-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9b344-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b344-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="9b344-110">Attributes</span></span>  
  
|<span data-ttu-id="9b344-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="9b344-111">Attribute</span></span>|<span data-ttu-id="9b344-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9b344-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="9b344-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9b344-113">Required attribute.</span></span> <span data-ttu-id="9b344-114">Určuje zobrazovaný název sestavení, které poskytuje správce domény aplikace pro výchozí doménu aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="9b344-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b344-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9b344-115">Child Elements</span></span>  
 <span data-ttu-id="9b344-116">Žádné.</span><span class="sxs-lookup"><span data-stu-id="9b344-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b344-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9b344-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9b344-118">Element</span><span class="sxs-lookup"><span data-stu-id="9b344-118">Element</span></span>|<span data-ttu-id="9b344-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9b344-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9b344-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b344-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9b344-121">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9b344-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b344-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b344-122">Remarks</span></span>  
 <span data-ttu-id="9b344-123">Chcete-li určit typ správce domény aplikace, musíte zadat tento prvek i>element [ \<appDomainManagerType.](appdomainmanagertype-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b344-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="9b344-124">Pokud některý z těchto prvků není zadán, druhý je ignorován.</span><span class="sxs-lookup"><span data-stu-id="9b344-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="9b344-125">Při načtení výchozí domény <xref:System.TypeLoadException> aplikace je vyvolána, pokud zadané sestavení neexistuje nebo pokud sestavení neobsahuje typ určený [ \<prvkem appDomainManagerType>;](appdomainmanagertype-element.md) a proces se nespustí.</span><span class="sxs-lookup"><span data-stu-id="9b344-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="9b344-126">Pokud je sestavení nalezeno, ale informace o <xref:System.IO.FileLoadException> verzi se neshodují, je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="9b344-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="9b344-127">Pokud zadáte typ správce domény aplikace pro výchozí doménu aplikace, ostatní domény aplikace vytvořené z výchozí aplikační domény zdědí typ správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b344-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="9b344-128">Pomocí <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> vlastností a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> určete jiný typ správce domény aplikace pro novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b344-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="9b344-129">Určení typu správce domény aplikace vyžaduje, aby aplikace měla úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="9b344-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="9b344-130">(Například aplikace spuštěná na ploše má plnou důvěryhodnost.) Pokud aplikace nemá úplný vztah <xref:System.TypeLoadException> důvěryhodnosti, je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="9b344-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="9b344-131">Formát zobrazovaného názvu sestavení naleznete <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> ve vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9b344-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="9b344-132">Tento konfigurační prvek je k dispozici pouze v rozhraní .NET Framework 4 a novější.</span><span class="sxs-lookup"><span data-stu-id="9b344-132">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b344-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b344-133">Example</span></span>  
 <span data-ttu-id="9b344-134">Následující příklad ukazuje, jak určit, že správce domény aplikace pro `MyMgr` výchozí aplikační `AdMgrExample` doménu procesu je typ v sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b344-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b344-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b344-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9b344-136">\<appDomainManagerType> element</span><span class="sxs-lookup"><span data-stu-id="9b344-136">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="9b344-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="9b344-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9b344-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9b344-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9b344-139">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="9b344-139">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
