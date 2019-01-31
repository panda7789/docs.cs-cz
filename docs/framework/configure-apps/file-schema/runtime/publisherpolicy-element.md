---
title: Element <publisherPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be87c91b798256f3913779bdbe36f3548066018b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55253935"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="a1d93-102">\<publisherPolicy > – Element</span><span class="sxs-lookup"><span data-stu-id="a1d93-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="a1d93-103">Určuje, zda modul runtime použije zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="a1d93-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="a1d93-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a1d93-104">\<configuration></span></span>  
<span data-ttu-id="a1d93-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="a1d93-105">\<runtime></span></span>  
<span data-ttu-id="a1d93-106">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="a1d93-106">\<assemblyBinding></span></span>  
<span data-ttu-id="a1d93-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="a1d93-107">\<dependentAssembly></span></span>  
<span data-ttu-id="a1d93-108">\<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="a1d93-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1d93-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1d93-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1d93-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a1d93-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a1d93-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a1d93-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1d93-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a1d93-112">Attributes</span></span>  
  
|<span data-ttu-id="a1d93-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a1d93-113">Attribute</span></span>|<span data-ttu-id="a1d93-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a1d93-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="a1d93-115">Určuje, jestli se má použít zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="a1d93-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="a1d93-116">použít atribut</span><span class="sxs-lookup"><span data-stu-id="a1d93-116">apply Attribute</span></span>  
  
|<span data-ttu-id="a1d93-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a1d93-117">Value</span></span>|<span data-ttu-id="a1d93-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a1d93-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="a1d93-119">Použije zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="a1d93-119">Applies publisher policy.</span></span> <span data-ttu-id="a1d93-120">Toto je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="a1d93-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="a1d93-121">Doporučení se netýká zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="a1d93-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1d93-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a1d93-122">Child Elements</span></span>  
 <span data-ttu-id="a1d93-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="a1d93-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1d93-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a1d93-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a1d93-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="a1d93-125">Element</span></span>|<span data-ttu-id="a1d93-126">Popis</span><span class="sxs-lookup"><span data-stu-id="a1d93-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a1d93-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1d93-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a1d93-128">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a1d93-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1d93-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1d93-129">Remarks</span></span>  
 <span data-ttu-id="a1d93-130">Při vydání nové verze sestavení dodavatele součástí můžete dodavatele obsahují zásad vydavatele, takže aplikace, které používají starší verzi nyní používat novou verzi.</span><span class="sxs-lookup"><span data-stu-id="a1d93-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="a1d93-131">Chcete-li určit, jestli se má použít pro konkrétní sestavení zásad vydavatele, umístěte  **\<publisherPolicy >** prvek  **\<dependentAssembly >** element.</span><span class="sxs-lookup"><span data-stu-id="a1d93-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="a1d93-132">Ve výchozím nastavení **použít** atribut je **Ano**.</span><span class="sxs-lookup"><span data-stu-id="a1d93-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="a1d93-133">Nastavení **použít** atribut **žádné** přepíše jakékoli předchozí **Ano** nastavení sestavení.</span><span class="sxs-lookup"><span data-stu-id="a1d93-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="a1d93-134">Oprávnění je požadováno pro aplikace explicitně ignorovat pomocí zásady vydavatele [ \<publisherPolicy použít = "žádný" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) prvku v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1d93-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="a1d93-135">Oprávnění je udělován nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="a1d93-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="a1d93-136">Další informace najdete v tématu [sestavení oprávnění zabezpečení přesměrování vazby](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="a1d93-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1d93-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1d93-137">Example</span></span>  
 <span data-ttu-id="a1d93-138">Následující příklad vypne zásady vydavatele pro sestavení, `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="a1d93-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1d93-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1d93-139">See also</span></span>
- [<span data-ttu-id="a1d93-140">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="a1d93-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="a1d93-141">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a1d93-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="a1d93-142">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="a1d93-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="a1d93-143">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="a1d93-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
