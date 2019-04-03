---
title: 'Postupy: Popisek příkazy (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 69ec8c7625410f140c59ba8dd492dca76857eb96
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828638"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="13305-102">Postupy: Popisek příkazy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13305-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="13305-103">Blok příkazu jsou tvořené řádků kódu, které jsou odděleny dvojtečkami.</span><span class="sxs-lookup"><span data-stu-id="13305-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="13305-104">Řádky kódu předchází identifikační řetězec nebo celé číslo se označují jako *označené*.</span><span class="sxs-lookup"><span data-stu-id="13305-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="13305-105">Popisky příkazů se používá k označení řádku kódu k jeho identifikaci při použití s příkazy, jako `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="13305-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="13305-106">Popisky mohou být buď platné identifikátory jazyka Visual Basic, jako jsou ty, které identifikují programovací prvky, nebo literály celých čísel.</span><span class="sxs-lookup"><span data-stu-id="13305-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="13305-107">Popisek musí být na začátku řádku zdrojového kódu a musí být následován dvojtečkou, bez ohledu na to, zda je následovaný příkazem na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="13305-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="13305-108">Kompilátor identifikuje popisky tak, že zkontrolujete, jestli odpovídá začátku řádku žádný identifikátor již definována.</span><span class="sxs-lookup"><span data-stu-id="13305-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="13305-109">Pokud tomu tak není, kompilátor předpokládá, že je popisek.</span><span class="sxs-lookup"><span data-stu-id="13305-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="13305-110">Popisky své vlastní prohlášení místa a nejsou v konfliktu s další identifikátory.</span><span class="sxs-lookup"><span data-stu-id="13305-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="13305-111">Obor popisku je tělo metody.</span><span class="sxs-lookup"><span data-stu-id="13305-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="13305-112">Deklarace popisek má přednost před v každé situaci, nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="13305-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13305-113">Popisky lze použít pouze na spustitelné příkazy uvnitř metody.</span><span class="sxs-lookup"><span data-stu-id="13305-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="13305-114">K označení řádku kódu</span><span class="sxs-lookup"><span data-stu-id="13305-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="13305-115">Místo identifikátoru, za nímž následuje dvojtečka, na začátek řádku zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="13305-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="13305-116">Například následující řádky kódu jsou označeny `Jump` a `120`v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="13305-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a><span data-ttu-id="13305-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13305-117">See also</span></span>

- [<span data-ttu-id="13305-118">Příkazy</span><span class="sxs-lookup"><span data-stu-id="13305-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="13305-119">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="13305-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="13305-120">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="13305-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
