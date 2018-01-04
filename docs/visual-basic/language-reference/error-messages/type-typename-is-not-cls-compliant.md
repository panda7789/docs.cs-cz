---
title: "Typ &lt;typename&gt; není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords: BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36a49ccf7d2185c26ef8d23eebea216cc193d951
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a><span data-ttu-id="dee94-102">Typ &lt;typename&gt; není kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="dee94-102">Type &lt;typename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="dee94-103">Proměnná, vlastnost nebo funkce návratový je deklarovaný s datovým typem, který není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="dee94-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="dee94-104">Pro aplikace splňovat [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="dee94-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="dee94-105">Následující [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] datové typy nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="dee94-105">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="dee94-106">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="dee94-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="dee94-107">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="dee94-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="dee94-108">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="dee94-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="dee94-109">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="dee94-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="dee94-110">**ID chyby:** BC40041</span><span class="sxs-lookup"><span data-stu-id="dee94-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dee94-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="dee94-111">To correct this error</span></span>  
  
-   <span data-ttu-id="dee94-112">Pokud vaše aplikace musí být kompatibilní se specifikací CLS, změňte datový typ tohoto elementu na nejbližší typ kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="dee94-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="dee94-113">Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="dee94-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="dee94-114">Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="dee94-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="dee94-115">Pokud vaše aplikace nemusí být kompatibilní se specifikací CLS, není potřeba nic nezmění.</span><span class="sxs-lookup"><span data-stu-id="dee94-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="dee94-116">Je třeba věnovat pozornost jeho nekompatibilitu, ale.</span><span class="sxs-lookup"><span data-stu-id="dee94-116">You should be aware of its noncompliance, however.</span></span>