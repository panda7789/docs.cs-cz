---
title: <Directives> – element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: abe2e7221e0afb984a6178b12fabc36ea24deb35
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128474"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="42425-102">\<direktivy > elementu (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="42425-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="42425-103">Kořenový element v každém souboru direktiv modulu runtime pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="42425-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="42425-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42425-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="42425-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="42425-105">Attributes</span></span>  
  
|<span data-ttu-id="42425-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="42425-106">Attribute</span></span>|<span data-ttu-id="42425-107">Popis</span><span class="sxs-lookup"><span data-stu-id="42425-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="42425-108">Obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="42425-108">The XML namespace.</span></span> <span data-ttu-id="42425-109">Jeho hodnota je vždy **"http://schemas.microsoft.com/netfx/2013/01/metadata"** .</span><span class="sxs-lookup"><span data-stu-id="42425-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="42425-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="42425-110">Child elements</span></span>  
  
|<span data-ttu-id="42425-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="42425-111">Element</span></span>|<span data-ttu-id="42425-112">Popis</span><span class="sxs-lookup"><span data-stu-id="42425-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42425-113">\<> aplikace</span><span class="sxs-lookup"><span data-stu-id="42425-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="42425-114">Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="42425-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="42425-115">> knihovny \<</span><span class="sxs-lookup"><span data-stu-id="42425-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="42425-116">Definuje sestavení, jehož podřízené typy a členové typu v době běhu vyžadují metadata.</span><span class="sxs-lookup"><span data-stu-id="42425-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42425-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42425-117">Remarks</span></span>  
 <span data-ttu-id="42425-118">Každý soubor direktiv modulu runtime může obsahovat pouze jeden `<Directives>` element.</span><span class="sxs-lookup"><span data-stu-id="42425-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="42425-119">Element `<Directives>` může obsahovat nula nebo jeden [\<> prvek aplikace](application-element-net-native.md) a nula, jeden nebo více [knihoven\<](library-element-net-native.md) prvků.</span><span class="sxs-lookup"><span data-stu-id="42425-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42425-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42425-120">See also</span></span>

- [<span data-ttu-id="42425-121">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="42425-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="42425-122">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="42425-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
