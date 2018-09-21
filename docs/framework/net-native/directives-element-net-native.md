---
title: Element &lt;Directives&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8921d2841f9a7b4228ae3b8735d7047453f71bcb
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46490624"
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="70bd3-102">Element &lt;Directives&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="70bd3-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="70bd3-103">Kořenový element v každém souboru direktiv modulu runtime pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="70bd3-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="70bd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70bd3-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="70bd3-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="70bd3-105">Attributes</span></span>  
  
|<span data-ttu-id="70bd3-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="70bd3-106">Attribute</span></span>|<span data-ttu-id="70bd3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="70bd3-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="70bd3-108">Obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="70bd3-108">The XML namespace.</span></span> <span data-ttu-id="70bd3-109">Její hodnota je vždy **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="70bd3-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="70bd3-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="70bd3-110">Child elements</span></span>  
  
|<span data-ttu-id="70bd3-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="70bd3-111">Element</span></span>|<span data-ttu-id="70bd3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="70bd3-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70bd3-113">\<Aplikace ></span><span class="sxs-lookup"><span data-stu-id="70bd3-113">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="70bd3-114">Slouží jako kontejner pro celou aplikaci typy a členy typu, jehož metadata jsou k dispozici pro účely reflexe.</span><span class="sxs-lookup"><span data-stu-id="70bd3-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="70bd3-115">\<Knihovny ></span><span class="sxs-lookup"><span data-stu-id="70bd3-115">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="70bd3-116">Určuje sestavení, jejichž podřízené typy a členy typu vyžadují metadata v době běhu.</span><span class="sxs-lookup"><span data-stu-id="70bd3-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70bd3-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70bd3-117">Remarks</span></span>  
 <span data-ttu-id="70bd3-118">Každý soubor direktiv modulu runtime může obsahovat jenom jednu `<Directives>` elementu.</span><span class="sxs-lookup"><span data-stu-id="70bd3-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="70bd3-119">`<Directives>` Element může obsahovat nula nebo jedna [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) elementu a nula, jeden nebo více [ \<knihovny >](../../../docs/framework/net-native/library-element-net-native.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="70bd3-119">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70bd3-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="70bd3-120">See Also</span></span>  
 [<span data-ttu-id="70bd3-121">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="70bd3-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="70bd3-122">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="70bd3-122">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
