---
title: MID – příkaz (Visual Basic)
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
ms.openlocfilehash: a653e63ded04616b6b0c6bdfb26a0a673d9299fc
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353457"
---
# <a name="mid-statement"></a><span data-ttu-id="84003-102">Mid – příkaz</span><span class="sxs-lookup"><span data-stu-id="84003-102">Mid Statement</span></span>
<span data-ttu-id="84003-103">Nahradí zadaný počet znaků `String` proměnné se znaky z jiného řetězce.</span><span class="sxs-lookup"><span data-stu-id="84003-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84003-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84003-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="84003-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="84003-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="84003-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="84003-106">Required.</span></span> <span data-ttu-id="84003-107">Název `String` proměnné, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="84003-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="84003-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="84003-108">Required.</span></span> <span data-ttu-id="84003-109">`Integer` výraz.</span><span class="sxs-lookup"><span data-stu-id="84003-109">`Integer` expression.</span></span> <span data-ttu-id="84003-110">Znak pozice v `Target` kde začne nahrazování textu.</span><span class="sxs-lookup"><span data-stu-id="84003-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="84003-111">`Start` používá indexu se základem 1.</span><span class="sxs-lookup"><span data-stu-id="84003-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="84003-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="84003-112">Optional.</span></span> <span data-ttu-id="84003-113">`Integer` výraz.</span><span class="sxs-lookup"><span data-stu-id="84003-113">`Integer` expression.</span></span> <span data-ttu-id="84003-114">Počet znaků k nahrazení.</span><span class="sxs-lookup"><span data-stu-id="84003-114">Number of characters to replace.</span></span> <span data-ttu-id="84003-115">Pokud tento parametr vynechán, všechny `String` se používá.</span><span class="sxs-lookup"><span data-stu-id="84003-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="84003-116">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="84003-116">Required.</span></span> <span data-ttu-id="84003-117">`String` výraz, který nahradí část `Target`.</span><span class="sxs-lookup"><span data-stu-id="84003-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="84003-118">Výjimky</span><span class="sxs-lookup"><span data-stu-id="84003-118">Exceptions</span></span>  
  
|<span data-ttu-id="84003-119">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="84003-119">Exception type</span></span>|<span data-ttu-id="84003-120">Podmínka</span><span class="sxs-lookup"><span data-stu-id="84003-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="84003-121">`Start` < = 0 nebo `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="84003-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84003-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84003-122">Remarks</span></span>  
 <span data-ttu-id="84003-123">Počet znaků, které nahradí je vždy menší než počet znaků v `Target`.</span><span class="sxs-lookup"><span data-stu-id="84003-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="84003-124">Visual Basic má <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkce a `Mid` příkazu.</span><span class="sxs-lookup"><span data-stu-id="84003-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="84003-125">Tyto prvky obou pracovat na zadaný počet znaků v řetězci, ale `Mid` funkce vrátí znaků při `Mid` příkaz nahradí znaky.</span><span class="sxs-lookup"><span data-stu-id="84003-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="84003-126">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="84003-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84003-127">`MidB` Příkaz předchozích verzí jazyka Visual Basic Nahradí podřetězec v bajtů namísto znaků.</span><span class="sxs-lookup"><span data-stu-id="84003-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="84003-128">Používá se především pro převod řetězců v aplikacích dvoubajtové znakové sady (DBCS).</span><span class="sxs-lookup"><span data-stu-id="84003-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="84003-129">Všechny řetězce jazyka Visual Basic jsou v kódování Unicode a `MidB` už není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="84003-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84003-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="84003-130">Example</span></span>  
 <span data-ttu-id="84003-131">V tomto příkladu `Mid` příkaz a nahraďte zadaný počet znaků v proměnné typu řetězec znaky z jiného řetězce.</span><span class="sxs-lookup"><span data-stu-id="84003-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="84003-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84003-132">Requirements</span></span>  
 <span data-ttu-id="84003-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="84003-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="84003-134">**Modul:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="84003-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="84003-135">**Sestavení:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84003-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84003-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="84003-136">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [<span data-ttu-id="84003-137">Řetězce</span><span class="sxs-lookup"><span data-stu-id="84003-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="84003-138">Úvod do řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84003-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
