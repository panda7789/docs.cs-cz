---
title: Nedostatek místa v zásobníku (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 2f91763888069b6dca90da03995dc1b6812fd426
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655488"
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="c500c-102">Nedostatek místa v zásobníku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c500c-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="c500c-103">Zásobník představuje pracovní oblast paměti, která zvyšuje nebo snižuje dynamicky s požadavky prováděnému programu.</span><span class="sxs-lookup"><span data-stu-id="c500c-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="c500c-104">Překročení omezení.</span><span class="sxs-lookup"><span data-stu-id="c500c-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c500c-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c500c-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="c500c-106">Zkontrolujte, že nejsou postupy vnořené příliš hluboko.</span><span class="sxs-lookup"><span data-stu-id="c500c-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="c500c-107">Zajistěte, aby rekurzivní procedury řádně ukončit.</span><span class="sxs-lookup"><span data-stu-id="c500c-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="c500c-108">Pokud místní proměnné vyžadují další místní proměnné místa než je k dispozici, zkuste deklarace proměnných na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="c500c-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="c500c-109">Můžete také deklarovat všechny proměnné v postupu statické před `Property`, `Sub`, nebo `Function` – klíčové slovo s `Static`.</span><span class="sxs-lookup"><span data-stu-id="c500c-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="c500c-110">Nebo můžete použít `Static` příkaz pro deklarování jednotlivých statické proměnné v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="c500c-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="c500c-111">Některé z vašich pevné délky řetězců jako řetězce proměnné délky, znovu definujte, jak používat více místa v zásobníku než řetězce proměnné délky řetězce pevné délky.</span><span class="sxs-lookup"><span data-stu-id="c500c-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="c500c-112">Můžete také definovat řetězec na úrovni modulu, ve kterém nevyžaduje žádné místo v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c500c-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="c500c-113">Zkontrolujte počet vnořených `DoEvents` volání, funkcí s použitím `Calls` dialogové okno k zobrazení, které postupy jsou aktivní v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c500c-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="c500c-114">Ujistěte se, že jste nezpůsobil "událost v kaskádě" vyvoláte událost, která volá proceduru události již v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c500c-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="c500c-115">Událost v kaskádě je podobný postup volání rozhraní neukončený rekurzivní, ale je méně zřejmé, protože při volání jazyka Visual Basic, spíše než explicitní volání konstruktoru v kódu.</span><span class="sxs-lookup"><span data-stu-id="c500c-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by Visual Basic rather than an explicit call in the code.</span></span> <span data-ttu-id="c500c-116">Použití `Calls` dialogové okno k zobrazení, které postupy jsou aktivní v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c500c-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c500c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c500c-117">See also</span></span>
- [<span data-ttu-id="c500c-118">Okna paměti</span><span class="sxs-lookup"><span data-stu-id="c500c-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
