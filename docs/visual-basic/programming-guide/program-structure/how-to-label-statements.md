---
title: 'Postupy: Popisek příkazy (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 2f6f0362fcec170e677d153ad9f936a5c2e55ad7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981202"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="1bec5-102">Postupy: Popisek příkazy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bec5-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="1bec5-103">Blok příkazu jsou tvořené řádků kódu, které jsou odděleny dvojtečkami.</span><span class="sxs-lookup"><span data-stu-id="1bec5-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="1bec5-104">Řádky kódu předchází identifikační řetězec nebo celé číslo se označují jako *označené*.</span><span class="sxs-lookup"><span data-stu-id="1bec5-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="1bec5-105">Popisky příkazů se používá k označení řádku kódu k jeho identifikaci při použití s příkazy, jako `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="1bec5-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="1bec5-106">Popisky mohou být buď platné identifikátory jazyka Visual Basic, jako jsou ty, které identifikují programovací prvky, nebo literály celých čísel.</span><span class="sxs-lookup"><span data-stu-id="1bec5-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="1bec5-107">Popisek musí být na začátku řádku zdrojového kódu a musí být následován dvojtečkou, bez ohledu na to, zda je následovaný příkazem na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="1bec5-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="1bec5-108">Kompilátor identifikuje popisky tak, že zkontrolujete, jestli odpovídá začátku řádku žádný identifikátor již definována.</span><span class="sxs-lookup"><span data-stu-id="1bec5-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="1bec5-109">Pokud tomu tak není, kompilátor předpokládá, že je popisek.</span><span class="sxs-lookup"><span data-stu-id="1bec5-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="1bec5-110">Popisky své vlastní prohlášení místa a nejsou v konfliktu s další identifikátory.</span><span class="sxs-lookup"><span data-stu-id="1bec5-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="1bec5-111">Obor popisku je tělo metody.</span><span class="sxs-lookup"><span data-stu-id="1bec5-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="1bec5-112">Deklarace popisek má přednost před v každé situaci, nejednoznačný.</span><span class="sxs-lookup"><span data-stu-id="1bec5-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bec5-113">Popisky lze použít pouze na spustitelné příkazy uvnitř metody.</span><span class="sxs-lookup"><span data-stu-id="1bec5-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="1bec5-114">K označení řádku kódu</span><span class="sxs-lookup"><span data-stu-id="1bec5-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="1bec5-115">Místo identifikátoru, za nímž následuje dvojtečka, na začátek řádku zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="1bec5-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="1bec5-116">Například následující řádky kódu jsou označeny `Jump` a `120`v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="1bec5-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a><span data-ttu-id="1bec5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1bec5-117">See also</span></span>
- [<span data-ttu-id="1bec5-118">Příkazy</span><span class="sxs-lookup"><span data-stu-id="1bec5-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="1bec5-119">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="1bec5-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="1bec5-120">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="1bec5-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
