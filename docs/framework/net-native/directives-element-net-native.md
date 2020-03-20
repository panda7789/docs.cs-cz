---
title: <Directives>Element (nativní.NET)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 49c1aaf005b80a6c1c1fa382eebc2cb0dbfa4be7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181046"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="9d6f7-102">\<Direktivy> element (nativní.NET)</span><span class="sxs-lookup"><span data-stu-id="9d6f7-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="9d6f7-103">Kořenový prvek v každém souboru direktiv runtime pro nativní rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="9d6f7-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="9d6f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d6f7-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="9d6f7-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="9d6f7-105">Attributes</span></span>  
  
|<span data-ttu-id="9d6f7-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="9d6f7-106">Attribute</span></span>|<span data-ttu-id="9d6f7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9d6f7-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="9d6f7-108">Obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="9d6f7-108">The XML namespace.</span></span> <span data-ttu-id="9d6f7-109">Jeho hodnota je vždy **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="9d6f7-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="9d6f7-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="9d6f7-110">Child elements</span></span>  
  
|<span data-ttu-id="9d6f7-111">Element</span><span class="sxs-lookup"><span data-stu-id="9d6f7-111">Element</span></span>|<span data-ttu-id="9d6f7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9d6f7-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d6f7-113">\<>aplikace</span><span class="sxs-lookup"><span data-stu-id="9d6f7-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="9d6f7-114">Slouží jako kontejner pro typy pro celou aplikaci a členy typu, jejichž metadata jsou k dispozici pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="9d6f7-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="9d6f7-115">\<>knihovny</span><span class="sxs-lookup"><span data-stu-id="9d6f7-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="9d6f7-116">Definuje sestavení, jehož podřízené typy a členy typu vyžadují metadata za běhu.</span><span class="sxs-lookup"><span data-stu-id="9d6f7-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d6f7-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d6f7-117">Remarks</span></span>  
 <span data-ttu-id="9d6f7-118">Každý soubor direktiv runtime direktivy může obsahovat pouze jeden `<Directives>` prvek.</span><span class="sxs-lookup"><span data-stu-id="9d6f7-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="9d6f7-119">Prvek `<Directives>` může obsahovat nula nebo jeden [ \<prvek>aplikace](application-element-net-native.md) a nula, jeden nebo více [ \<prvků Library>.](library-element-net-native.md)</span><span class="sxs-lookup"><span data-stu-id="9d6f7-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6f7-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d6f7-120">See also</span></span>

- [<span data-ttu-id="9d6f7-121">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="9d6f7-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="9d6f7-122">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="9d6f7-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
