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
ms.openlocfilehash: 89fa8a991cc7d0352eb0a13cdfd3a6063ea468e7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115848"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="7b725-102">Element \<publisherPolicy></span><span class="sxs-lookup"><span data-stu-id="7b725-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="7b725-103">Určuje, zda modul runtime používá zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="7b725-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="7b725-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b725-104">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b725-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7b725-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7b725-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7b725-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b725-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="7b725-107">Attributes</span></span>  
  
|<span data-ttu-id="7b725-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="7b725-108">Attribute</span></span>|<span data-ttu-id="7b725-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7b725-109">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="7b725-110">Určuje, jestli se mají použít zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="7b725-110">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="7b725-111">použít atribut</span><span class="sxs-lookup"><span data-stu-id="7b725-111">apply Attribute</span></span>  
  
|<span data-ttu-id="7b725-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7b725-112">Value</span></span>|<span data-ttu-id="7b725-113">Description</span><span class="sxs-lookup"><span data-stu-id="7b725-113">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="7b725-114">Použije zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="7b725-114">Applies publisher policy.</span></span> <span data-ttu-id="7b725-115">Toto je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="7b725-115">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="7b725-116">Nepoužívá zásadu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="7b725-116">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b725-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7b725-117">Child Elements</span></span>  

<span data-ttu-id="7b725-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="7b725-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b725-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7b725-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7b725-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="7b725-120">Element</span></span>|<span data-ttu-id="7b725-121">Description</span><span class="sxs-lookup"><span data-stu-id="7b725-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="7b725-122">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b725-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="7b725-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b725-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="7b725-124">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b725-124">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="7b725-125">`<dependentAssembly>`Pro každé sestavení použijte jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="7b725-125">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="7b725-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7b725-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b725-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b725-127">Remarks</span></span>  
 <span data-ttu-id="7b725-128">Když dodavatel komponenty uvolní novou verzi sestavení, dodavatel může zahrnout zásadu vydavatele, aby aplikace, které používají starou verzi, teď používaly novou verzi.</span><span class="sxs-lookup"><span data-stu-id="7b725-128">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="7b725-129">Chcete-li určit, zda se má použít zásada vydavatele pro konkrétní sestavení, vložte **\<publisherPolicy>** prvek do **\<dependentAssembly>** elementu.</span><span class="sxs-lookup"><span data-stu-id="7b725-129">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="7b725-130">Výchozí nastavení atributu **Apply** je **Ano**.</span><span class="sxs-lookup"><span data-stu-id="7b725-130">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="7b725-131">Nastavení atributu **Apply** na hodnotu **ne** přepíše všechna předchozí nastavení **Ano** pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="7b725-131">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="7b725-132">Pro aplikaci se vyžaduje oprávnění explicitně ignorovat zásady vydavatele pomocí [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) elementu v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b725-132">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="7b725-133">Oprávnění je uděleno nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku na <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="7b725-133">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="7b725-134">Další informace naleznete v tématu [oprávnění zabezpečení přesměrování vazby sestavení](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="7b725-134">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b725-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b725-135">Example</span></span>  
 <span data-ttu-id="7b725-136">Následující příklad vypne zásady vydavatele pro sestavení `myAssembly` .</span><span class="sxs-lookup"><span data-stu-id="7b725-136">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7b725-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b725-137">See also</span></span>

- [<span data-ttu-id="7b725-138">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="7b725-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7b725-139">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="7b725-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7b725-140">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="7b725-140">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="7b725-141">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="7b725-141">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
