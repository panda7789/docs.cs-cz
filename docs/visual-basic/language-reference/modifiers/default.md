---
title: Výchozí (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18126a0a5b6254da0b43e806b3de1f5b2127e6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="default-visual-basic"></a><span data-ttu-id="8466a-102">Výchozí (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8466a-102">Default (Visual Basic)</span></span>
<span data-ttu-id="8466a-103">Identifikuje vlastnost jako vlastnost Výchozí třída, struktura, nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8466a-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8466a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8466a-104">Remarks</span></span>  
 <span data-ttu-id="8466a-105">Třída, struktura nebo rozhraní můžete určit jednu z jejích vlastností, jako *výchozí vlastnost*, za předpokladu, že má vlastnost minimálně jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="8466a-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="8466a-106">Pokud kód provede odkaz na třídu nebo strukturu bez zadání členem, Visual Basic řeší tento odkaz na výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8466a-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="8466a-107">Výchozí vlastnosti může vést ke snížení malé znaky zdrojový kód, ale jejich byl váš kód obtížněji čitelný.</span><span class="sxs-lookup"><span data-stu-id="8466a-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="8466a-108">Pokud volání kód není obeznámeni s třídě nebo struktuře, když má odkaz na název třídy nebo struktura nemůže být určité jestli přistupuje k tento odkaz, třídu nebo strukturu sám sebe nebo výchozí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8466a-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="8466a-109">To může vést k chybám kompilátoru nebo jemně běhu logické chyby.</span><span class="sxs-lookup"><span data-stu-id="8466a-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="8466a-110">Poněkud může snížit pravděpodobnost chyby výchozí vlastnost vždy pomocí [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md) nastavte typ kompilátoru kontrole `On`.</span><span class="sxs-lookup"><span data-stu-id="8466a-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="8466a-111">Pokud máte v úmyslu použít předdefinované třídu nebo strukturu ve vašem kódu, je třeba určit, jestli má výchozí vlastnost a pokud ano, jaké jeho název je.</span><span class="sxs-lookup"><span data-stu-id="8466a-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="8466a-112">Z důvodu tyto nevýhody měli byste zvážit není definování výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8466a-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="8466a-113">Kód čitelnější měli také zvážit vždy odkazující na všechny vlastnosti explicitně, i výchozí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8466a-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="8466a-114">`Default` Modifikátor můžete v tomto kontextu použít:</span><span class="sxs-lookup"><span data-stu-id="8466a-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="8466a-115">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="8466a-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8466a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8466a-116">See Also</span></span>  
 [<span data-ttu-id="8466a-117">Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8466a-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="8466a-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8466a-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
