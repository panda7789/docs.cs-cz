---
title: Kopírování hodnoty parametru '<parametername> 'ByRef' zpět na odpovídající argument způsobí zúžení z typu '<typename1>' na typ '<typename2>'.
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: bac5f9a88df719bc64a8b0541f65e5912275866e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409748"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a><span data-ttu-id="0b9ac-102">Kopírování hodnoty parametru '\<parametername> 'ByRef' zpět na odpovídající argument způsobí zúžení z typu '\<typename1>' na typ '\<typename2>'.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-102">Copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument narrows from type '\<typename1>' to type '\<typename2>'</span></span>
<span data-ttu-id="0b9ac-103">Procedura je volána s argumentem, který rozšiřuje na odpovídající typ parametru a je zúžena konverze z parametru na argument.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="0b9ac-104">Při definování třídy nebo struktury můžete definovat jeden nebo více operátorů převodu pro převod této třídy nebo typu struktury na jiné typy.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="0b9ac-105">Můžete také definovat operátory zpětného převodu pro převod těchto ostatních typů zpět na typ třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="0b9ac-106">Použijete-li typ třídy nebo struktury ve volání procedury, Visual Basic mohou použít tyto operátory převodu pro převod typu argumentu na typ odpovídajícího parametru.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-106">When you use your class or structure type in a procedure call, Visual Basic can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="0b9ac-107">Pokud předáte argument [ByRef](../modifiers/byref.md), Visual Basic někdy zkopíruje hodnotu argumentu do místní proměnné v proceduře namísto předání odkazu.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-107">If you pass the argument [ByRef](../modifiers/byref.md), Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="0b9ac-108">V takovém případě, když se procedura vrátí, Visual Basic nutné zkopírovat hodnotu lokální proměnné zpátky do argumentu v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-108">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="0b9ac-109">Pokud `ByRef` je do procedury zkopírována hodnota argumentu a argument a parametr je stejného typu, není nutný žádný převod.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="0b9ac-110">Pokud se však typy liší, Visual Basic nutné převést v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-110">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="0b9ac-111">Pokud je jeden z typů vaší třídy nebo typu struktury, Visual Basic musí převést na i z druhého typu.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-111">If one of the types is your class or structure type, Visual Basic must convert it both to and from the other type.</span></span> <span data-ttu-id="0b9ac-112">Pokud jeden z těchto převodů rozšiřujete, může se zpětný převod zúžit.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="0b9ac-113">**ID chyby:** BC32053</span><span class="sxs-lookup"><span data-stu-id="0b9ac-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0b9ac-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0b9ac-114">To correct this error</span></span>  
  
- <span data-ttu-id="0b9ac-115">Pokud je to možné, použijte jako parametr procedury volající argument stejného typu, takže Visual Basic nemusí provádět žádné konverze.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-115">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
- <span data-ttu-id="0b9ac-116">Pokud potřebujete zavolat proceduru s typem argumentu odlišným od typu parametru, ale nemusíte vracet hodnotu do argumentu volání, definujte parametr jako [ByVal](../modifiers/byval.md) namísto `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="0b9ac-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>  
  
- <span data-ttu-id="0b9ac-117">Pokud potřebujete vrátit hodnotu do argumentu volání, definujte operátor zpětného převodu jako [rozšiřující](../modifiers/widening.md), pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="0b9ac-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b9ac-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b9ac-118">See also</span></span>

- [<span data-ttu-id="0b9ac-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="0b9ac-119">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="0b9ac-120">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="0b9ac-120">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0b9ac-121">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="0b9ac-121">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="0b9ac-122">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="0b9ac-122">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="0b9ac-123">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="0b9ac-123">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="0b9ac-124">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="0b9ac-124">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="0b9ac-125">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="0b9ac-125">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="0b9ac-126">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b9ac-126">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="0b9ac-127">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="0b9ac-127">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
