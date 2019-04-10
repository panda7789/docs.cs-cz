---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234651"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="b2b91-101">Entity Framework verze musí odpovídat verzi rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b2b91-101">Entity Framework version must match the .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b2b91-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b2b91-102">Details</span></span>|<span data-ttu-id="b2b91-103">S verzí rozhraní .NET framework by si měly odpovídat verzi rozhraní entity framework.</span><span class="sxs-lookup"><span data-stu-id="b2b91-103">The entity framework version should be matched with the .NET framework version.</span></span> <span data-ttu-id="b2b91-104">Entity Framework 5 se doporučuje pro rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="b2b91-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="b2b91-105">Existují některé známé problémy s platformou EF s 4.x v projektu rozhraní .NET Framework 4.5 kolem <xref:System.ComponentModel.DataAnnotations>.</span><span class="sxs-lookup"><span data-stu-id="b2b91-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="b2b91-106">V rozhraní .NET 4.5 tyto se přesunuly na jiné sestavení, takže dojde k problémům určující, které poznámky k použití.</span><span class="sxs-lookup"><span data-stu-id="b2b91-106">In .NET 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>|
|<span data-ttu-id="b2b91-107">Doporučení</span><span class="sxs-lookup"><span data-stu-id="b2b91-107">Suggestion</span></span>|<span data-ttu-id="b2b91-108">Upgrade na rozhraní Entity Framework 5 pro rozhraní .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b2b91-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>|
|<span data-ttu-id="b2b91-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b2b91-109">Scope</span></span>|<span data-ttu-id="b2b91-110">Hlavní</span><span class="sxs-lookup"><span data-stu-id="b2b91-110">Major</span></span>|
|<span data-ttu-id="b2b91-111">Version</span><span class="sxs-lookup"><span data-stu-id="b2b91-111">Version</span></span>|<span data-ttu-id="b2b91-112">4.5</span><span class="sxs-lookup"><span data-stu-id="b2b91-112">4.5</span></span>|
|<span data-ttu-id="b2b91-113">Type</span><span class="sxs-lookup"><span data-stu-id="b2b91-113">Type</span></span>|<span data-ttu-id="b2b91-114">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="b2b91-114">Retargeting</span></span>|
