---
title: <proceduresignature1> není kompatibilní se Specifikací CLS, protože přetěžuje <proceduresignature2> které se od ní liší jenom polem typů parametrů nebo rozměrem typů parametru pole
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 0bda4ad6a4d5368d93e2ca603b78bf9db6aca858
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920910"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="3a4c6-102">\<proceduresignature1 > není kompatibilní se Specifikací CLS, protože přetěžuje \<proceduresignature2 > které se od ní liší jenom polem typů parametrů nebo rozměrem typů parametru pole</span><span class="sxs-lookup"><span data-stu-id="3a4c6-102">\<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>
<span data-ttu-id="3a4c6-103">Procedura nebo vlastnost je označena jako `<CLSCompliant(True)>` když přepíše jiný postup nebo vlastnost a jediným rozdílem mezi seznamy parametrů je úroveň vnoření vícenásobného pole nebo počet rozměrů pole.</span><span class="sxs-lookup"><span data-stu-id="3a4c6-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>  
  
 <span data-ttu-id="3a4c6-104">V následující deklarace generovat deklarace druhý a třetí k této chybě.</span><span class="sxs-lookup"><span data-stu-id="3a4c6-104">In the following declarations, the second and third declarations generate this error.</span></span>  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 <span data-ttu-id="3a4c6-105">Druhý deklarace změní původní jednorozměrné parametr `arrayParam` do pole polí.</span><span class="sxs-lookup"><span data-stu-id="3a4c6-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="3a4c6-106">Třetí deklarace změny `arrayParam` dvourozměrné pole (řazení 2).</span><span class="sxs-lookup"><span data-stu-id="3a4c6-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="3a4c6-107">Přestože Visual Basic umožňuje přetížení se liší pouze jednou z těchto změn, tato přetížení není kompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="3a4c6-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="3a4c6-108">Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="3a4c6-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="3a4c6-109">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3a4c6-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="3a4c6-110">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="3a4c6-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="3a4c6-111">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="3a4c6-111">By default, this message is a warning.</span></span> <span data-ttu-id="3a4c6-112">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3a4c6-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3a4c6-113">**ID chyby:** BC40035</span><span class="sxs-lookup"><span data-stu-id="3a4c6-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3a4c6-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3a4c6-114">To correct this error</span></span>  
  
- <span data-ttu-id="3a4c6-115">Pokud budete vyžadovat dodržování specifikace CLS, definujte vaši přetížení se liší od sebe navzájem více způsoby než pouze změny, které jsou uvedené na této stránce nápovědy.</span><span class="sxs-lookup"><span data-stu-id="3a4c6-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>  
  
- <span data-ttu-id="3a4c6-116">Pokud budete vyžadovat, aby přetížení se liší pouze provedené změny uvedené v této nápovědě stránce, odeberte <xref:System.CLSCompliantAttribute> z jejich definice nebo označit je jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="3a4c6-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a4c6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a4c6-117">See also</span></span>

- [<span data-ttu-id="3a4c6-118">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="3a4c6-118">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="3a4c6-119">Overloads</span><span class="sxs-lookup"><span data-stu-id="3a4c6-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
