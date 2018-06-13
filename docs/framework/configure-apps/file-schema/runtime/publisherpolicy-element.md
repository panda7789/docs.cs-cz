---
title: '&lt;publisherPolicy&gt; – Element'
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
ms.openlocfilehash: 2cc3b7220fe34f5dc049a3da71b160a88f82fdb1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746095"
---
# <a name="ltpublisherpolicygt-element"></a><span data-ttu-id="ecd80-102">&lt;publisherPolicy&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="ecd80-102">&lt;publisherPolicy&gt; Element</span></span>
<span data-ttu-id="ecd80-103">Určuje, zda modul runtime aplikuje zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="ecd80-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="ecd80-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="ecd80-104">\<configuration></span></span>  
<span data-ttu-id="ecd80-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="ecd80-105">\<runtime></span></span>  
<span data-ttu-id="ecd80-106">\<assemblybinding – ></span><span class="sxs-lookup"><span data-stu-id="ecd80-106">\<assemblyBinding></span></span>  
<span data-ttu-id="ecd80-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="ecd80-107">\<dependentAssembly></span></span>  
<span data-ttu-id="ecd80-108">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="ecd80-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecd80-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecd80-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecd80-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ecd80-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ecd80-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ecd80-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecd80-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="ecd80-112">Attributes</span></span>  
  
|<span data-ttu-id="ecd80-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="ecd80-113">Attribute</span></span>|<span data-ttu-id="ecd80-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ecd80-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="ecd80-115">Určuje, jestli použít zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="ecd80-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="ecd80-116">použití atributů</span><span class="sxs-lookup"><span data-stu-id="ecd80-116">apply Attribute</span></span>  
  
|<span data-ttu-id="ecd80-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ecd80-117">Value</span></span>|<span data-ttu-id="ecd80-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ecd80-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="ecd80-119">Platí zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="ecd80-119">Applies publisher policy.</span></span> <span data-ttu-id="ecd80-120">Toto je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="ecd80-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="ecd80-121">Nevztahuje zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="ecd80-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecd80-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ecd80-122">Child Elements</span></span>  
 <span data-ttu-id="ecd80-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="ecd80-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ecd80-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ecd80-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ecd80-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="ecd80-125">Element</span></span>|<span data-ttu-id="ecd80-126">Popis</span><span class="sxs-lookup"><span data-stu-id="ecd80-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ecd80-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecd80-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ecd80-128">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ecd80-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecd80-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecd80-129">Remarks</span></span>  
 <span data-ttu-id="ecd80-130">Při dodavatelem součásti uvolní novou verzi sestavení, můžete dodavatele zahrnout zásad vydavatele, aplikace, které používají předchozí verzi aplikace teď použili tuto novou verzi.</span><span class="sxs-lookup"><span data-stu-id="ecd80-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="ecd80-131">K určení, jestli se má použít pro konkrétní sestavení zásady vydavatele, uvést  **\<publisherPolicy >** element v  **\<dependentAssembly >** element.</span><span class="sxs-lookup"><span data-stu-id="ecd80-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="ecd80-132">Výchozí nastavení **použít** atribut je **Ano**.</span><span class="sxs-lookup"><span data-stu-id="ecd80-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="ecd80-133">Nastavení **použít** atribut **žádné** přepsání všechny předchozí **Ano** nastavení pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="ecd80-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="ecd80-134">Oprávnění jsou nutná pro aplikaci explicitně ignorovat pomocí zásad vydavatele [ \<publisherPolicy použít = "žádný" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ecd80-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="ecd80-135">Je povoleno nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznak na <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="ecd80-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="ecd80-136">Další informace najdete v tématu [sestavení vazby bezpečnostní oprávnění k přesměrování](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="ecd80-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecd80-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecd80-137">Example</span></span>  
 <span data-ttu-id="ecd80-138">Následující příklad vypne zásad vydavatele pro sestavení, `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="ecd80-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ecd80-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecd80-139">See Also</span></span>  
 [<span data-ttu-id="ecd80-140">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="ecd80-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ecd80-141">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ecd80-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ecd80-142">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="ecd80-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="ecd80-143">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="ecd80-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
