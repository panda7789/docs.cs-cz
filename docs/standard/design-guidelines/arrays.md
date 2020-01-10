---
title: Pole
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: ac4b073d2d3291922498a0e56c7e81f7e7868c65
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709566"
---
# <a name="arrays"></a><span data-ttu-id="26e05-102">Pole</span><span class="sxs-lookup"><span data-stu-id="26e05-102">Arrays</span></span>
<span data-ttu-id="26e05-103">**✓ DO** raději pomocí kolekcí přes pole v veřejná rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="26e05-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="26e05-104">V části [kolekce](../../../docs/standard/design-guidelines/guidelines-for-collections.md) najdete podrobné informace o tom, jak zvolit mezi kolekcemi a poli.</span><span class="sxs-lookup"><span data-stu-id="26e05-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="26e05-105">**X DO NOT** použít pole pouze pro čtení.</span><span class="sxs-lookup"><span data-stu-id="26e05-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="26e05-106">Pole, které je samotné, je jen pro čtení a nelze jej změnit, ale prvky v poli lze změnit.</span><span class="sxs-lookup"><span data-stu-id="26e05-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="26e05-107">**✓ CONSIDER** pomocí Vícenásobná pole místo vícerozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="26e05-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="26e05-108">Vícenásobné pole je pole s prvky, které jsou také pole.</span><span class="sxs-lookup"><span data-stu-id="26e05-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="26e05-109">Pole, která tvoří prvky, mohou mít různé velikosti, což vede k menšímu množství nevyužitého prostoru pro některé sady dat (například zhuštěné matrice) ve srovnání s multidimenzionálními poli.</span><span class="sxs-lookup"><span data-stu-id="26e05-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="26e05-110">Kromě toho CLR optimalizuje operace indexu u vícenásobných polí, takže může v některých scénářích vykazovat lepší běhový výkon.</span><span class="sxs-lookup"><span data-stu-id="26e05-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="26e05-111">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="26e05-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="26e05-112">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="26e05-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e05-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26e05-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="26e05-114">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="26e05-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="26e05-115">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="26e05-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
