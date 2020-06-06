---
title: Element <bindingRedirect>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: d96585b397f75dcb9fac7e7fce93799cc95e7c6c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154293"
---
# <a name="bindingredirect-element"></a><span data-ttu-id="94d14-102">Element \<bindingRedirect></span><span class="sxs-lookup"><span data-stu-id="94d14-102">\<bindingRedirect> Element</span></span>
<span data-ttu-id="94d14-103">Přesměruje jednu verzi sestavení k jiné.</span><span class="sxs-lookup"><span data-stu-id="94d14-103">Redirects one assembly version to another.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**  
  
## <a name="syntax"></a><span data-ttu-id="94d14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94d14-104">Syntax</span></span>  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94d14-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="94d14-105">Attributes and Elements</span></span>  
 <span data-ttu-id="94d14-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="94d14-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94d14-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="94d14-107">Attributes</span></span>  
  
|<span data-ttu-id="94d14-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="94d14-108">Attribute</span></span>|<span data-ttu-id="94d14-109">Popis</span><span class="sxs-lookup"><span data-stu-id="94d14-109">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="94d14-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="94d14-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="94d14-111">Určuje verzi sestavení, která byla původně požadována.</span><span class="sxs-lookup"><span data-stu-id="94d14-111">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="94d14-112">Formát čísla verze sestavení je *hlavní_verze. podverze. sestavení. revize*.</span><span class="sxs-lookup"><span data-stu-id="94d14-112">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="94d14-113">Platné hodnoty pro jednotlivé části tohoto čísla verze jsou 0 až 65535.</span><span class="sxs-lookup"><span data-stu-id="94d14-113">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="94d14-114">Můžete také zadat rozsah verzí v tomto formátu:</span><span class="sxs-lookup"><span data-stu-id="94d14-114">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="94d14-115">*n. n. n. n. n-n. n. n. n. n*</span><span class="sxs-lookup"><span data-stu-id="94d14-115">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="94d14-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="94d14-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="94d14-117">Určuje verzi sestavení, která se má použít místo původně požadované verze ve formátu: *n. n. n.* n</span><span class="sxs-lookup"><span data-stu-id="94d14-117">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="94d14-118">Tato hodnota může specifikovat starší verzi než `oldVersion` .</span><span class="sxs-lookup"><span data-stu-id="94d14-118">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94d14-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="94d14-119">Child Elements</span></span>  
  
|<span data-ttu-id="94d14-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="94d14-120">Element</span></span>|<span data-ttu-id="94d14-121">Description</span><span class="sxs-lookup"><span data-stu-id="94d14-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94d14-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="94d14-122">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="94d14-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="94d14-123">Parent Elements</span></span>  
  
|<span data-ttu-id="94d14-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="94d14-124">Element</span></span>|<span data-ttu-id="94d14-125">Description</span><span class="sxs-lookup"><span data-stu-id="94d14-125">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="94d14-126">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="94d14-126">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="94d14-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94d14-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="94d14-128">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="94d14-128">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="94d14-129">Používá pro jednotlivá sestavení jeden prvek dependentAssembly.</span><span class="sxs-lookup"><span data-stu-id="94d14-129">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="94d14-130">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="94d14-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94d14-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94d14-131">Remarks</span></span>  
 <span data-ttu-id="94d14-132">Při sestavování aplikace rozhraní .NET Framework v rámci sestavení se silným názvem používá aplikace ve výchozím nastavení při spuštění zmíněnou verzi, a to i tehdy, pokud je k dispozici nová verze.</span><span class="sxs-lookup"><span data-stu-id="94d14-132">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="94d14-133">Aplikaci však můžete nastavit tak, aby se spustila v rámci novější verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="94d14-133">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="94d14-134">Podrobnosti o tom, jak modul runtime používá tyto soubory k určení verze sestavení, která se má použít, najdete v tématu [jak modul runtime vyhledává sestavení](../../../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="94d14-134">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="94d14-135">Můžete přesměrovat více než jednu verzi sestavení zahrnutím více `bindingRedirect` prvků do `dependentAssembly` prvku.</span><span class="sxs-lookup"><span data-stu-id="94d14-135">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="94d14-136">Můžete také vytvořit přesměrování z novější verze na starší verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="94d14-136">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="94d14-137">Explicitní přesměrování vazeb sestavení v konfiguračním souboru aplikace vyžaduje oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="94d14-137">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="94d14-138">To platí pro přesměrování sestavení rozhraní .NET Framework a sestavení třetích stran.</span><span class="sxs-lookup"><span data-stu-id="94d14-138">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="94d14-139">Oprávnění je uděleno nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku na <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="94d14-139">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="94d14-140">Další informace naleznete v tématu [oprávnění zabezpečení přesměrování vazby sestavení](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="94d14-140">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94d14-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="94d14-141">Example</span></span>  
 <span data-ttu-id="94d14-142">Následující příklad znázorňuje způsob přesměrování jedné verze sestavení na jinou.</span><span class="sxs-lookup"><span data-stu-id="94d14-142">The following example shows how to redirect one assembly version to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94d14-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="94d14-143">See also</span></span>

- [<span data-ttu-id="94d14-144">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="94d14-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="94d14-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="94d14-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="94d14-146">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="94d14-146">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
