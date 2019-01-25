---
title: Výchozí (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: b63fa66c9cda1e439e3917ca62377f68028fc049
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497838"
---
# <a name="default-visual-basic"></a><span data-ttu-id="514cf-102">Výchozí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="514cf-102">Default (Visual Basic)</span></span>
<span data-ttu-id="514cf-103">Identifikuje vlastnost jako výchozí vlastnost své třídy, struktury nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="514cf-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="514cf-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="514cf-104">Remarks</span></span>  
 <span data-ttu-id="514cf-105">Třídy, struktury nebo rozhraní můžete určit jenom jedna z jeho vlastnosti, jako *výchozí vlastnost*za předpokladu, že vlastnost používá nejméně jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="514cf-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="514cf-106">Pokud kód provede odkaz na třídy nebo struktury bez zadání členem, Visual Basic přeloží tento odkaz na výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="514cf-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="514cf-107">Výchozí vlastnosti může vést k malé snížení zdrojového kódu – znaků, ale váš kód mohl provést obtížněji čitelný.</span><span class="sxs-lookup"><span data-stu-id="514cf-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="514cf-108">Pokud volající kód není znáte třídy nebo struktury, když se vytváří odkaz na název třídy nebo struktury nemůže být určité Určuje, zda přistupuje k této referenční třídy nebo struktury samotné nebo výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="514cf-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="514cf-109">To může vést k chybám kompilátoru nebo běhové logiky drobné chyby.</span><span class="sxs-lookup"><span data-stu-id="514cf-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="514cf-110">Můžete poněkud snížit pravděpodobnost vzniku chyby výchozí vlastnost vždy používat [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavení kompilátoru kontroly typů pro `On`.</span><span class="sxs-lookup"><span data-stu-id="514cf-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="514cf-111">Pokud máte v úmyslu použít předdefinované třídy nebo struktury v kódu, musíte určit, zda má výchozí vlastnosti a pokud ano, co její název je.</span><span class="sxs-lookup"><span data-stu-id="514cf-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="514cf-112">Z důvodu tyto nevýhody měli byste zvážit, není definování výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="514cf-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="514cf-113">Pro lepší čitelnost kódu byste také vzít v úvahu vždy odkazuje na všechny vlastnosti explicitně, dokonce i výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="514cf-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="514cf-114">`Default` Modifikátor lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="514cf-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="514cf-115">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="514cf-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="514cf-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="514cf-116">See also</span></span>
- [<span data-ttu-id="514cf-117">Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="514cf-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="514cf-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="514cf-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
