---
title: Klíčová slova jako názvy elementů v kódu
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: a98f0b027700717b414d58e1284ddec655eb25f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403223"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="d2edc-102">Klíčová slova jako názvy elementu v kódu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2edc-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="d2edc-103">Libovolný prvek programu, například proměnná, třída nebo člen – může mít stejný název jako klíčové slovo s omezením.</span><span class="sxs-lookup"><span data-stu-id="d2edc-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="d2edc-104">Můžete například vytvořit proměnnou s názvem `Loop` .</span><span class="sxs-lookup"><span data-stu-id="d2edc-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="d2edc-105">Chcete-li však odkazovat na svou verzi, která má stejný název jako klíčové slovo s omezeným přístupem, `Loop` je nutné před něj přednést úplný řetězec kvalifikace nebo jej uzavřít do hranatých závorek ( `[ ]` ), jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="d2edc-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="d2edc-106">Pokud to neuděláte, Visual Basic předpokládá použití `Loop` klíčového slova vnitřní a vytvoří chybu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d2edc-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="d2edc-107">Můžete použít hranaté závorky při odkazování na formuláře a ovládací prvky a při deklaraci proměnné nebo definování procedury se stejným názvem jako klíčové slovo s omezením.</span><span class="sxs-lookup"><span data-stu-id="d2edc-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="d2edc-108">Může být snadné zapomenout názvy nebo zahrnovat hranaté závorky a tím do kódu začlenit chyby a ztížit jeho čtení.</span><span class="sxs-lookup"><span data-stu-id="d2edc-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="d2edc-109">Z tohoto důvodu doporučujeme, abyste nepoužívali omezená klíčová slova jako názvy prvků programu.</span><span class="sxs-lookup"><span data-stu-id="d2edc-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="d2edc-110">Nicméně pokud budoucí verze Visual Basic definuje nové klíčové slovo, které je v konfliktu s existujícím formulářem nebo názvem ovládacího prvku, můžete použít tuto techniku při aktualizaci kódu pro práci s novou verzí.</span><span class="sxs-lookup"><span data-stu-id="d2edc-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2edc-111">Program může také obsahovat názvy elementů, které jsou k dispozici v jiných odkazovaných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="d2edc-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="d2edc-112">Pokud tyto názvy jsou v konfliktu s omezenými klíčovými slovy, pak při jejich umístění hranaté závorky způsobí, Visual Basic je interpretovat jako definované prvky.</span><span class="sxs-lookup"><span data-stu-id="d2edc-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2edc-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2edc-113">See also</span></span>

- [<span data-ttu-id="d2edc-114">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2edc-114">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="d2edc-115">Struktura programu a konvence kódu</span><span class="sxs-lookup"><span data-stu-id="d2edc-115">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="d2edc-116">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d2edc-116">Keywords</span></span>](../../language-reference/keywords/index.md)
