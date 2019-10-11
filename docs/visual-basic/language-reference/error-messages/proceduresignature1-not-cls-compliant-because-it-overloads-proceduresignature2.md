---
title: <proceduresignature1> není kompatibilní se specifikací CLS, protože přetěžuje <proceduresignature2>, které se liší pouze polem typů parametrů pole nebo řazením typů parametrů pole.
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 6143ebfbe7f131b0e196e531ed4282c8333be4ea
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250171"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="2f5dc-102">\<proceduresignature1 > není kompatibilní se specifikací CLS, protože přetěžuje > \<proceduresignature2, které se liší pouze polem typů parametrů pole nebo řazením typů parametrů pole.</span><span class="sxs-lookup"><span data-stu-id="2f5dc-102">\<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>

<span data-ttu-id="2f5dc-103">Procedura nebo vlastnost je označena jako `<CLSCompliant(True)>`, Pokud Přepisuje jinou proceduru nebo vlastnost a jediným rozdílem mezi jejich seznamy parametrů je vnořená úroveň vícenásobného pole nebo rozměru pole.</span><span class="sxs-lookup"><span data-stu-id="2f5dc-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>
  
 <span data-ttu-id="2f5dc-104">V následujících deklaracích generuje druhá a třetí deklarace tuto chybu:</span><span class="sxs-lookup"><span data-stu-id="2f5dc-104">In the following declarations, the second and third declarations generate this error:</span></span>
  
 `Overloads Sub ProcessArray(arrayParam() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam()() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`  
  
 <span data-ttu-id="2f5dc-105">Druhá deklarace změní původní jednorozměrné parametr `arrayParam` na pole polí.</span><span class="sxs-lookup"><span data-stu-id="2f5dc-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="2f5dc-106">Třetí deklarace mění `arrayParam` do dvojrozměrného pole (Rank 2).</span><span class="sxs-lookup"><span data-stu-id="2f5dc-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="2f5dc-107">I když Visual Basic umožňuje, aby se přetížení lišila pouze jednou z těchto změn, takové přetížení není kompatibilní s [nezávislostí jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="2f5dc-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="2f5dc-108">Použijete-li <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte parametr `isCompliant` atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="2f5dc-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="2f5dc-109">Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2f5dc-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="2f5dc-110">Pokud nepoužijete <xref:System.CLSCompliantAttribute> na prvek, považuje se za nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="2f5dc-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="2f5dc-111">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="2f5dc-111">By default, this message is a warning.</span></span> <span data-ttu-id="2f5dc-112">Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2f5dc-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2f5dc-113">**ID chyby:** BC40035</span><span class="sxs-lookup"><span data-stu-id="2f5dc-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2f5dc-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2f5dc-114">To correct this error</span></span>  
  
- <span data-ttu-id="2f5dc-115">Pokud požadujete kompatibilitu se specifikací CLS, definujte přetížení tak, aby se vzájemně lišily více způsoby, než jenom změny citované na této stránce s touto stránkou help.</span><span class="sxs-lookup"><span data-stu-id="2f5dc-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>
- <span data-ttu-id="2f5dc-116">Pokud vyžadujete, aby se přetížení lišila pouze změnami citovanými na této stránce Nápověda, odeberte <xref:System.CLSCompliantAttribute> ze svých definic nebo je označte jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="2f5dc-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2f5dc-117">Související témata</span><span class="sxs-lookup"><span data-stu-id="2f5dc-117">See also</span></span>

- [<span data-ttu-id="2f5dc-118">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="2f5dc-118">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="2f5dc-119">Přetížení</span><span class="sxs-lookup"><span data-stu-id="2f5dc-119">Overloads</span></span>](../modifiers/overloads.md)
