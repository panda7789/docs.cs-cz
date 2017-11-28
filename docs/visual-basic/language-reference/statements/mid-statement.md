---
title: "Mid – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61d812ef91acc65728b04efc9aa99e3975e71d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="mid-statement"></a><span data-ttu-id="6e42f-102">Mid – příkaz</span><span class="sxs-lookup"><span data-stu-id="6e42f-102">Mid Statement</span></span>
<span data-ttu-id="6e42f-103">Nahradí zadaný počet znaků `String` proměnné s znaky z jiné řetězce.</span><span class="sxs-lookup"><span data-stu-id="6e42f-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e42f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e42f-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="6e42f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6e42f-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="6e42f-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6e42f-106">Required.</span></span> <span data-ttu-id="6e42f-107">Název `String` proměnné, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="6e42f-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="6e42f-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6e42f-108">Required.</span></span> <span data-ttu-id="6e42f-109">`Integer`výraz.</span><span class="sxs-lookup"><span data-stu-id="6e42f-109">`Integer` expression.</span></span> <span data-ttu-id="6e42f-110">Znak pozice v `Target` kde začíná nahrazení textu.</span><span class="sxs-lookup"><span data-stu-id="6e42f-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="6e42f-111">`Start`používá indexu se základem jedna.</span><span class="sxs-lookup"><span data-stu-id="6e42f-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="6e42f-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6e42f-112">Optional.</span></span> <span data-ttu-id="6e42f-113">`Integer`výraz.</span><span class="sxs-lookup"><span data-stu-id="6e42f-113">`Integer` expression.</span></span> <span data-ttu-id="6e42f-114">Počet znaků, který má nahradit.</span><span class="sxs-lookup"><span data-stu-id="6e42f-114">Number of characters to replace.</span></span> <span data-ttu-id="6e42f-115">Pokud se vynechá, všechny `String` se používá.</span><span class="sxs-lookup"><span data-stu-id="6e42f-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="6e42f-116">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6e42f-116">Required.</span></span> <span data-ttu-id="6e42f-117">`String`výraz, který nahradí část `Target`.</span><span class="sxs-lookup"><span data-stu-id="6e42f-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="6e42f-118">Výjimky</span><span class="sxs-lookup"><span data-stu-id="6e42f-118">Exceptions</span></span>  
  
|<span data-ttu-id="6e42f-119">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="6e42f-119">Exception type</span></span>|<span data-ttu-id="6e42f-120">Podmínka</span><span class="sxs-lookup"><span data-stu-id="6e42f-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="6e42f-121">`Start`< = 0 nebo `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="6e42f-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e42f-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e42f-122">Remarks</span></span>  
 <span data-ttu-id="6e42f-123">Počet znaků, nahradí se vždy menší než počet znaků v `Target`.</span><span class="sxs-lookup"><span data-stu-id="6e42f-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="6e42f-124">Visual Basic má <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkce a `Mid` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6e42f-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="6e42f-125">Tyto prvky obě pracovat na zadaný počet znaků v řetězci, ale `Mid` funkce vrací znaky při `Mid` příkaz nahradí znaky.</span><span class="sxs-lookup"><span data-stu-id="6e42f-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="6e42f-126">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e42f-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e42f-127">`MidB` Prohlášení o dřívějších verzích jazyka Visual Basic nahrazuje podřetězce v bajtech, nikoli znaků.</span><span class="sxs-lookup"><span data-stu-id="6e42f-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="6e42f-128">Používá se především pro převod řetězců v aplikacích dvoubajtové znakové sady (DBCS).</span><span class="sxs-lookup"><span data-stu-id="6e42f-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="6e42f-129">V kódu Unicode, jsou všechny řetězce jazyka Visual Basic a `MidB` již není podporována.</span><span class="sxs-lookup"><span data-stu-id="6e42f-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e42f-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e42f-130">Example</span></span>  
 <span data-ttu-id="6e42f-131">Tento příklad používá `Mid` příkaz, který má zadaný počet znaků v proměnné řetězce nahraďte znaky z jiné řetězce.</span><span class="sxs-lookup"><span data-stu-id="6e42f-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="6e42f-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e42f-132">Requirements</span></span>  
 <span data-ttu-id="6e42f-133">**Namespace:** [Microsoft.VisualBasic –](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="6e42f-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="6e42f-134">**Modul:**`Strings`</span><span class="sxs-lookup"><span data-stu-id="6e42f-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="6e42f-135">**Sestavení:**[!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e42f-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e42f-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e42f-136">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [<span data-ttu-id="6e42f-137">Řetězce</span><span class="sxs-lookup"><span data-stu-id="6e42f-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="6e42f-138">Představení řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e42f-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
