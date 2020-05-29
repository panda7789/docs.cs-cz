---
title: <Directives>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 0c6ebb8954e80f3f6dc6733f0e9d76094477689b
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202387"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="0f8cd-102">\<Directives>– Element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="0f8cd-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="0f8cd-103">Kořenový element v každém souboru direktiv modulu runtime pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0f8cd-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="0f8cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f8cd-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="0f8cd-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="0f8cd-105">Attributes</span></span>  
  
|<span data-ttu-id="0f8cd-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="0f8cd-106">Attribute</span></span>|<span data-ttu-id="0f8cd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0f8cd-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="0f8cd-108">Obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="0f8cd-108">The XML namespace.</span></span> <span data-ttu-id="0f8cd-109">Jeho hodnota je vždy `http://schemas.microsoft.com/netfx/2013/01/metadata` .</span><span class="sxs-lookup"><span data-stu-id="0f8cd-109">Its value is always `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="0f8cd-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="0f8cd-110">Child elements</span></span>  
  
|<span data-ttu-id="0f8cd-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="0f8cd-111">Element</span></span>|<span data-ttu-id="0f8cd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0f8cd-112">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="0f8cd-113">Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="0f8cd-113">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="0f8cd-114">Definuje sestavení, jehož podřízené typy a členové typu v době běhu vyžadují metadata.</span><span class="sxs-lookup"><span data-stu-id="0f8cd-114">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f8cd-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f8cd-115">Remarks</span></span>  
 <span data-ttu-id="0f8cd-116">Každý soubor direktiv modulu runtime může obsahovat pouze jeden `<Directives>` element.</span><span class="sxs-lookup"><span data-stu-id="0f8cd-116">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="0f8cd-117">`<Directives>`Element může obsahovat nula nebo jeden [\<Application>](application-element-net-native.md) prvek a nula, jeden nebo více [\<Library>](library-element-net-native.md) prvků.</span><span class="sxs-lookup"><span data-stu-id="0f8cd-117">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f8cd-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f8cd-118">See also</span></span>

- [<span data-ttu-id="0f8cd-119">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="0f8cd-119">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="0f8cd-120">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0f8cd-120">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
