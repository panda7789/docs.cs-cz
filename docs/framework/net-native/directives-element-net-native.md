---
title: Element &lt;Directives&gt; (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd571255f924c9f3878c00a2bc01397d63e6d777
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394443"
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="5df2c-102">Element &lt;Directives&gt; (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="5df2c-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="5df2c-103">Kořenový element v každém souboru direktivy modulu runtime pro [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5df2c-103">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="5df2c-104">**\<Direktivy xmlns = "http://schemas.microsoft.com/netfx/2013/01/metadata" >**</span><span class="sxs-lookup"><span data-stu-id="5df2c-104">**\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5df2c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5df2c-105">Syntax</span></span>  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="5df2c-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="5df2c-106">Attributes</span></span>  
  
|<span data-ttu-id="5df2c-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="5df2c-107">Attribute</span></span>|<span data-ttu-id="5df2c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="5df2c-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="5df2c-109">Obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="5df2c-109">The XML namespace.</span></span> <span data-ttu-id="5df2c-110">Její hodnota je vždycky **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="5df2c-110">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="5df2c-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="5df2c-111">Child elements</span></span>  
  
|<span data-ttu-id="5df2c-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="5df2c-112">Element</span></span>|<span data-ttu-id="5df2c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5df2c-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5df2c-114">\<Aplikace ></span><span class="sxs-lookup"><span data-stu-id="5df2c-114">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="5df2c-115">Slouží jako kontejner pro celou aplikaci typy a členy typu jejichž metadata jsou k dispozici pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="5df2c-115">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="5df2c-116">\<Knihovna ></span><span class="sxs-lookup"><span data-stu-id="5df2c-116">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="5df2c-117">Definuje sestavení, jehož podřízené typy a členy typu vyžadují metadata v době běhu.</span><span class="sxs-lookup"><span data-stu-id="5df2c-117">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5df2c-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5df2c-118">Remarks</span></span>  
 <span data-ttu-id="5df2c-119">Každý soubor direktivy modulu runtime může obsahovat jenom jednu `<Directives>` elementu.</span><span class="sxs-lookup"><span data-stu-id="5df2c-119">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="5df2c-120">`<Directives>` Element může obsahovat nula nebo jedna [ \<aplikace >](../../../docs/framework/net-native/application-element-net-native.md) elementu a nula, jednu nebo více [ \<Knihovna >](../../../docs/framework/net-native/library-element-net-native.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="5df2c-120">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df2c-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="5df2c-121">See Also</span></span>  
 [<span data-ttu-id="5df2c-122">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="5df2c-122">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="5df2c-123">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="5df2c-123">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
