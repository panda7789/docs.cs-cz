---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa5724eb9123b2776c3a579e4244c55b3129816b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="740fa-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="740fa-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="740fa-103">Určuje, že jazyka Visual Basic má zařazování všechny řetězce hodnoty American National Standards Institute (ANSI) bez ohledu na název externí procedura je deklarován.</span><span class="sxs-lookup"><span data-stu-id="740fa-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="740fa-104">Při volání procedury definované mimo projekt Visual Basic – kompilátor nemá přístup k informacím, které potřebuje voláním procedury správně.</span><span class="sxs-lookup"><span data-stu-id="740fa-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="740fa-105">Tyto informace zahrnují, kde se nachází postup, jak je identifikovat, jeho volací sekvence a návratový typ a řetězec znaková sada, se používá.</span><span class="sxs-lookup"><span data-stu-id="740fa-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="740fa-106">[Deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.</span><span class="sxs-lookup"><span data-stu-id="740fa-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="740fa-107">`charsetmodifier` Část v `Declare` příkaz poskytuje informace o znakových sadách pro zařazování řetězců během volání externí procedura.</span><span class="sxs-lookup"><span data-stu-id="740fa-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="740fa-108">Ovlivní také jak jazyka Visual Basic prohledává externí soubor pro externí procedura název.</span><span class="sxs-lookup"><span data-stu-id="740fa-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="740fa-109">`Ansi` Modifikátor Určuje, že jazyka Visual Basic má zařazování všechny řetězce ANSI hodnoty a musí vyhledat postup beze změny jeho názvu během hledání.</span><span class="sxs-lookup"><span data-stu-id="740fa-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="740fa-110">Pokud není zadaný žádný modifikátor sady znaků, `Ansi` je výchozí.</span><span class="sxs-lookup"><span data-stu-id="740fa-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="740fa-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="740fa-111">Remarks</span></span>  
 <span data-ttu-id="740fa-112">`Ansi` Modifikátor můžete v tomto kontextu použít:</span><span class="sxs-lookup"><span data-stu-id="740fa-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="740fa-113">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="740fa-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="740fa-114">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="740fa-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="740fa-115">This – klíčové slovo není podporováno.</span><span class="sxs-lookup"><span data-stu-id="740fa-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="740fa-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="740fa-116">See Also</span></span>  
 [<span data-ttu-id="740fa-117">Automaticky</span><span class="sxs-lookup"><span data-stu-id="740fa-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="740fa-118">Kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="740fa-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="740fa-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="740fa-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
