---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 042908b8427de2de0de96bbb32df7be018bb915c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="3047f-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3047f-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="3047f-103">Určuje, že jazyka Visual Basic má zařazování všechny řetězce Unicode hodnoty bez ohledu na název externí procedura se deklarovat.</span><span class="sxs-lookup"><span data-stu-id="3047f-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="3047f-104">Při volání procedury definované mimo projekt Visual Basic – kompilátor nemá přístup k informacím, že se musí mít, aby správně voláním procedury.</span><span class="sxs-lookup"><span data-stu-id="3047f-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="3047f-105">Tyto informace zahrnují, kde se nachází postup, jak je identifikovat, jeho volací sekvence a návratový typ a řetězec znaková sada, se používá.</span><span class="sxs-lookup"><span data-stu-id="3047f-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="3047f-106">[Deklarovat příkaz](../../../visual-basic/language-reference/statements/declare-statement.md) vytvoří odkaz na externí procedura a poskytuje tyto nezbytné informace.</span><span class="sxs-lookup"><span data-stu-id="3047f-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="3047f-107">`charsetmodifier` Část v `Declare` příkaz poskytuje informace sady znaků, které zařazování řetězců během volání externí procedura.</span><span class="sxs-lookup"><span data-stu-id="3047f-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="3047f-108">Ovlivní také jak jazyka Visual Basic prohledává externí soubor pro externí procedura název.</span><span class="sxs-lookup"><span data-stu-id="3047f-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="3047f-109">`Unicode` Modifikátor Určuje, že jazyka Visual Basic má zařazování všechny řetězce Unicode hodnoty a musí vyhledat postup beze změny jeho názvu během hledání.</span><span class="sxs-lookup"><span data-stu-id="3047f-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="3047f-110">Pokud není zadaný žádný modifikátor sady znaků, `Ansi` je výchozí.</span><span class="sxs-lookup"><span data-stu-id="3047f-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3047f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3047f-111">Remarks</span></span>  
 <span data-ttu-id="3047f-112">`Unicode` Modifikátor můžete v tomto kontextu použít:</span><span class="sxs-lookup"><span data-stu-id="3047f-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="3047f-113">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="3047f-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="3047f-114">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="3047f-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="3047f-115">This – klíčové slovo není podporováno.</span><span class="sxs-lookup"><span data-stu-id="3047f-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3047f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3047f-116">See Also</span></span>  
 [<span data-ttu-id="3047f-117">ANSI</span><span class="sxs-lookup"><span data-stu-id="3047f-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="3047f-118">Automaticky</span><span class="sxs-lookup"><span data-stu-id="3047f-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="3047f-119">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3047f-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
