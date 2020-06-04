---
title: 'Deklarace operátoru musí být jedna z těchto: +,-, *,-,-, ^, &amp; , like, mod, and, or, XOR, not,  <<,  >>, =,  <>, <, <=, >, >=, CType, true, false.'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 3fb2cf392611e5ca83818e3bf173513be031085d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409330"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="fceed-102">Deklarace operátoru musí být jedna z těchto: +,-, \*, \, /, ^, &amp; , like, mod, and, or, XOR, not, \<\<, >>...</span><span class="sxs-lookup"><span data-stu-id="fceed-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>
<span data-ttu-id="fceed-103">Můžete deklarovat pouze operátor, který má nárok na přetížení.</span><span class="sxs-lookup"><span data-stu-id="fceed-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="fceed-104">V následující tabulce jsou uvedeny operátory, které můžete deklarovat.</span><span class="sxs-lookup"><span data-stu-id="fceed-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="fceed-105">Typ</span><span class="sxs-lookup"><span data-stu-id="fceed-105">Type</span></span>|<span data-ttu-id="fceed-106">Operátory</span><span class="sxs-lookup"><span data-stu-id="fceed-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="fceed-107">Unární</span><span class="sxs-lookup"><span data-stu-id="fceed-107">Unary</span></span>|<span data-ttu-id="fceed-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="fceed-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="fceed-109">Binární</span><span class="sxs-lookup"><span data-stu-id="fceed-109">Binary</span></span>|<span data-ttu-id="fceed-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="fceed-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="fceed-111">Převod (Unární)</span><span class="sxs-lookup"><span data-stu-id="fceed-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="fceed-112">Všimněte si, že `=` operátor v binárním seznamu je operátor porovnání, nikoli operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="fceed-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="fceed-113">**ID chyby:** BC33000</span><span class="sxs-lookup"><span data-stu-id="fceed-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fceed-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fceed-114">To correct this error</span></span>  
  
1. <span data-ttu-id="fceed-115">Vyberte operátor ze sady přetížených operátorů.</span><span class="sxs-lookup"><span data-stu-id="fceed-115">Select an operator from the set of overloadable operators.</span></span>  
  
2. <span data-ttu-id="fceed-116">Pokud potřebujete funkcionalitu přetížení operátoru, který nelze přímo přetížit, vytvořte `Function` proceduru, která přijímá příslušné parametry a vrátí příslušnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fceed-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fceed-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="fceed-117">See also</span></span>

- [<span data-ttu-id="fceed-118">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="fceed-118">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="fceed-119">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="fceed-119">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="fceed-120">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="fceed-120">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="fceed-121">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="fceed-121">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="fceed-122">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="fceed-122">Function Statement</span></span>](../statements/function-statement.md)
