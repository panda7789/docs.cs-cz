---
title: Implicitní převod z '<typename1>' na '<typename2>' při kopírování hodnoty 'ByRef' parametru '<parametername> zpět na odpovídající argument
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 4d0f9aac795f683cf58210ea38b3783e451ccfc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402859"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a><span data-ttu-id="c49f9-102">Implicitní převod z '\<typename1>' na '\<typename2>' při kopírování hodnoty 'ByRef' parametru '\<parametername> zpět na odpovídající argument</span><span class="sxs-lookup"><span data-stu-id="c49f9-102">Implicit conversion from '\<typename1>' to '\<typename2>' in copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument.</span></span>
<span data-ttu-id="c49f9-103">Procedura je volána s argumentem [ByRef](../modifiers/byref.md) jiného typu než odpovídajícím parametrem.</span><span class="sxs-lookup"><span data-stu-id="c49f9-103">A procedure is called with a [ByRef](../modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="c49f9-104">Pokud předáte argument `ByRef` , Visual Basic někdy zkopíruje hodnotu argumentu do místní proměnné v proceduře namísto předání odkazu.</span><span class="sxs-lookup"><span data-stu-id="c49f9-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="c49f9-105">V takovém případě, když se procedura vrátí, Visual Basic nutné zkopírovat hodnotu lokální proměnné zpátky do argumentu v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c49f9-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="c49f9-106">Pokud `ByRef` je do procedury zkopírována hodnota argumentu a argument a parametr je stejného typu, není nutný žádný převod.</span><span class="sxs-lookup"><span data-stu-id="c49f9-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="c49f9-107">Pokud se však typy liší, Visual Basic nutné převést v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="c49f9-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="c49f9-108">Vzhledem k tomu, že nemůžete použít `CType` ani žádná jiná klíčová slova převodu pro argument procedury nebo parametr, je takový převod vždy implicitní.</span><span class="sxs-lookup"><span data-stu-id="c49f9-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="c49f9-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="c49f9-109">By default, this message is a warning.</span></span> <span data-ttu-id="c49f9-110">Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c49f9-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c49f9-111">**ID chyby:** BC41999</span><span class="sxs-lookup"><span data-stu-id="c49f9-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c49f9-112">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c49f9-112">To correct this error</span></span>  
  
- <span data-ttu-id="c49f9-113">Pokud je to možné, použijte jako parametr procedury volající argument stejného typu, takže Visual Basic nemusí provádět žádné konverze.</span><span class="sxs-lookup"><span data-stu-id="c49f9-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
- <span data-ttu-id="c49f9-114">Pokud potřebujete zavolat proceduru s typem argumentu odlišným od typu parametru, ale nemusíte vracet hodnotu do argumentu volání, definujte parametr jako [ByVal](../modifiers/byval.md) namísto `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="c49f9-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c49f9-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c49f9-115">See also</span></span>

- [<span data-ttu-id="c49f9-116">Procedury</span><span class="sxs-lookup"><span data-stu-id="c49f9-116">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="c49f9-117">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="c49f9-117">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c49f9-118">Předávání argumentů podle hodnoty a reference</span><span class="sxs-lookup"><span data-stu-id="c49f9-118">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="c49f9-119">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="c49f9-119">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
