---
title: Mid – příkaz (Visual Basic)
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
ms.openlocfilehash: ea22af2eb896542bfc329e087101608e08c45107
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581479"
---
# <a name="mid-statement"></a><span data-ttu-id="c7b50-102">Mid – příkaz</span><span class="sxs-lookup"><span data-stu-id="c7b50-102">Mid Statement</span></span>
<span data-ttu-id="c7b50-103">Nahradí zadaný počet znaků v proměnné `String` znaky z jiného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c7b50-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7b50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7b50-104">Syntax</span></span>  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="c7b50-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c7b50-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="c7b50-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c7b50-106">Required.</span></span> <span data-ttu-id="c7b50-107">Název proměnné `String`, kterou chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="c7b50-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="c7b50-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c7b50-108">Required.</span></span> <span data-ttu-id="c7b50-109">výraz `Integer`</span><span class="sxs-lookup"><span data-stu-id="c7b50-109">`Integer` expression.</span></span> <span data-ttu-id="c7b50-110">Pozice znaku v `Target`, kde začíná nahrazování textu.</span><span class="sxs-lookup"><span data-stu-id="c7b50-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="c7b50-111">`Start` používá index založený na jednom.</span><span class="sxs-lookup"><span data-stu-id="c7b50-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="c7b50-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c7b50-112">Optional.</span></span> <span data-ttu-id="c7b50-113">výraz `Integer`</span><span class="sxs-lookup"><span data-stu-id="c7b50-113">`Integer` expression.</span></span> <span data-ttu-id="c7b50-114">Počet znaků, které mají být nahrazeny.</span><span class="sxs-lookup"><span data-stu-id="c7b50-114">Number of characters to replace.</span></span> <span data-ttu-id="c7b50-115">Je-li tento parametr vynechán, je použita veškerá `String`.</span><span class="sxs-lookup"><span data-stu-id="c7b50-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="c7b50-116">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c7b50-116">Required.</span></span> <span data-ttu-id="c7b50-117">výraz `String`, který nahrazuje část `Target`.</span><span class="sxs-lookup"><span data-stu-id="c7b50-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="c7b50-118">Výjimky</span><span class="sxs-lookup"><span data-stu-id="c7b50-118">Exceptions</span></span>  
  
|<span data-ttu-id="c7b50-119">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="c7b50-119">Exception type</span></span>|<span data-ttu-id="c7b50-120">Podmínka</span><span class="sxs-lookup"><span data-stu-id="c7b50-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="c7b50-121">`Start` < = 0 nebo `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="c7b50-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7b50-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7b50-122">Remarks</span></span>  
 <span data-ttu-id="c7b50-123">Počet nahrazených znaků je vždy menší nebo roven počtu znaků v `Target`.</span><span class="sxs-lookup"><span data-stu-id="c7b50-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="c7b50-124">Visual Basic má funkci <xref:Microsoft.VisualBasic.Strings.Mid%2A> a příkaz `Mid`.</span><span class="sxs-lookup"><span data-stu-id="c7b50-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="c7b50-125">Tyto prvky fungují na zadaném počtu znaků v řetězci, ale funkce `Mid` vrátí znaky, zatímco příkaz `Mid` nahrazuje znaky.</span><span class="sxs-lookup"><span data-stu-id="c7b50-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="c7b50-126">Další informace najdete v tématu <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7b50-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7b50-127">Příkaz `MidB` starších verzí Visual Basic nahrazuje podřetězec v bajtech namísto znaků.</span><span class="sxs-lookup"><span data-stu-id="c7b50-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="c7b50-128">Používá se především pro převod řetězců v aplikacích dvoubajtové znakové sady (DBCS).</span><span class="sxs-lookup"><span data-stu-id="c7b50-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="c7b50-129">Všechny Visual Basic řetězce jsou v kódování Unicode a `MidB` již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="c7b50-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7b50-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7b50-130">Example</span></span>  
 <span data-ttu-id="c7b50-131">V tomto příkladu se používá příkaz `Mid` k nahrazení zadaného počtu znaků v řetězcové proměnné znaky z jiného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c7b50-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="c7b50-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7b50-132">Requirements</span></span>  
 <span data-ttu-id="c7b50-133">**Obor názvů:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="c7b50-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="c7b50-134">**Modul:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="c7b50-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="c7b50-135">**Sestavení:** Knihovna Visual Basic runtime (v souboru Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="c7b50-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b50-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7b50-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="c7b50-137">Řetězce</span><span class="sxs-lookup"><span data-stu-id="c7b50-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="c7b50-138">Seznámení s řetězci v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7b50-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
