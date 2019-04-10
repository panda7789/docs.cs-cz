---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235287"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="30b2d-101">Katalogy MEF implementují rozhraní IEnumerable a proto již lze vytvořit serializátor</span><span class="sxs-lookup"><span data-stu-id="30b2d-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

|   |   |
|---|---|
|<span data-ttu-id="30b2d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="30b2d-102">Details</span></span>|<span data-ttu-id="30b2d-103">Od verze rozhraní .NET Framework 4.5, katalogy MEF implementovat rozhraní IEnumerable a proto již lze vytvořit serializátor (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> objekt).</span><span class="sxs-lookup"><span data-stu-id="30b2d-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> object).</span></span> <span data-ttu-id="30b2d-104">Při pokusu o serializaci katalogu MEF vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="30b2d-104">Trying to serialize a MEF catalog throws an exception.</span></span>|
|<span data-ttu-id="30b2d-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="30b2d-105">Suggestion</span></span>|<span data-ttu-id="30b2d-106">MEF lze vytvořit serializátor již nebudete používat</span><span class="sxs-lookup"><span data-stu-id="30b2d-106">Can no longer use MEF to create a serializer</span></span>|
|<span data-ttu-id="30b2d-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="30b2d-107">Scope</span></span>|<span data-ttu-id="30b2d-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="30b2d-108">Major</span></span>|
|<span data-ttu-id="30b2d-109">Version</span><span class="sxs-lookup"><span data-stu-id="30b2d-109">Version</span></span>|<span data-ttu-id="30b2d-110">4.5</span><span class="sxs-lookup"><span data-stu-id="30b2d-110">4.5</span></span>|
|<span data-ttu-id="30b2d-111">Type</span><span class="sxs-lookup"><span data-stu-id="30b2d-111">Type</span></span>|<span data-ttu-id="30b2d-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="30b2d-112">Runtime</span></span>|
