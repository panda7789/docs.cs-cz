---
title: Implicitní převod z '<typename1>' na '<typename2>' při kopírování hodnoty 'ByRef' parametru '<parametername> zpět na odpovídající argument
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 7ac0e7961e1a039e505c85a35c7c31353ed6578e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661992"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a><span data-ttu-id="26020-102">Implicitní převod z '\<NázevTypu1 > "k"\<NázevTypu2 >' při kopírování hodnoty 'ByRef' parametru '\<parametername > "zpět do odpovídajícího argumentu.</span><span class="sxs-lookup"><span data-stu-id="26020-102">Implicit conversion from '\<typename1>' to '\<typename2>' in copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument.</span></span>
<span data-ttu-id="26020-103">Postup se nazývá se [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument jiného typu než jeho odpovídající parametr.</span><span class="sxs-lookup"><span data-stu-id="26020-103">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="26020-104">Pokud předáte argument `ByRef`, Visual Basic někdy kopíruje hodnotu argumentu do místní proměnné v postupu namísto předávání odkazem.</span><span class="sxs-lookup"><span data-stu-id="26020-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="26020-105">V takovém případě se po návratu podle postupu Visual Basic musí potom zkopírujte hodnotu lokální proměnné zpět do argumentu ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="26020-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="26020-106">Pokud `ByRef` hodnota argumentu je zkopírován do procedury a argumentu a parametru jsou stejného typu, je nezbytné žádný převod.</span><span class="sxs-lookup"><span data-stu-id="26020-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="26020-107">Ale pokud se typy liší, musíte převést jazyka Visual Basic v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="26020-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="26020-108">Protože nemůžete použít `CType` nebo některý z další klíčová slova převodu na argumentu procedury nebo parametr, takový převod je vždy implicitní.</span><span class="sxs-lookup"><span data-stu-id="26020-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="26020-109">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="26020-109">By default, this message is a warning.</span></span> <span data-ttu-id="26020-110">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="26020-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="26020-111">**ID chyby:** BC41999</span><span class="sxs-lookup"><span data-stu-id="26020-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="26020-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="26020-112">To correct this error</span></span>  
  
- <span data-ttu-id="26020-113">Pokud je to možné použijte volání argument stejného typu jako parametr procedury, proto není nutné provádět jakýkoli převod jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="26020-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
- <span data-ttu-id="26020-114">Pokud je potřeba volání procedury s argumentem typu liší od typu parametru, ale není nutné vrátit hodnotu do volání argument, definujte parametr bude [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) místo `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="26020-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26020-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26020-115">See also</span></span>

- [<span data-ttu-id="26020-116">Procedury</span><span class="sxs-lookup"><span data-stu-id="26020-116">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="26020-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="26020-117">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="26020-118">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="26020-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="26020-119">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="26020-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
