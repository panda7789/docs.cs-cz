---
title: Klíčová slova jako názvy elementu v kódu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 0d52df42b00abfa364762d97c162eb143e511f06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649482"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="15a96-102">Klíčová slova jako názvy elementu v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15a96-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="15a96-103">Libovolný prvek programu, jako jsou proměnné, třídu nebo člen – může mít stejný název jako s omezeným přístupem – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="15a96-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="15a96-104">Můžete například vytvořit proměnnou s názvem `Loop`.</span><span class="sxs-lookup"><span data-stu-id="15a96-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="15a96-105">Však k odkazování na vaší verzi, která má stejný název jako s omezeným přístupem `Loop` – klíčové slovo – musí předcházet řetězec úplné kvalifikace nebo uzavřete ho do hranatých závorek (`[ ]`), jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="15a96-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 <span data-ttu-id="15a96-106">Pokud, proveďte jednu z nich pak jazyka Visual Basic se předpokládá použití uvedených vnitřní `Loop` – klíčové slovo a dojde k chybě, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15a96-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="15a96-107">Hranaté závorky můžete použít k odkazování na formuláře a ovládací prvky a při deklarování proměnné nebo definice procedury se stejným názvem jako s omezeným přístupem – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="15a96-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="15a96-108">Může být snadné zapomenout kvalifikovat názvy nebo zahrnovat hranaté závorky a proto zanést chyby do kódu a znesnadňuje ke čtení.</span><span class="sxs-lookup"><span data-stu-id="15a96-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="15a96-109">Z tohoto důvodu doporučujeme je velmi riskantní používat s omezeným přístupem klíčová slova jako názvy prvků programu.</span><span class="sxs-lookup"><span data-stu-id="15a96-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="15a96-110">Ale pokud budoucí verzi systému Visual Basic definuje new – klíčové slovo této je v konfliktu s existujícím formuláři nebo název ovládacího prvku, pak můžete použít tento postup při aktualizaci kódu pro práci s novou verzí.</span><span class="sxs-lookup"><span data-stu-id="15a96-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15a96-111">Váš program může obsahovat také názvy elementů poskytované jiných odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="15a96-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="15a96-112">Pokud tyto názvy jsou v konfliktu s klíčovými slovy s omezeným přístupem, pak umístění hranaté závorky kolem nich způsobí, že chcete interpretovat jako definované elementy jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="15a96-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a96-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15a96-113">See also</span></span>
- [<span data-ttu-id="15a96-114">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15a96-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="15a96-115">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="15a96-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="15a96-116">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="15a96-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
