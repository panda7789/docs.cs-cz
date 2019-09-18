---
title: <Directives>– Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9ec9a09e2fc03adbfcff0d7e69489e37da6e4a5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049882"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="57c7c-102">\<Direktivy > element (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="57c7c-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="57c7c-103">Kořenový element v každém souboru direktiv modulu runtime pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="57c7c-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="57c7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57c7c-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="57c7c-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="57c7c-105">Attributes</span></span>  
  
|<span data-ttu-id="57c7c-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="57c7c-106">Attribute</span></span>|<span data-ttu-id="57c7c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="57c7c-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="57c7c-108">Obor názvů XML.</span><span class="sxs-lookup"><span data-stu-id="57c7c-108">The XML namespace.</span></span> <span data-ttu-id="57c7c-109">Jeho hodnota je vždy **"http://schemas.microsoft.com/netfx/2013/01/metadata"** .</span><span class="sxs-lookup"><span data-stu-id="57c7c-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="57c7c-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="57c7c-110">Child elements</span></span>  
  
|<span data-ttu-id="57c7c-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="57c7c-111">Element</span></span>|<span data-ttu-id="57c7c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="57c7c-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57c7c-113">\<> Aplikace</span><span class="sxs-lookup"><span data-stu-id="57c7c-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="57c7c-114">Slouží jako kontejner pro typy v rámci aplikace a členy typu, jejichž metadata jsou k dispozici pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="57c7c-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="57c7c-115">\<Library></span><span class="sxs-lookup"><span data-stu-id="57c7c-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="57c7c-116">Definuje sestavení, jehož podřízené typy a členové typu v době běhu vyžadují metadata.</span><span class="sxs-lookup"><span data-stu-id="57c7c-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57c7c-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57c7c-117">Remarks</span></span>  
 <span data-ttu-id="57c7c-118">Každý soubor direktiv modulu runtime může obsahovat pouze `<Directives>` jeden element.</span><span class="sxs-lookup"><span data-stu-id="57c7c-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="57c7c-119">Element může obsahovat nula nebo jeden [ \<> element aplikace](application-element-net-native.md) a žádnou, jednu nebo více [ \<> prvků knihovny.](library-element-net-native.md) `<Directives>`</span><span class="sxs-lookup"><span data-stu-id="57c7c-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c7c-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57c7c-120">See also</span></span>

- [<span data-ttu-id="57c7c-121">Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="57c7c-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="57c7c-122">Elementy direktivy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="57c7c-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
