---
title: Element <dependentAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
ms.openlocfilehash: 2de8c752867d00708173d11d1851f415a2e8518d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154202"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="65e9f-102">Element \<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="65e9f-102">\<dependentAssembly> Element</span></span>
<span data-ttu-id="65e9f-103">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e9f-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="65e9f-104">`dependentAssembly`Pro každé sestavení použijte jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="65e9f-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="65e9f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65e9f-105">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65e9f-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="65e9f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="65e9f-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="65e9f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65e9f-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="65e9f-108">Attributes</span></span>  
 <span data-ttu-id="65e9f-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="65e9f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="65e9f-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="65e9f-110">Child Elements</span></span>  
  
|<span data-ttu-id="65e9f-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="65e9f-111">Element</span></span>|<span data-ttu-id="65e9f-112">Description</span><span class="sxs-lookup"><span data-stu-id="65e9f-112">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="65e9f-113">Obsahuje identifikační informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e9f-113">Contains identifying information about the assembly.</span></span> <span data-ttu-id="65e9f-114">Tento prvek musí být zahrnut v každém `dependentAssembly` elementu.</span><span class="sxs-lookup"><span data-stu-id="65e9f-114">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="65e9f-115">Určuje, kde modul runtime může najít sdílené sestavení, pokud není nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="65e9f-115">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="65e9f-116">Přesměruje jednu verzi sestavení k jiné.</span><span class="sxs-lookup"><span data-stu-id="65e9f-116">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="65e9f-117">Určuje, zda modul runtime používá zásady vydavatele pro toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e9f-117">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65e9f-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="65e9f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="65e9f-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="65e9f-119">Element</span></span>|<span data-ttu-id="65e9f-120">Description</span><span class="sxs-lookup"><span data-stu-id="65e9f-120">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="65e9f-121">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e9f-121">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="65e9f-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65e9f-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="65e9f-123">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="65e9f-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="65e9f-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="65e9f-124">Example</span></span>  
 <span data-ttu-id="65e9f-125">Následující příklad ukazuje, jak zapouzdřit informace o sestavení pro dvě sestavení.</span><span class="sxs-lookup"><span data-stu-id="65e9f-125">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="65e9f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="65e9f-126">See also</span></span>

- [<span data-ttu-id="65e9f-127">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="65e9f-127">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="65e9f-128">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="65e9f-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="65e9f-129">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="65e9f-129">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
