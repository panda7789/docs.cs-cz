---
title: Typ <typename> není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 4adbf38e448dad7634a4336d20b3fce8702be1db
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664274"
---
# <a name="type-typename-is-not-cls-compliant"></a><span data-ttu-id="4add8-102">Typ \<typename > není kompatibilní se Specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="4add8-102">Type \<typename> is not CLS-compliant</span></span>
<span data-ttu-id="4add8-103">Proměnná, vlastnost nebo návratová hodnota funkce je deklarována s datovým typem, který není kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="4add8-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="4add8-104">Aplikace má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat jenom typy kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="4add8-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="4add8-105">Následující datové typy jazyka Visual Basic nejsou kompatibilní se Specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="4add8-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="4add8-106">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="4add8-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="4add8-107">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="4add8-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="4add8-108">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="4add8-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="4add8-109">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="4add8-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="4add8-110">**ID chyby:** BC40041</span><span class="sxs-lookup"><span data-stu-id="4add8-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4add8-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4add8-111">To correct this error</span></span>  
  
- <span data-ttu-id="4add8-112">Pokud vaše aplikace musí být kompatibilní se Specifikací CLS, změňte datový typ tohoto elementu na nejbližší typ. kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="4add8-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="4add8-113">Například místo hodnoty `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot nad 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="4add8-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="4add8-114">Pokud budete potřebovat delší rozsah, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="4add8-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="4add8-115">Pokud vaše aplikace nemusí být kompatibilní se Specifikací CLS, není potřeba nic měnit.</span><span class="sxs-lookup"><span data-stu-id="4add8-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="4add8-116">Měli byste vědět, jeho nedodržování předpisů, ale.</span><span class="sxs-lookup"><span data-stu-id="4add8-116">You should be aware of its noncompliance, however.</span></span>