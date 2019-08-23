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
ms.openlocfilehash: 212ce1f06a01c39acbce43d8d069dae3526b1b4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963554"
---
# <a name="mid-statement"></a><span data-ttu-id="eb6a3-102">Mid – příkaz</span><span class="sxs-lookup"><span data-stu-id="eb6a3-102">Mid Statement</span></span>
<span data-ttu-id="eb6a3-103">Nahradí zadaný počet znaků v `String` proměnné znaky z jiného řetězce.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb6a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb6a3-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="eb6a3-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="eb6a3-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="eb6a3-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-106">Required.</span></span> <span data-ttu-id="eb6a3-107">`String` Název proměnné, která se má změnit</span><span class="sxs-lookup"><span data-stu-id="eb6a3-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="eb6a3-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-108">Required.</span></span> <span data-ttu-id="eb6a3-109">`Integer`vyjádření.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-109">`Integer` expression.</span></span> <span data-ttu-id="eb6a3-110">Pozice znaku, `Target` kde začíná nahrazování textu.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="eb6a3-111">`Start`používá index založený na jednom.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="eb6a3-112">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-112">Optional.</span></span> <span data-ttu-id="eb6a3-113">`Integer`vyjádření.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-113">`Integer` expression.</span></span> <span data-ttu-id="eb6a3-114">Počet znaků, které mají být nahrazeny.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-114">Number of characters to replace.</span></span> <span data-ttu-id="eb6a3-115">`String` Je-li tento parametr vynechán, je použita hodnota all.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="eb6a3-116">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-116">Required.</span></span> <span data-ttu-id="eb6a3-117">`String`výraz, který nahrazuje část `Target`.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="eb6a3-118">Výjimky</span><span class="sxs-lookup"><span data-stu-id="eb6a3-118">Exceptions</span></span>  
  
|<span data-ttu-id="eb6a3-119">Typ výjimky</span><span class="sxs-lookup"><span data-stu-id="eb6a3-119">Exception type</span></span>|<span data-ttu-id="eb6a3-120">Podmínka</span><span class="sxs-lookup"><span data-stu-id="eb6a3-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="eb6a3-121">`Start`< = 0 nebo `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb6a3-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb6a3-122">Remarks</span></span>  
 <span data-ttu-id="eb6a3-123">Počet nahrazených znaků je vždy menší nebo roven počtu znaků v `Target`.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="eb6a3-124">Visual Basic má <xref:Microsoft.VisualBasic.Strings.Mid%2A> funkci `Mid` a příkaz.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="eb6a3-125">Tyto prvky jsou provozovány na zadaném počtu znaků v řetězci, ale `Mid` funkce vrátí znaky, `Mid` zatímco příkaz nahradí znaky.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="eb6a3-126">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb6a3-127">`MidB` Příkaz starší verze Visual Basic nahrazuje podřetězec v bajtech namísto znaků.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="eb6a3-128">Používá se především pro převod řetězců v aplikacích dvoubajtové znakové sady (DBCS).</span><span class="sxs-lookup"><span data-stu-id="eb6a3-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="eb6a3-129">Všechny Visual Basic řetězce jsou v kódování Unicode a `MidB` již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb6a3-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb6a3-130">Example</span></span>  
 <span data-ttu-id="eb6a3-131">V `Mid` tomto příkladu se používá příkaz k nahrazení zadaného počtu znaků v řetězcové proměnné znaky z jiného řetězce.</span><span class="sxs-lookup"><span data-stu-id="eb6a3-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="eb6a3-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb6a3-132">Requirements</span></span>  
 <span data-ttu-id="eb6a3-133">**Hosting** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="eb6a3-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="eb6a3-134">**Modul:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="eb6a3-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="eb6a3-135">**Shromážděním** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="eb6a3-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6a3-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb6a3-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="eb6a3-137">Řetězce</span><span class="sxs-lookup"><span data-stu-id="eb6a3-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="eb6a3-138">Seznámení s řetězci v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb6a3-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
