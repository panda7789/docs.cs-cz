---
title: "Postupy: Vytváření popisků příkazů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190ec9fc2392e6e4adae9b2b612edd69d73cedfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="febb6-102">Postupy: Vytváření popisků příkazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="febb6-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="febb6-103">Blok příkazu jsou tvořeny řádků kódu oddělené dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="febb6-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="febb6-104">Řádky kódu před sebou identifikační řetězec nebo celé číslo, které jsou označeny jako *s názvem bez přípony*.</span><span class="sxs-lookup"><span data-stu-id="febb6-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="febb6-105">Příkaz popisky slouží k označení řádku kódu pro jeho rozpoznání pro použití s příkazy, jako `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="febb6-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="febb6-106">Popisky může být buď platné identifikátory jazyka Visual Basic – jako jsou ty, které identifikují elementům programování – nebo literály celé číslo.</span><span class="sxs-lookup"><span data-stu-id="febb6-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="febb6-107">Štítek musí být uvedena na začátku řádku zdrojového kódu a musí být následovaným dvojtečkou, bez ohledu na to, jestli je následovaný příkazem na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="febb6-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="febb6-108">Kompilátor rozpoznává popisky tak, že zkontrolujete, jestli začátek řádku odpovídá žádný identifikátor již definována.</span><span class="sxs-lookup"><span data-stu-id="febb6-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="febb6-109">Pokud ne, kompilátor předpokládá, že je štítek.</span><span class="sxs-lookup"><span data-stu-id="febb6-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="febb6-110">Popisky vlastní deklarace místa a nebudou v konfliktu s další identifikátory.</span><span class="sxs-lookup"><span data-stu-id="febb6-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="febb6-111">Rozsah popisku je těla metody.</span><span class="sxs-lookup"><span data-stu-id="febb6-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="febb6-112">Popisek deklarace má přednost před v jakékoliv jiné situaci s nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="febb6-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="febb6-113">Popisky lze použít pouze v spustitelné příkazy uvnitř metody.</span><span class="sxs-lookup"><span data-stu-id="febb6-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="febb6-114">Pro označení řádku kódu</span><span class="sxs-lookup"><span data-stu-id="febb6-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="febb6-115">Umístěte identifikátorem následovaným dvojtečkou, na začátku řádku zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="febb6-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="febb6-116">Například následující řádky kódu jsou označeny `Jump` a `120`, v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="febb6-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="febb6-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="febb6-117">See Also</span></span>  
 [<span data-ttu-id="febb6-118">Příkazy</span><span class="sxs-lookup"><span data-stu-id="febb6-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="febb6-119">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="febb6-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="febb6-120">Struktura programu a pravidla týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="febb6-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
