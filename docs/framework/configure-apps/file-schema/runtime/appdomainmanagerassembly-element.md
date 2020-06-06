---
title: Element <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154420"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="46916-102">Element \<appDomainManagerAssembly></span><span class="sxs-lookup"><span data-stu-id="46916-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="46916-103">Určuje sestavení, které poskytuje správce aplikační domény pro výchozí doménu aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="46916-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="46916-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46916-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46916-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="46916-105">Attributes and Elements</span></span>  
 <span data-ttu-id="46916-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="46916-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46916-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="46916-107">Attributes</span></span>  
  
|<span data-ttu-id="46916-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="46916-108">Attribute</span></span>|<span data-ttu-id="46916-109">Popis</span><span class="sxs-lookup"><span data-stu-id="46916-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="46916-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="46916-110">Required attribute.</span></span> <span data-ttu-id="46916-111">Určuje zobrazovaný název sestavení, které poskytuje správce aplikační domény pro výchozí doménu aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="46916-111">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46916-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="46916-112">Child Elements</span></span>  
 <span data-ttu-id="46916-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="46916-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46916-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="46916-114">Parent Elements</span></span>  
  
|<span data-ttu-id="46916-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="46916-115">Element</span></span>|<span data-ttu-id="46916-116">Description</span><span class="sxs-lookup"><span data-stu-id="46916-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="46916-117">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46916-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="46916-118">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="46916-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46916-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46916-119">Remarks</span></span>  
 <span data-ttu-id="46916-120">Chcete-li zadat typ Správce aplikační domény, je nutné zadat jak tento prvek, tak i [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="46916-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="46916-121">Pokud některý z těchto prvků není zadán, druhá je ignorována.</span><span class="sxs-lookup"><span data-stu-id="46916-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="46916-122">Pokud je výchozí doména aplikace načtena, <xref:System.TypeLoadException> je vyvolána, pokud zadané sestavení neexistuje nebo pokud sestavení neobsahuje typ určený [\<appDomainManagerType>](appdomainmanagertype-element.md) elementem a proces se nepovede spustit.</span><span class="sxs-lookup"><span data-stu-id="46916-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="46916-123">Pokud je sestavení nalezeno, ale informace o verzi se neshodují, <xref:System.IO.FileLoadException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="46916-123">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="46916-124">Když zadáte typ Správce aplikační domény pro výchozí doménu aplikace, ostatní domény aplikace vytvořené z výchozí domény aplikace zdědí typ Správce aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="46916-124">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="46916-125">Pomocí <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> vlastností a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> určete jiný typ Správce aplikační domény pro novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="46916-125">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="46916-126">Zadání typu správce aplikační domény vyžaduje, aby aplikace měla úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="46916-126">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="46916-127">(Například aplikace spuštěná na ploše má úplný vztah důvěryhodnosti.) Pokud aplikace nemá úplný vztah důvěryhodnosti, <xref:System.TypeLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="46916-127">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="46916-128">Pro formát zobrazovaného názvu sestavení se podívejte na <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="46916-128">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="46916-129">Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="46916-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46916-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="46916-130">Example</span></span>  
 <span data-ttu-id="46916-131">Následující příklad ukazuje, jak určit, že správce aplikační domény pro výchozí doménu aplikace v procesu je `MyMgr` typ v `AdMgrExample` sestavení.</span><span class="sxs-lookup"><span data-stu-id="46916-131">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="46916-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="46916-132">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="46916-133">\<appDomainManagerType>Objekt</span><span class="sxs-lookup"><span data-stu-id="46916-133">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="46916-134">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="46916-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="46916-135">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="46916-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="46916-136">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="46916-136">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
