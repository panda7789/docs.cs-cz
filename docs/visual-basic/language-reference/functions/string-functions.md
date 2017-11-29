---
title: "Funkce řetězce (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7672f03cda99aa0e1dcecd79b0358f9d5f16f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="string-functions-visual-basic"></a><span data-ttu-id="2117d-102">Funkce řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2117d-102">String Functions (Visual Basic)</span></span>
<span data-ttu-id="2117d-103">Následující tabulka uvádí funkce, které Visual Basic poskytuje k vyhledávání a manipulaci s řetězci.</span><span class="sxs-lookup"><span data-stu-id="2117d-103">The following table lists the functions that Visual Basic provides to search and manipulate strings.</span></span>  
  
|<span data-ttu-id="2117d-104">Rozhraní .NET framework – metoda</span><span class="sxs-lookup"><span data-stu-id="2117d-104">.NET Framework method</span></span>|<span data-ttu-id="2117d-105">Popis</span><span class="sxs-lookup"><span data-stu-id="2117d-105">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="2117d-106"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="2117d-106"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>|<span data-ttu-id="2117d-107">Vrátí `Integer` hodnotu představující kód odpovídající znaku.</span><span class="sxs-lookup"><span data-stu-id="2117d-107">Returns an `Integer` value representing the character code corresponding to a character.</span></span>|  
|<span data-ttu-id="2117d-108"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="2117d-108"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>|<span data-ttu-id="2117d-109">Vrací znak přiřazený k určenému kódu znaku.</span><span class="sxs-lookup"><span data-stu-id="2117d-109">Returns the character associated with the specified character code.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|<span data-ttu-id="2117d-110">Vrátí pole s nulovým základem obsahující dílčí sadu `String` pole podle zadaných kritérií filtru.</span><span class="sxs-lookup"><span data-stu-id="2117d-110">Returns a zero-based array containing a subset of a `String` array based on specified filter criteria.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|<span data-ttu-id="2117d-111">Vrací řetězec formátovaný podle pokynů obsažených ve formátu `String` výraz.</span><span class="sxs-lookup"><span data-stu-id="2117d-111">Returns a string formatted according to instructions contained in a format `String` expression.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|<span data-ttu-id="2117d-112">Vrací výraz formátovaný jako hodnota měny pomocí symbolu měny definovaného v Ovládacích panelech systému.</span><span class="sxs-lookup"><span data-stu-id="2117d-112">Returns an expression formatted as a currency value using the currency symbol defined in the system control panel.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|<span data-ttu-id="2117d-113">Vrací výraz řetězce představující hodnotu data a času.</span><span class="sxs-lookup"><span data-stu-id="2117d-113">Returns a string expression representing a date/time value.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|<span data-ttu-id="2117d-114">Vrací výraz formátovaný jako číslo.</span><span class="sxs-lookup"><span data-stu-id="2117d-114">Returns an expression formatted as a number.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|<span data-ttu-id="2117d-115">Vrací výraz formátovaný jako procento (tj, násobenou 100) s znakem %.</span><span class="sxs-lookup"><span data-stu-id="2117d-115">Returns an expression formatted as a percentage (that is, multiplied by 100) with a trailing % character.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|<span data-ttu-id="2117d-116">Vrátí celé číslo určující počáteční pozici prvního výskytu jednoho řetězce v jiném.</span><span class="sxs-lookup"><span data-stu-id="2117d-116">Returns an integer specifying the start position of the first occurrence of one string within another.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|<span data-ttu-id="2117d-117">Vrátí pozici prvního výskytu jednoho řetězce v rámci druhého, počínaje z pravé strany řetězce.</span><span class="sxs-lookup"><span data-stu-id="2117d-117">Returns the position of the first occurrence of one string within another, starting from the right side of the string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|<span data-ttu-id="2117d-118">Vrací řetězec vytvořený sloučením několika dílčích řetězců obsažených v poli.</span><span class="sxs-lookup"><span data-stu-id="2117d-118">Returns a string created by joining a number of substrings contained in an array.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|<span data-ttu-id="2117d-119">Vrací řetězec nebo znak převedený na malá písmena.</span><span class="sxs-lookup"><span data-stu-id="2117d-119">Returns a string or character converted to lowercase.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|<span data-ttu-id="2117d-120">Vrací řetězec obsahující určený počet znaků z řetězce levé strany.</span><span class="sxs-lookup"><span data-stu-id="2117d-120">Returns a string containing a specified number of characters from the left side of a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|<span data-ttu-id="2117d-121">Vrátí celé číslo, které obsahuje počet znaků v řetězci.</span><span class="sxs-lookup"><span data-stu-id="2117d-121">Returns an integer that contains the number of characters in a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|<span data-ttu-id="2117d-122">Vrací vlevo zarovnaný řetězec obsahující určený řetězec přizpůsobený na určenou délku.</span><span class="sxs-lookup"><span data-stu-id="2117d-122">Returns a left-aligned string containing the specified string adjusted to the specified length.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|<span data-ttu-id="2117d-123">Vrací řetězec obsahující kopii určeného řetězce bez mezer na začátku.</span><span class="sxs-lookup"><span data-stu-id="2117d-123">Returns a string containing a copy of a specified string with no leading spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|<span data-ttu-id="2117d-124">Vrací řetězec obsahující určený počet znaků z řetězce.</span><span class="sxs-lookup"><span data-stu-id="2117d-124">Returns a string containing a specified number of characters from a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|<span data-ttu-id="2117d-125">Vrátí řetězec, ve kterém je určený dílčí řetězec má nahrazen jiným dílčím řetězcem zadaného počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="2117d-125">Returns a string in which a specified substring has been replaced with another substring a specified number of times.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|<span data-ttu-id="2117d-126">Vrací řetězec obsahující určený počet znaků z pravé strany řetězce.</span><span class="sxs-lookup"><span data-stu-id="2117d-126">Returns a string containing a specified number of characters from the right side of a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|<span data-ttu-id="2117d-127">Vrací vpravo zarovnaný řetězec obsahující určený řetězec přizpůsobený na určenou délku.</span><span class="sxs-lookup"><span data-stu-id="2117d-127">Returns a right-aligned string containing the specified string adjusted to the specified length.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|<span data-ttu-id="2117d-128">Vrací řetězec obsahující kopii určeného řetězce koncové mezery.</span><span class="sxs-lookup"><span data-stu-id="2117d-128">Returns a string containing a copy of a specified string with no trailing spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|<span data-ttu-id="2117d-129">Vrací řetězec sestávající z určeného počtu mezer.</span><span class="sxs-lookup"><span data-stu-id="2117d-129">Returns a string consisting of the specified number of spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|<span data-ttu-id="2117d-130">Vrátí nule jednorozměrné pole obsahující určený počet dílčích řetězců.</span><span class="sxs-lookup"><span data-stu-id="2117d-130">Returns a zero-based, one-dimensional array containing a specified number of substrings.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|<span data-ttu-id="2117d-131">Vrátí hodnotu -1, 0 nebo 1, na základě výsledku porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="2117d-131">Returns -1, 0, or 1, based on the result of a string comparison.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|<span data-ttu-id="2117d-132">Vrací řetězec převedený podle určení.</span><span class="sxs-lookup"><span data-stu-id="2117d-132">Returns a string converted as specified.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|<span data-ttu-id="2117d-133">Vrátí řetězec nebo objekt sestávající z určeného znaku opakuje zadaného počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="2117d-133">Returns a string or object consisting of the specified character repeated the specified number of times.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|<span data-ttu-id="2117d-134">Vrátí řetězec, ve kterém je pořadí znaků z určeného řetězce obrácený.</span><span class="sxs-lookup"><span data-stu-id="2117d-134">Returns a string in which the character order of a specified string is reversed.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|<span data-ttu-id="2117d-135">Vrací řetězec obsahující kopii určeného řetězce bez mezer na začátku nebo na konci.</span><span class="sxs-lookup"><span data-stu-id="2117d-135">Returns a string containing a copy of a specified string with no leading or trailing spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|<span data-ttu-id="2117d-136">Vrací řetězec nebo znak obsahující určený řetězec převedený na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="2117d-136">Returns a string or character containing the specified string converted to uppercase.</span></span>|  
  
 <span data-ttu-id="2117d-137">Můžete použít [možnost porovnat](../../../visual-basic/language-reference/statements/option-compare-statement.md) pořadí dáno národního prostředí vašeho systému řazení příkaz, který má-li nastavit, jestli jsou porovnány pomocí velká a malá písmena textového řetězce (`Text`) nebo interní binární reprezentace (znaků `Binary`).</span><span class="sxs-lookup"><span data-stu-id="2117d-137">You can use the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) statement to set whether strings are compared using a case-insensitive text sort order determined by your system's locale (`Text`) or by the internal binary representations of the characters (`Binary`).</span></span> <span data-ttu-id="2117d-138">Výchozí metoda porovnání textu je `Binary`.</span><span class="sxs-lookup"><span data-stu-id="2117d-138">The default text comparison method is `Binary`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2117d-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="2117d-139">Example</span></span>  
 <span data-ttu-id="2117d-140">Tento příklad používá `UCase` funkci vrátíte verzi řetězec s velkými písmeny.</span><span class="sxs-lookup"><span data-stu-id="2117d-140">This example uses the `UCase` function to return an uppercase version of a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#31](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="2117d-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="2117d-141">Example</span></span>  
 <span data-ttu-id="2117d-142">Tento příklad používá `LTrim` funkce oddělit úvodní mezery a `RTrim` funkce oddělit koncové mezery z proměnné řetězce.</span><span class="sxs-lookup"><span data-stu-id="2117d-142">This example uses the `LTrim` function to strip leading spaces and the `RTrim` function to strip trailing spaces from a string variable.</span></span> <span data-ttu-id="2117d-143">Použije `Trim` funkce pro odstranění obou typů prostory.</span><span class="sxs-lookup"><span data-stu-id="2117d-143">It uses the `Trim` function to strip both types of spaces.</span></span>  
  
 [!code-vb[VbVbalrStrings#25](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="2117d-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="2117d-144">Example</span></span>  
 <span data-ttu-id="2117d-145">Tento příklad používá `Mid` funkce vrací zadaný počet znaků z řetězce.</span><span class="sxs-lookup"><span data-stu-id="2117d-145">This example uses the `Mid` function to return a specified number of characters from a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="2117d-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="2117d-146">Example</span></span>  
 <span data-ttu-id="2117d-147">Tento příklad používá `Len` k vrátí počet znaků v řetězci.</span><span class="sxs-lookup"><span data-stu-id="2117d-147">This example uses `Len` to return the number of characters in a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#33](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="2117d-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="2117d-148">Example</span></span>  
 <span data-ttu-id="2117d-149">Tento příklad používá `InStr` funkce vrací pozici prvního výskytu jednoho řetězce v jiném.</span><span class="sxs-lookup"><span data-stu-id="2117d-149">This example uses the `InStr` function to return the position of the first occurrence of one string within another.</span></span>  
  
 [!code-vb[VbVbalrStrings#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="2117d-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="2117d-150">Example</span></span>  
 <span data-ttu-id="2117d-151">Tento příklad ukazuje použití různých `Format` funkce, která má formát hodnoty pomocí obou `String` formátů a uživatelem definované formátů.</span><span class="sxs-lookup"><span data-stu-id="2117d-151">This example shows various uses of the `Format` function to format values using both `String` formats and user-defined formats.</span></span> <span data-ttu-id="2117d-152">Pro oddělovač data (`/`), oddělovač času (`:`) a indikátory dop. / odp (`t` a `tt`), aktuální formátovaný výstup zobrazí systém závisí na nastavení národního prostředí je pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="2117d-152">For the date separator (`/`), time separator (`:`), and the AM/PM indicators (`t` and `tt`), the actual formatted output displayed by your system depends on the locale settings the code is using.</span></span> <span data-ttu-id="2117d-153">Když časy a data se zobrazují ve vývojovém prostředí, používají formát krátkého času a formát krátkého data kód národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="2117d-153">When times and dates are displayed in the development environment, the short time format and short date format of the code locale are used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2117d-154">Pro národní prostředí, které používají 24hodinovém formátu indikátory dop. / odp (`t` a `tt`) zobrazit prázdnou.</span><span class="sxs-lookup"><span data-stu-id="2117d-154">For locales that use a 24-hour clock, the AM/PM indicators (`t` and `tt`) display nothing.</span></span>  
  
 [!code-vb[VbVbalrStrings#27](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2117d-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="2117d-155">See Also</span></span>  
 [<span data-ttu-id="2117d-156">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2117d-156">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="2117d-157">Členové knihovny prostředí Runtime jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2117d-157">Visual Basic Runtime Library Members</span></span>](../../../visual-basic/language-reference/runtime-library-members.md)  
 [<span data-ttu-id="2117d-158">Souhrn manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="2117d-158">String Manipulation Summary</span></span>](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
