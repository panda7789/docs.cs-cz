---
title: "Nedostatek místa v zásobníku (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3959c24aa4e95204e156a9863ef0ce237af1fcda
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="7512c-102">Nedostatek místa v zásobníku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7512c-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="7512c-103">Zásobník představuje pracovní oblasti paměti, která zvětšují a zvětšování dynamicky s požadavky vaší provádění programu.</span><span class="sxs-lookup"><span data-stu-id="7512c-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="7512c-104">Jeho omezení byly překročeny.</span><span class="sxs-lookup"><span data-stu-id="7512c-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7512c-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7512c-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="7512c-106">Zkontrolujte, že nejsou postupy vnořeny příliš hluboko.</span><span class="sxs-lookup"><span data-stu-id="7512c-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="7512c-107">Zajistěte, aby rekurzivní procedury ukončit správně.</span><span class="sxs-lookup"><span data-stu-id="7512c-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="7512c-108">Pokud místní proměnné vyžadovat další místní proměnné místa na disku než je k dispozici, zkuste deklarace některé proměnné na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="7512c-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="7512c-109">Můžete také deklarovat všechny proměnné v postupu statické tak, že před `Property`, `Sub`, nebo `Function` – klíčové slovo s `Static`.</span><span class="sxs-lookup"><span data-stu-id="7512c-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="7512c-110">Nebo můžete použít `Static` příkaz deklarovat jednotlivých statické proměnné v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="7512c-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="7512c-111">Některé z vaší řetězce pevné délky jako proměnné délky řetězce, znovu definujte jako řetězce pevné délky použijte více místa v zásobníku než proměnné délky řetězce.</span><span class="sxs-lookup"><span data-stu-id="7512c-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="7512c-112">Můžete také definovat řetězec na úrovni modulu vyžaduje na žádné místa v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7512c-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="7512c-113">Zkontrolujte počet vnořených `DoEvents` funkce volání, pomocí `Calls` dialogové okno pro zobrazení, které postupy jsou aktivní v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7512c-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="7512c-114">Zkontrolujte, zda že jste nezpůsobila "cascade událostí" podle aktivuje událost, která volá proceduru události, které jsou již v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7512c-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="7512c-115">Událost v kaskádě je podobná neukončený rekurzivní volání procedur, ale je méně zřejmé, vzhledem k tomu, že se provedené volání [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] místo explicitní volání v kódu.</span><span class="sxs-lookup"><span data-stu-id="7512c-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rather than an explicit call in the code.</span></span> <span data-ttu-id="7512c-116">Použití `Calls` dialogové okno pro zobrazení, které postupy jsou aktivní v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7512c-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7512c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7512c-117">See Also</span></span>  
 [<span data-ttu-id="7512c-118">Okna paměti</span><span class="sxs-lookup"><span data-stu-id="7512c-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
