---
title: "#<a name=\"const-directive\"></a>#Const – direktiva"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6e162b01dc5c99fb7708337d259f9e66ddd6b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="const-directive"></a><span data-ttu-id="fb3e4-102">#Const – direktiva</span><span class="sxs-lookup"><span data-stu-id="fb3e4-102">#Const Directive</span></span>
<span data-ttu-id="fb3e4-103">Definuje konstanty podmíněného kompilátoru jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb3e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb3e4-104">Syntax</span></span>  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="fb3e4-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="fb3e4-105">Parts</span></span>  
 `constname`  
 <span data-ttu-id="fb3e4-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-106">Required.</span></span> <span data-ttu-id="fb3e4-107">Název konstanta definovaný.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="fb3e4-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-108">Required.</span></span> <span data-ttu-id="fb3e4-109">Literál, ostatní konstanta podmíněného kompilátoru nebo libovolnou kombinaci, která zahrnuje některé nebo všechny aritmetické nebo logické operátory s výjimkou `Is`.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb3e4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb3e4-110">Remarks</span></span>  
 <span data-ttu-id="fb3e4-111">Konstanty podmíněného kompilátoru jsou vždy privátní do souboru, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="fb3e4-112">Nelze vytvořit veřejný kompilátoru konstanty pomocí `#Const` direktivy; můžete vytvořit pouze v uživatelském rozhraní nebo pomocí `/define` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="fb3e4-113">Můžete použít pouze konstanty podmíněného kompilátoru a literály v `expression`.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="fb3e4-114">Pomocí standardní konstanta definovaný s `Const` dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="fb3e4-115">Naopak můžete použít konstanty definovaný s `#Const` – klíčové slovo pouze pro Podmíněná kompilace.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="fb3e4-116">Konstanty můžete také být undefined, v takovém případě budou mít hodnotu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb3e4-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3e4-117">Example</span></span>  
 <span data-ttu-id="fb3e4-118">Tento příklad používá `#Const` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="fb3e4-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fb3e4-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb3e4-119">See Also</span></span>  
 [<span data-ttu-id="fb3e4-120">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb3e4-120">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)  
 [<span data-ttu-id="fb3e4-121">#If... Then... #Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="fb3e4-121">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="fb3e4-122">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="fb3e4-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="fb3e4-123">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="fb3e4-123">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="fb3e4-124">If... Potom... Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="fb3e4-124">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
