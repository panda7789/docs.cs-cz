---
title: Typ <typename> není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: eacf5036ebc6fc31dfa0e8de39c4fb574c9072b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386955"
---
# <a name="type-typename-is-not-cls-compliant"></a><span data-ttu-id="3bf1a-102">Typ \<typename> není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="3bf1a-102">Type \<typename> is not CLS-compliant</span></span>
<span data-ttu-id="3bf1a-103">Proměnná, vlastnost nebo návrat funkce jsou deklarovány s datovým typem, který není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="3bf1a-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="3bf1a-104">Aby aplikace splňovala [jazykovou nezávislost a součásti nezávislé na jazyce](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="3bf1a-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="3bf1a-105">Následující Visual Basic datové typy nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="3bf1a-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="3bf1a-106">SByte – datový typ</span><span class="sxs-lookup"><span data-stu-id="3bf1a-106">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="3bf1a-107">UInteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="3bf1a-107">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="3bf1a-108">ULong – datový typ</span><span class="sxs-lookup"><span data-stu-id="3bf1a-108">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="3bf1a-109">UShort – datový typ</span><span class="sxs-lookup"><span data-stu-id="3bf1a-109">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="3bf1a-110">**ID chyby:** BC40041</span><span class="sxs-lookup"><span data-stu-id="3bf1a-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3bf1a-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3bf1a-111">To correct this error</span></span>  
  
- <span data-ttu-id="3bf1a-112">Pokud vaše aplikace musí být kompatibilní se specifikací CLS, změňte datový typ tohoto prvku na nejbližší typ kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="3bf1a-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="3bf1a-113">Například, `UInteger` `Integer` Pokud nepotřebujete rozsah hodnoty nad 2 147 483 647, můžete použít třeba místo.</span><span class="sxs-lookup"><span data-stu-id="3bf1a-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="3bf1a-114">Pokud budete potřebovat Rozšířený rozsah, můžete nahradit `UInteger` `Long` .</span><span class="sxs-lookup"><span data-stu-id="3bf1a-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="3bf1a-115">Pokud vaše aplikace nemusí být kompatibilní se specifikací CLS, nemusíte měnit žádné změny.</span><span class="sxs-lookup"><span data-stu-id="3bf1a-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="3bf1a-116">Měli byste si uvědomit, že nedodržující předpisy byste ale.</span><span class="sxs-lookup"><span data-stu-id="3bf1a-116">You should be aware of its noncompliance, however.</span></span>
