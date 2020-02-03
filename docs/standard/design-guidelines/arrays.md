---
title: Pole
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: d4a1f379a88231654c710b1df7b505316377c915
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741803"
---
# <a name="arrays"></a><span data-ttu-id="e0fe3-102">Pole</span><span class="sxs-lookup"><span data-stu-id="e0fe3-102">Arrays</span></span>
<span data-ttu-id="e0fe3-103">✔️ preferovat používání kolekcí v polích ve veřejných rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="e0fe3-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="e0fe3-104">V části [kolekce](../../../docs/standard/design-guidelines/guidelines-for-collections.md) najdete podrobné informace o tom, jak zvolit mezi kolekcemi a poli.</span><span class="sxs-lookup"><span data-stu-id="e0fe3-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="e0fe3-105">❌ pole nepoužívají pole jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e0fe3-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="e0fe3-106">Pole, které je samotné, je jen pro čtení a nelze jej změnit, ale prvky v poli lze změnit.</span><span class="sxs-lookup"><span data-stu-id="e0fe3-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="e0fe3-107">✔️ Zvažte použití vícenásobných polí namísto multidimenzionálních polí.</span><span class="sxs-lookup"><span data-stu-id="e0fe3-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="e0fe3-108">Vícenásobné pole je pole s prvky, které jsou také pole.</span><span class="sxs-lookup"><span data-stu-id="e0fe3-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="e0fe3-109">Pole, která tvoří prvky, mohou mít různé velikosti, což vede k menšímu množství nevyužitého prostoru pro některé sady dat (například zhuštěné matrice) ve srovnání s multidimenzionálními poli.</span><span class="sxs-lookup"><span data-stu-id="e0fe3-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="e0fe3-110">Kromě toho CLR optimalizuje operace indexu u vícenásobných polí, takže může v některých scénářích vykazovat lepší běhový výkon.</span><span class="sxs-lookup"><span data-stu-id="e0fe3-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="e0fe3-111">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="e0fe3-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e0fe3-112">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="e0fe3-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e0fe3-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0fe3-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="e0fe3-114">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="e0fe3-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="e0fe3-115">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="e0fe3-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
