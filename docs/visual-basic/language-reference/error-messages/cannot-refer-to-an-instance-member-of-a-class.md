---
title: V rámci sdílené metody nebo inicializační procedury sdíleného člena nelze odkazovat na instanci členu, aniž by byla k dispozici explicitní instance třídy.
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: fc54bbf8053c07cc3b48a762b6f1c60344de9921
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822567"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="0e149-102">V rámci sdílené metody nebo inicializační procedury sdíleného člena nelze odkazovat na instanci členu, aniž by byla k dispozici explicitní instance třídy.</span><span class="sxs-lookup"><span data-stu-id="0e149-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="0e149-103">Pokusili jste se odkazovat na nesdílený člen třídy z v rámci sdílené procedury.</span><span class="sxs-lookup"><span data-stu-id="0e149-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="0e149-104">Následující příklad ukazuje takovou situaci.</span><span class="sxs-lookup"><span data-stu-id="0e149-104">The following example demonstrates such a situation.</span></span>  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="0e149-105">V předchozím příkladu přiřazovací příkaz `x = 10` tuto chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="0e149-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="0e149-106">Je to proto, sdílený postup se pokouší o přístup k proměnné instance.</span><span class="sxs-lookup"><span data-stu-id="0e149-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="0e149-107">Proměnná `x` je členem instance, protože není deklarován jako [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="0e149-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="0e149-108">Každá instance třídy `sample` obsahuje vlastní jednotlivých proměnnou `x`.</span><span class="sxs-lookup"><span data-stu-id="0e149-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="0e149-109">Když jedna instance nastavuje nebo mění hodnotu `x`, nemá vliv na hodnotu `x` v jiné instanci.</span><span class="sxs-lookup"><span data-stu-id="0e149-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="0e149-110">Nicméně postup `setX` je `Shared` mezi všemi instancemi třídy `sample`.</span><span class="sxs-lookup"><span data-stu-id="0e149-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="0e149-111">To znamená, že není spojen s jakoukoli jednu instanci třídy, ale místo toho pracuje nezávisle jednotlivých instancí.</span><span class="sxs-lookup"><span data-stu-id="0e149-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="0e149-112">Protože nemá žádné připojení s konkrétní instancí `setX` nelze přistupovat k proměnné instance.</span><span class="sxs-lookup"><span data-stu-id="0e149-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="0e149-113">Musíte pouze na provoz `Shared` proměnné.</span><span class="sxs-lookup"><span data-stu-id="0e149-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="0e149-114">Když `setX` nastavuje nebo mění hodnotu sdíleného proměnné, nová hodnota je k dispozici pro všechny instance třídy.</span><span class="sxs-lookup"><span data-stu-id="0e149-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="0e149-115">**ID chyby:** BC30369</span><span class="sxs-lookup"><span data-stu-id="0e149-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0e149-116">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0e149-116">To correct this error</span></span>  
  
1.  <span data-ttu-id="0e149-117">Rozhodněte, jestli chcete, aby člen sdílí mezi všemi instancemi třídy, nebo se uchovávají jednotlivé pro každou instanci.</span><span class="sxs-lookup"><span data-stu-id="0e149-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2.  <span data-ttu-id="0e149-118">Pokud chcete jednu kopii členu, který chcete sdílet mezi všemi instancemi, přidejte `Shared` – klíčové slovo do deklarace člena.</span><span class="sxs-lookup"><span data-stu-id="0e149-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="0e149-119">Zachovat `Shared` – klíčové slovo v deklaraci procedury.</span><span class="sxs-lookup"><span data-stu-id="0e149-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3.  <span data-ttu-id="0e149-120">Pokud chcete, aby každá instance má svůj vlastní jednotlivá kopie člena, nezadávejte `Shared` pro deklarace člena.</span><span class="sxs-lookup"><span data-stu-id="0e149-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="0e149-121">Odeberte `Shared` – klíčové slovo z deklarace procedury.</span><span class="sxs-lookup"><span data-stu-id="0e149-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e149-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e149-122">See also</span></span>

- [<span data-ttu-id="0e149-123">Shared</span><span class="sxs-lookup"><span data-stu-id="0e149-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
