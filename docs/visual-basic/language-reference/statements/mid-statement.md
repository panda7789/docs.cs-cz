---
title: Mid – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: eeef4c13743b75a3d5e61ac46afb94d9ea105b7a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348030"
---
# <a name="mid-statement"></a><span data-ttu-id="03c28-102">Mid – příkaz</span><span class="sxs-lookup"><span data-stu-id="03c28-102">Mid Statement</span></span>
<span data-ttu-id="03c28-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span><span class="sxs-lookup"><span data-stu-id="03c28-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03c28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03c28-104">Syntax</span></span>  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="03c28-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="03c28-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="03c28-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="03c28-106">Required.</span></span> <span data-ttu-id="03c28-107">Name of the `String` variable to modify.</span><span class="sxs-lookup"><span data-stu-id="03c28-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="03c28-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="03c28-108">Required.</span></span> <span data-ttu-id="03c28-109">`Integer` expression.</span><span class="sxs-lookup"><span data-stu-id="03c28-109">`Integer` expression.</span></span> <span data-ttu-id="03c28-110">Character position in `Target` where the replacement of text begins.</span><span class="sxs-lookup"><span data-stu-id="03c28-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="03c28-111">`Start` uses a one-based index.</span><span class="sxs-lookup"><span data-stu-id="03c28-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="03c28-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="03c28-112">Optional.</span></span> <span data-ttu-id="03c28-113">`Integer` expression.</span><span class="sxs-lookup"><span data-stu-id="03c28-113">`Integer` expression.</span></span> <span data-ttu-id="03c28-114">Number of characters to replace.</span><span class="sxs-lookup"><span data-stu-id="03c28-114">Number of characters to replace.</span></span> <span data-ttu-id="03c28-115">If omitted, all of `String` is used.</span><span class="sxs-lookup"><span data-stu-id="03c28-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="03c28-116">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="03c28-116">Required.</span></span> <span data-ttu-id="03c28-117">`String` expression that replaces part of `Target`.</span><span class="sxs-lookup"><span data-stu-id="03c28-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="03c28-118">Výjimky</span><span class="sxs-lookup"><span data-stu-id="03c28-118">Exceptions</span></span>  
  
|<span data-ttu-id="03c28-119">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="03c28-119">Exception type</span></span>|<span data-ttu-id="03c28-120">Podmínka</span><span class="sxs-lookup"><span data-stu-id="03c28-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="03c28-121">`Start` <= 0 or `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="03c28-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03c28-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03c28-122">Remarks</span></span>  
 <span data-ttu-id="03c28-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span><span class="sxs-lookup"><span data-stu-id="03c28-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="03c28-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span><span class="sxs-lookup"><span data-stu-id="03c28-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="03c28-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span><span class="sxs-lookup"><span data-stu-id="03c28-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="03c28-126">Další informace najdete v tématu <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="03c28-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03c28-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span><span class="sxs-lookup"><span data-stu-id="03c28-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="03c28-128">Používá se především pro převod řetězců v aplikacích dvoubajtové znakové sady (DBCS).</span><span class="sxs-lookup"><span data-stu-id="03c28-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="03c28-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span><span class="sxs-lookup"><span data-stu-id="03c28-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03c28-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="03c28-130">Example</span></span>  
 <span data-ttu-id="03c28-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span><span class="sxs-lookup"><span data-stu-id="03c28-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="03c28-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03c28-132">Requirements</span></span>  
 <span data-ttu-id="03c28-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="03c28-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="03c28-134">**Module:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="03c28-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="03c28-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="03c28-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03c28-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03c28-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="03c28-137">Řetězce</span><span class="sxs-lookup"><span data-stu-id="03c28-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="03c28-138">Introduction to Strings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03c28-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
