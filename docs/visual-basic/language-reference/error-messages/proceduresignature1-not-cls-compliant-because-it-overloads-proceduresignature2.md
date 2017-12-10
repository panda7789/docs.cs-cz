---
title: "&lt;proceduresignature1&gt; není kompatibilní se specifikací CLS, protože ho přetížení &lt;proceduresignature2&gt; který se liší od jeho pouze pole typů parametr pole nebo pořadí typy pole parametrů"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords: BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cdbd8edaefba4554e8de92cb600f045dc39f780
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="7e9b2-102">&lt;proceduresignature1&gt; není kompatibilní se specifikací CLS, protože ho přetížení &lt;proceduresignature2&gt; který se liší od jeho pouze pole typů parametr pole nebo pořadí typy pole parametrů</span><span class="sxs-lookup"><span data-stu-id="7e9b2-102">&lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>
<span data-ttu-id="7e9b2-103">Procedura nebo vlastnosti je označena jako `<CLSCompliant(True)>` při přepíše jiný postup nebo vlastnost a je jediným rozdílem mezi seznamy jejich parametrů úroveň vnoření Vícenásobná pole nebo pole pořadí.</span><span class="sxs-lookup"><span data-stu-id="7e9b2-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>  
  
 <span data-ttu-id="7e9b2-104">V následující deklarace druhý a třetí deklarace generovat tuto chybu.</span><span class="sxs-lookup"><span data-stu-id="7e9b2-104">In the following declarations, the second and third declarations generate this error.</span></span>  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 <span data-ttu-id="7e9b2-105">Druhý deklaraci změní parametr původní jednorozměrné `arrayParam` do pole polí.</span><span class="sxs-lookup"><span data-stu-id="7e9b2-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="7e9b2-106">Třetí změny deklarace `arrayParam` dvourozměrné pole (pořadí 2).</span><span class="sxs-lookup"><span data-stu-id="7e9b2-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="7e9b2-107">Přestože jazyka Visual Basic umožňuje přetížení pro liší pouze jednu z těchto změn, takové přetížení není kompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="7e9b2-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="7e9b2-108">Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="7e9b2-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="7e9b2-109">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7e9b2-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="7e9b2-110">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.</span><span class="sxs-lookup"><span data-stu-id="7e9b2-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="7e9b2-111">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="7e9b2-111">By default, this message is a warning.</span></span> <span data-ttu-id="7e9b2-112">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7e9b2-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="7e9b2-113">**ID chyby:** BC40035</span><span class="sxs-lookup"><span data-stu-id="7e9b2-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7e9b2-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7e9b2-114">To correct this error</span></span>  
  
-   <span data-ttu-id="7e9b2-115">Pokud budete potřebovat souladu se specifikací CLS, definujte vaše přetížení pro více způsoby než pouze změny, které jsou uvedené na této stránce nápovědy se liší od sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="7e9b2-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>  
  
-   <span data-ttu-id="7e9b2-116">Pokud požadujete, aby přetížení liší pouze změnami citovalo na této nápovědy stránky, odeberte <xref:System.CLSCompliantAttribute> z jejich definice nebo označit je jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="7e9b2-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e9b2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e9b2-117">See Also</span></span>  
 [<span data-ttu-id="7e9b2-118">\<PAVE přes > zápis kompatibilní se specifikací CLS kódu</span><span class="sxs-lookup"><span data-stu-id="7e9b2-118">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)  
 [<span data-ttu-id="7e9b2-119">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="7e9b2-119">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="7e9b2-120">Přetížení</span><span class="sxs-lookup"><span data-stu-id="7e9b2-120">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
