---
title: "V rámci sdílené metody nebo inicializační procedury sdíleného člena nelze odkazovat na instanci členu, aniž by byla k dispozici explicitní instance třídy."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a15d36c0b3a4d6b1657d583de0dc61621da960d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="2ec45-102">V rámci sdílené metody nebo inicializační procedury sdíleného člena nelze odkazovat na instanci členu, aniž by byla k dispozici explicitní instance třídy.</span><span class="sxs-lookup"><span data-stu-id="2ec45-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="2ec45-103">Pokusili jste se k odkazování na člena nesdílené třídy z v rámci sdílené procedury.</span><span class="sxs-lookup"><span data-stu-id="2ec45-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="2ec45-104">Následující příklad ukazuje taková situace.</span><span class="sxs-lookup"><span data-stu-id="2ec45-104">The following example demonstrates such a situation.</span></span>  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="2ec45-105">V předchozím příkladu příkaz přiřazení `x = 10` tuto chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="2ec45-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="2ec45-106">Je to proto, že sdílený postup se pokouší o přístup k proměnné instance.</span><span class="sxs-lookup"><span data-stu-id="2ec45-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="2ec45-107">Proměnná `x` je členem instance, protože není deklarovaný jako [sdílené](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="2ec45-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="2ec45-108">Každá instance třídy `sample` obsahuje vlastní jednotlivé proměnné `x`.</span><span class="sxs-lookup"><span data-stu-id="2ec45-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="2ec45-109">Když jedna instance Nastaví nebo změní hodnotu `x`, nemá vliv na hodnotu `x` v jeho ostatní instance.</span><span class="sxs-lookup"><span data-stu-id="2ec45-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="2ec45-110">Však postup `setX` je `Shared` mezi všechny instance třídy `sample`.</span><span class="sxs-lookup"><span data-stu-id="2ec45-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="2ec45-111">To znamená, že není přidružen k žádné jedna instance třídy, ale spíš funguje nezávisle na jednotlivých instancí.</span><span class="sxs-lookup"><span data-stu-id="2ec45-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="2ec45-112">Protože nemá žádné připojení s konkrétní instanci `setX` nelze přistupovat k proměnné instance.</span><span class="sxs-lookup"><span data-stu-id="2ec45-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="2ec45-113">Ho musí fungovat jenom na `Shared` proměnné.</span><span class="sxs-lookup"><span data-stu-id="2ec45-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="2ec45-114">Když `setX` nastaví změny nebo změny hodnoty sdílené proměnné, nová hodnota je k dispozici pro všechny instance třídy.</span><span class="sxs-lookup"><span data-stu-id="2ec45-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="2ec45-115">**ID chyby:** BC30369</span><span class="sxs-lookup"><span data-stu-id="2ec45-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ec45-116">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2ec45-116">To correct this error</span></span>  
  
1.  <span data-ttu-id="2ec45-117">Rozhodněte, zda chcete, aby člen sdílen všech instancí třídy, nebo zachovány jednotlivých pro každou instanci.</span><span class="sxs-lookup"><span data-stu-id="2ec45-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2.  <span data-ttu-id="2ec45-118">Pokud chcete, aby jedna kopie člena na všechny instance, přidejte `Shared` – klíčové slovo k deklarace členů.</span><span class="sxs-lookup"><span data-stu-id="2ec45-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="2ec45-119">Zachovat `Shared` – klíčové slovo v postupu deklaraci.</span><span class="sxs-lookup"><span data-stu-id="2ec45-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3.  <span data-ttu-id="2ec45-120">Pokud chcete, aby každá instance mít svůj vlastní jednotlivá kopie člena, nezadávejte `Shared` pro deklarace členů.</span><span class="sxs-lookup"><span data-stu-id="2ec45-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="2ec45-121">Odeberte `Shared` – klíčové slovo z deklarace procedury.</span><span class="sxs-lookup"><span data-stu-id="2ec45-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec45-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ec45-122">See Also</span></span>  
 [<span data-ttu-id="2ec45-123">Sdílené</span><span class="sxs-lookup"><span data-stu-id="2ec45-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
