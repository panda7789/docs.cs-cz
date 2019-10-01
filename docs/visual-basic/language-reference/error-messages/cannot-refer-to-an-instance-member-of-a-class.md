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
ms.openlocfilehash: a2a5ab99ff68e6dce783a2fd986ee6e8c15ae858
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701166"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="cbbdd-102">V rámci sdílené metody nebo inicializační procedury sdíleného člena nelze odkazovat na instanci členu, aniž by byla k dispozici explicitní instance třídy.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="cbbdd-103">Pokusili jste se v rámci sdílené procedury odkazovat na nesdíleného člena třídy.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="cbbdd-104">Následující příklad znázorňuje takovou situaci.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-104">The following example demonstrates such a situation.</span></span>  
  
```vb  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="cbbdd-105">V předchozím příkladu příkaz přiřazení `x = 10` vygeneruje tuto chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="cbbdd-106">Je to proto, že se sdílená procedura pokouší o přístup k proměnné instance.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="cbbdd-107">Proměnná `x` je členem instance, protože není deklarována jako [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="cbbdd-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="cbbdd-108">Každá instance třídy `sample` obsahuje vlastní individuální proměnnou `x`.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="cbbdd-109">Když jedna instance nastaví nebo změní hodnotu `x`, neovlivní hodnotu `x` v jakékoli jiné instanci.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="cbbdd-110">Nicméně procedura `setX` je `Shared` mezi všemi instancemi třídy `sample`.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="cbbdd-111">To znamená, že není přidružena k žádné jedné instanci třídy, ale funguje spíše nezávisle na jednotlivých instancích.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="cbbdd-112">Protože nemá připojení s určitou instancí, `setX` nemůže získat přístup k proměnné instance.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="cbbdd-113">Musí pracovat pouze s proměnnými @no__t 0.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="cbbdd-114">Když `setX` nastaví nebo změní hodnotu sdílené proměnné, je tato nová hodnota k dispozici všem instancím třídy.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="cbbdd-115">**ID chyby:** BC30369</span><span class="sxs-lookup"><span data-stu-id="cbbdd-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cbbdd-116">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="cbbdd-116">To correct this error</span></span>  
  
1. <span data-ttu-id="cbbdd-117">Rozhodněte, zda chcete, aby byl člen sdílen mezi všemi instancemi třídy, nebo aby se pro každou instanci chovaly jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2. <span data-ttu-id="cbbdd-118">Pokud chcete jednu kopii člena sdílet mezi všemi instancemi, přidejte do deklarace členů klíčové slovo `Shared`.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="cbbdd-119">V deklaraci procedury zachovejte klíčové slovo `Shared`.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3. <span data-ttu-id="cbbdd-120">Chcete-li, aby každá instance měla svou vlastní jednotlivou kopii člena, nezadávejte pro deklaraci člena `Shared`.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="cbbdd-121">Odeberte klíčové slovo `Shared` z deklarace procedury.</span><span class="sxs-lookup"><span data-stu-id="cbbdd-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbbdd-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbbdd-122">See also</span></span>

- [<span data-ttu-id="cbbdd-123">Shared</span><span class="sxs-lookup"><span data-stu-id="cbbdd-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
