---
title: '#Const – direktiva'
ms.date: 07/20/2015
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
ms.openlocfilehash: 91152771a4ef5ec74a7408511ccc2afe28dd442e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415463"
---
# <a name="const-directive"></a><span data-ttu-id="90411-102">#Const – direktiva</span><span class="sxs-lookup"><span data-stu-id="90411-102">#Const Directive</span></span>

<span data-ttu-id="90411-103">Definuje podmíněné konstanty kompilátoru pro Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="90411-103">Defines conditional compiler constants for Visual Basic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90411-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90411-104">Syntax</span></span>  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a><span data-ttu-id="90411-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="90411-105">Parts</span></span>  

 `constname`  
 <span data-ttu-id="90411-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="90411-106">Required.</span></span> <span data-ttu-id="90411-107">Název konstanty, která je definována.</span><span class="sxs-lookup"><span data-stu-id="90411-107">Name of the constant being defined.</span></span>  
  
 `expression`  
 <span data-ttu-id="90411-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="90411-108">Required.</span></span> <span data-ttu-id="90411-109">Literál, jiné podmíněné konstanty kompilátoru nebo libovolná kombinace obsahující všechny nebo všechny aritmetické nebo logické operátory s výjimkou `Is` .</span><span class="sxs-lookup"><span data-stu-id="90411-109">Literal, other conditional compiler constant, or any combination that includes any or all arithmetic or logical operators except `Is`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90411-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90411-110">Remarks</span></span>  

 <span data-ttu-id="90411-111">Podmíněné konstanty kompilátoru jsou vždy soukromé k souboru, ve kterém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="90411-111">Conditional compiler constants are always private to the file in which they appear.</span></span> <span data-ttu-id="90411-112">Nemůžete vytvořit konstanty veřejného kompilátoru pomocí `#Const` direktivy. můžete je vytvořit pouze v uživatelském rozhraní nebo pomocí `/define` Možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="90411-112">You cannot create public compiler constants using the `#Const` directive; you can create them only in the user interface or with the `/define` compiler option.</span></span>  
  
 <span data-ttu-id="90411-113">V můžete použít pouze podmíněné konstanty kompilátoru a literály `expression` .</span><span class="sxs-lookup"><span data-stu-id="90411-113">You can use only conditional compiler constants and literals in `expression`.</span></span> <span data-ttu-id="90411-114">Použití standardní konstanty definované s `Const` způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="90411-114">Using a standard constant defined with `Const` causes an error.</span></span> <span data-ttu-id="90411-115">Naopak můžete použít konstanty definované s `#Const` klíčovým slovem pouze pro podmíněnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="90411-115">Conversely, you can use constants defined with the `#Const` keyword only for conditional compilation.</span></span> <span data-ttu-id="90411-116">Konstanty mohou být také nedefinovány, v takovém případě mají hodnotu `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="90411-116">Constants can also be undefined, in which case they have a value of `Nothing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90411-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="90411-117">Example</span></span>  

 <span data-ttu-id="90411-118">V tomto příkladu se používá `#Const` direktiva.</span><span class="sxs-lookup"><span data-stu-id="90411-118">This example uses the `#Const` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="90411-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="90411-119">See also</span></span>

- [<span data-ttu-id="90411-120">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90411-120">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
- [<span data-ttu-id="90411-121">#If... Then... #Else – direktivy</span><span class="sxs-lookup"><span data-stu-id="90411-121">#If...Then...#Else Directives</span></span>](if-then-else-directives.md)
- [<span data-ttu-id="90411-122">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="90411-122">Const Statement</span></span>](../statements/const-statement.md)
- [<span data-ttu-id="90411-123">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="90411-123">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="90411-124">If...Then...Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="90411-124">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
