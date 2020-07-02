---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617195"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="dc539-101">Verze Entity Framework musí odpovídat verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc539-101">Entity Framework version must match the .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="dc539-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="dc539-102">Details</span></span>

<span data-ttu-id="dc539-103">Verze Entity Framework (EF) by měla odpovídat verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc539-103">The Entity Framework (EF) version should be matched with the .NET Framework version.</span></span> <span data-ttu-id="dc539-104">Pro .NET Framework 4,5 se doporučuje Entity Framework 5.</span><span class="sxs-lookup"><span data-stu-id="dc539-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="dc539-105">K dispozici jsou některé známé problémy s EF 4. x v projektu .NET Framework 4,5 <xref:System.ComponentModel.DataAnnotations> .</span><span class="sxs-lookup"><span data-stu-id="dc539-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="dc539-106">V .NET Framework 4,5 byly tyto přesunuty do jiného sestavení, takže dojde k problémům s určením, které poznámky se mají použít.</span><span class="sxs-lookup"><span data-stu-id="dc539-106">In .NET Framework 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dc539-107">Návrh</span><span class="sxs-lookup"><span data-stu-id="dc539-107">Suggestion</span></span>

<span data-ttu-id="dc539-108">Upgrade na Entity Framework 5 pro .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="dc539-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>

| <span data-ttu-id="dc539-109">Name</span><span class="sxs-lookup"><span data-stu-id="dc539-109">Name</span></span>    | <span data-ttu-id="dc539-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="dc539-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dc539-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="dc539-111">Scope</span></span>   | <span data-ttu-id="dc539-112">Hlavní</span><span class="sxs-lookup"><span data-stu-id="dc539-112">Major</span></span>       |
| <span data-ttu-id="dc539-113">Verze</span><span class="sxs-lookup"><span data-stu-id="dc539-113">Version</span></span> | <span data-ttu-id="dc539-114">4.5</span><span class="sxs-lookup"><span data-stu-id="dc539-114">4.5</span></span>         |
| <span data-ttu-id="dc539-115">Typ</span><span class="sxs-lookup"><span data-stu-id="dc539-115">Type</span></span>    | <span data-ttu-id="dc539-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="dc539-116">Retargeting</span></span> |
