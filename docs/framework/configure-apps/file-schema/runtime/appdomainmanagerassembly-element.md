---
title: Element <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 083e3ba21dcd196eacfe3d9fd649c211da9dc125
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252853"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="f87d7-102">\<appDomainManagerAssembly – element ></span><span class="sxs-lookup"><span data-stu-id="f87d7-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="f87d7-103">Určuje sestavení, které poskytuje správce aplikační domény pro výchozí doménu aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="f87d7-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
<span data-ttu-id="f87d7-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f87d7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f87d7-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="f87d7-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="f87d7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerAssembly>**</span><span class="sxs-lookup"><span data-stu-id="f87d7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f87d7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f87d7-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f87d7-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f87d7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f87d7-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f87d7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f87d7-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f87d7-110">Attributes</span></span>  
  
|<span data-ttu-id="f87d7-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f87d7-111">Attribute</span></span>|<span data-ttu-id="f87d7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f87d7-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="f87d7-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f87d7-113">Required attribute.</span></span> <span data-ttu-id="f87d7-114">Určuje zobrazovaný název sestavení, které poskytuje správce aplikační domény pro výchozí doménu aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="f87d7-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f87d7-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f87d7-115">Child Elements</span></span>  
 <span data-ttu-id="f87d7-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="f87d7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f87d7-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f87d7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f87d7-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="f87d7-118">Element</span></span>|<span data-ttu-id="f87d7-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f87d7-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f87d7-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f87d7-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f87d7-121">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f87d7-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f87d7-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f87d7-122">Remarks</span></span>  
 <span data-ttu-id="f87d7-123">Chcete-li zadat typ Správce aplikační domény, je nutné zadat jak tento prvek, tak [ \<i prvek appDomainManagerType >](appdomainmanagertype-element.md) .</span><span class="sxs-lookup"><span data-stu-id="f87d7-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="f87d7-124">Pokud některý z těchto prvků není zadán, druhá je ignorována.</span><span class="sxs-lookup"><span data-stu-id="f87d7-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="f87d7-125">Když je načtena výchozí doména aplikace, <xref:System.TypeLoadException> je vyvolána, pokud zadané sestavení neexistuje nebo pokud sestavení neobsahuje typ určený [ \<prvkem appDomainManagerType >](appdomainmanagertype-element.md) ; a proces se nezdařil. Čína.</span><span class="sxs-lookup"><span data-stu-id="f87d7-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="f87d7-126">Pokud je sestavení nalezeno, ale informace o verzi se neshodují, <xref:System.IO.FileLoadException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f87d7-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="f87d7-127">Když zadáte typ Správce aplikační domény pro výchozí doménu aplikace, ostatní domény aplikace vytvořené z výchozí domény aplikace zdědí typ Správce aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="f87d7-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="f87d7-128">Pomocí vlastností <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> a určete jiný typ Správce aplikační domény pro novou doménu aplikace. <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f87d7-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="f87d7-129">Zadání typu správce aplikační domény vyžaduje, aby aplikace měla úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="f87d7-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="f87d7-130">(Například aplikace spuštěná na ploše má úplný vztah důvěryhodnosti.) Pokud aplikace nemá úplný vztah důvěryhodnosti, <xref:System.TypeLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="f87d7-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="f87d7-131">Pro formát zobrazovaného názvu sestavení se podívejte na <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f87d7-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="f87d7-132">Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="f87d7-132">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f87d7-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="f87d7-133">Example</span></span>  
 <span data-ttu-id="f87d7-134">Následující příklad ukazuje, jak určit, že správce aplikační domény pro výchozí doménu aplikace v procesu je `MyMgr` typ `AdMgrExample` v sestavení.</span><span class="sxs-lookup"><span data-stu-id="f87d7-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f87d7-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f87d7-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f87d7-136">\<appDomainManagerType> Element</span><span class="sxs-lookup"><span data-stu-id="f87d7-136">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="f87d7-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="f87d7-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f87d7-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f87d7-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f87d7-139">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="f87d7-139">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
