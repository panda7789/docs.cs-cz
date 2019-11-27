---
title: Výchozí
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
ms.openlocfilehash: ad4c9528f208cc2c31f07b0506d1b049a7568c86
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351572"
---
# <a name="default-visual-basic"></a><span data-ttu-id="ea63b-102">Výchozí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea63b-102">Default (Visual Basic)</span></span>
<span data-ttu-id="ea63b-103">Identifikuje vlastnost jako výchozí vlastnost své třídy, struktury nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ea63b-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea63b-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea63b-104">Remarks</span></span>  
 <span data-ttu-id="ea63b-105">Třída, struktura nebo rozhraní mohou jako *výchozí vlastnost*označovat nejvíce jednu z jejích vlastností, za předpokladu, že vlastnost přebírá alespoň jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="ea63b-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="ea63b-106">Pokud kód vytvoří odkaz na třídu nebo strukturu bez určení člena, Visual Basic tento odkaz přeloží na výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ea63b-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="ea63b-107">Výchozí vlastnosti můžou mít za následek malé snížení počtu znaků zdrojového kódu, ale můžou ztížit čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="ea63b-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="ea63b-108">Pokud volající kód není obeznámen s vaší třídou nebo strukturou, při odkazování na název třídy nebo struktury nemůže být jisté, zda tento odkaz přistupuje k třídě nebo struktuře samotné nebo výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ea63b-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="ea63b-109">To může vést k chybám kompilátoru nebo k drobným chybám logiky run-time.</span><span class="sxs-lookup"><span data-stu-id="ea63b-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="ea63b-110">Můžete trochu snížit šanci na chyby výchozích vlastností – vždy pomocí [příkazu Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavit kontrolu typu kompilátoru na `On`.</span><span class="sxs-lookup"><span data-stu-id="ea63b-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="ea63b-111">Pokud plánujete použít předdefinovanou třídu nebo strukturu v kódu, je nutné určit, zda má výchozí vlastnost, a pokud ano, jaký je její název.</span><span class="sxs-lookup"><span data-stu-id="ea63b-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="ea63b-112">Z důvodu těchto nevýhody byste měli zvážit, že nedefinujete výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ea63b-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="ea63b-113">V případě čitelnosti kódu byste měli také zvážit možnost vždy odkazovat na všechny vlastnosti, a to i na výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ea63b-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="ea63b-114">V tomto kontextu lze použít modifikátor `Default`:</span><span class="sxs-lookup"><span data-stu-id="ea63b-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="ea63b-115">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="ea63b-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ea63b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea63b-116">See also</span></span>

- [<span data-ttu-id="ea63b-117">Postupy: deklarace a volání výchozí vlastnosti v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ea63b-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="ea63b-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ea63b-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
