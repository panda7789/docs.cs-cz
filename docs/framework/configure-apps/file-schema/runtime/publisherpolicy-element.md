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
ms.openlocfilehash: cc206e584440778858e61fc0bab51fc8ffa2009a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252382"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="23503-102">\<publisherPolicy – element ></span><span class="sxs-lookup"><span data-stu-id="23503-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="23503-103">Určuje, zda modul runtime používá zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="23503-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
<span data-ttu-id="23503-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="23503-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="23503-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="23503-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="23503-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="23503-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="23503-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dependentAssembly**](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="23503-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="23503-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<publisherPolicy >**</span><span class="sxs-lookup"><span data-stu-id="23503-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23503-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23503-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23503-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="23503-110">Attributes and Elements</span></span>  
 <span data-ttu-id="23503-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="23503-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23503-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="23503-112">Attributes</span></span>  
  
|<span data-ttu-id="23503-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="23503-113">Attribute</span></span>|<span data-ttu-id="23503-114">Popis</span><span class="sxs-lookup"><span data-stu-id="23503-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="23503-115">Určuje, jestli se mají použít zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="23503-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="23503-116">použít atribut</span><span class="sxs-lookup"><span data-stu-id="23503-116">apply Attribute</span></span>  
  
|<span data-ttu-id="23503-117">Value</span><span class="sxs-lookup"><span data-stu-id="23503-117">Value</span></span>|<span data-ttu-id="23503-118">Popis</span><span class="sxs-lookup"><span data-stu-id="23503-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="23503-119">Použije zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="23503-119">Applies publisher policy.</span></span> <span data-ttu-id="23503-120">Toto je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="23503-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="23503-121">Nepoužívá zásadu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="23503-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23503-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="23503-122">Child Elements</span></span>  

<span data-ttu-id="23503-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="23503-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23503-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="23503-124">Parent Elements</span></span>  
  
|<span data-ttu-id="23503-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="23503-125">Element</span></span>|<span data-ttu-id="23503-126">Popis</span><span class="sxs-lookup"><span data-stu-id="23503-126">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="23503-127">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="23503-127">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="23503-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23503-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="23503-129">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="23503-129">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="23503-130">Pro každé `<dependentAssembly>` sestavení použijte jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="23503-130">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="23503-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="23503-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23503-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23503-132">Remarks</span></span>  
 <span data-ttu-id="23503-133">Když dodavatel komponenty uvolní novou verzi sestavení, dodavatel může zahrnout zásadu vydavatele, aby aplikace, které používají starou verzi, teď používaly novou verzi.</span><span class="sxs-lookup"><span data-stu-id="23503-133">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="23503-134">Chcete-li určit, zda má být pro konkrétní sestavení použita zásada vydavatele, vložte  **\<prvek publisherPolicy >** do  **\<prvku dependentAssembly >** .</span><span class="sxs-lookup"><span data-stu-id="23503-134">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="23503-135">Výchozí nastavení atributu **Apply** je **Ano**.</span><span class="sxs-lookup"><span data-stu-id="23503-135">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="23503-136">Nastavení atributu **Apply** na hodnotu **ne** přepíše všechna předchozí nastavení **Ano** pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="23503-136">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="23503-137">Aby aplikace explicitně ignorovala zásady vydavatele pomocí [ \<elementu publisherPolicy Apply = "No"/>](publisherpolicy-element.md) v konfiguračním souboru aplikace, vyžaduje oprávnění.</span><span class="sxs-lookup"><span data-stu-id="23503-137">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="23503-138">Oprávnění je uděleno nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku <xref:System.Security.Permissions.SecurityPermission>na.</span><span class="sxs-lookup"><span data-stu-id="23503-138">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="23503-139">Další informace naleznete v tématu [oprávnění zabezpečení přesměrování vazby sestavení](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="23503-139">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23503-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="23503-140">Example</span></span>  
 <span data-ttu-id="23503-141">Následující příklad vypne zásady vydavatele pro sestavení `myAssembly`.</span><span class="sxs-lookup"><span data-stu-id="23503-141">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23503-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23503-142">See also</span></span>

- [<span data-ttu-id="23503-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="23503-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="23503-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="23503-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="23503-145">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="23503-145">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="23503-146">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="23503-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
