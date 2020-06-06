---
title: Element <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154421"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="9587f-102">Element \<appDomainManagerType></span><span class="sxs-lookup"><span data-stu-id="9587f-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="9587f-103">Určuje typ, který slouží jako správce aplikační domény pro výchozí doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9587f-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
## <a name="syntax"></a><span data-ttu-id="9587f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9587f-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9587f-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9587f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9587f-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9587f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9587f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="9587f-107">Attributes</span></span>  
  
|<span data-ttu-id="9587f-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="9587f-108">Attribute</span></span>|<span data-ttu-id="9587f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9587f-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="9587f-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9587f-110">Required attribute.</span></span> <span data-ttu-id="9587f-111">Určuje název typu, včetně oboru názvů, který slouží jako správce aplikační domény pro výchozí doménu aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="9587f-111">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9587f-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9587f-112">Child Elements</span></span>  
 <span data-ttu-id="9587f-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="9587f-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9587f-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9587f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="9587f-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="9587f-115">Element</span></span>|<span data-ttu-id="9587f-116">Description</span><span class="sxs-lookup"><span data-stu-id="9587f-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9587f-117">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9587f-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9587f-118">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9587f-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9587f-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9587f-119">Remarks</span></span>  
 <span data-ttu-id="9587f-120">Chcete-li zadat typ Správce aplikační domény, je nutné zadat jak tento prvek, tak i [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="9587f-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="9587f-121">Pokud některý z těchto prvků není zadán, druhá je ignorována.</span><span class="sxs-lookup"><span data-stu-id="9587f-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="9587f-122">V případě, že je načtena výchozí doména aplikace, <xref:System.TypeLoadException> je vyvolána, pokud zadaný typ neexistuje v sestavení určeném [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) elementem a proces se nepodařilo spustit.</span><span class="sxs-lookup"><span data-stu-id="9587f-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="9587f-123">Když zadáte typ Správce aplikační domény pro výchozí doménu aplikace, ostatní domény aplikace vytvořené z výchozí domény aplikace zdědí typ Správce aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="9587f-123">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="9587f-124">Pomocí <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> vlastností a <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> určete jiný typ Správce aplikační domény pro novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9587f-124">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="9587f-125">Zadání typu správce aplikační domény vyžaduje, aby aplikace měla úplný vztah důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="9587f-125">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="9587f-126">(Například aplikace spuštěná na ploše má úplný vztah důvěryhodnosti.) Pokud aplikace nemá úplný vztah důvěryhodnosti, <xref:System.TypeLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9587f-126">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="9587f-127">Formát typu a oboru názvů je stejný formát, který se používá pro <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9587f-127">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="9587f-128">Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="9587f-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9587f-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="9587f-129">Example</span></span>  
 <span data-ttu-id="9587f-130">Následující příklad ukazuje, jak určit, že správce aplikační domény pro výchozí doménu aplikace v procesu je `MyMgr` typ v `AdMgrExample` sestavení.</span><span class="sxs-lookup"><span data-stu-id="9587f-130">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9587f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="9587f-131">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9587f-132">\<appDomainManagerAssembly>Objekt</span><span class="sxs-lookup"><span data-stu-id="9587f-132">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="9587f-133">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="9587f-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9587f-134">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9587f-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9587f-135">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="9587f-135">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
