---
title: '&lt;proceduresignature1&gt; není kompatibilní se specifikací CLS, protože ho přetížení &lt;proceduresignature2&gt; který se liší od jeho pouze pole typů parametr pole nebo pořadí typy pole parametrů'
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 0d150dad8d32b4bfa2b9e549e068ef24382d0eba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594725"
---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="842fb-102">&lt;proceduresignature1&gt; není kompatibilní se specifikací CLS, protože ho přetížení &lt;proceduresignature2&gt; který se liší od jeho pouze pole typů parametr pole nebo pořadí typy pole parametrů</span><span class="sxs-lookup"><span data-stu-id="842fb-102">&lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>
<span data-ttu-id="842fb-103">Procedura nebo vlastnosti je označena jako `<CLSCompliant(True)>` při přepíše jiný postup nebo vlastnost a je jediným rozdílem mezi seznamy jejich parametrů úroveň vnoření Vícenásobná pole nebo pole pořadí.</span><span class="sxs-lookup"><span data-stu-id="842fb-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>  
  
 <span data-ttu-id="842fb-104">V následující deklarace druhý a třetí deklarace generovat tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="842fb-104">In the following declarations, the second and third declarations generate this error.</span></span>  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 <span data-ttu-id="842fb-105">Druhý deklaraci změní parametr původní jednorozměrné `arrayParam` do pole polí.</span><span class="sxs-lookup"><span data-stu-id="842fb-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="842fb-106">Třetí změny deklarace `arrayParam` dvourozměrné pole (pořadí 2).</span><span class="sxs-lookup"><span data-stu-id="842fb-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="842fb-107">Přestože jazyka Visual Basic umožňuje přetížení pro liší pouze jednu z těchto změn, takové přetížení není kompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="842fb-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="842fb-108">Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="842fb-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="842fb-109">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="842fb-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="842fb-110">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.</span><span class="sxs-lookup"><span data-stu-id="842fb-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="842fb-111">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="842fb-111">By default, this message is a warning.</span></span> <span data-ttu-id="842fb-112">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="842fb-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="842fb-113">**ID chyby:** BC40035</span><span class="sxs-lookup"><span data-stu-id="842fb-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="842fb-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="842fb-114">To correct this error</span></span>  
  
-   <span data-ttu-id="842fb-115">Pokud budete potřebovat souladu se specifikací CLS, definujte vaše přetížení pro více způsoby než pouze změny, které jsou uvedené na této stránce nápovědy se liší od sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="842fb-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>  
  
-   <span data-ttu-id="842fb-116">Pokud požadujete, aby přetížení liší pouze změnami citovalo na této nápovědy stránky, odeberte <xref:System.CLSCompliantAttribute> z jejich definice nebo označit je jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="842fb-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="842fb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="842fb-117">See Also</span></span>  
   
 [<span data-ttu-id="842fb-118">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="842fb-118">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="842fb-119">Overloads</span><span class="sxs-lookup"><span data-stu-id="842fb-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
