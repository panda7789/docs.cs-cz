---
title: Funkce řetězce (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 917797700c3e403971ce6f48174a282b1102f127
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799318"
---
# <a name="string-functions-visual-basic"></a><span data-ttu-id="4fb99-102">Funkce řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fb99-102">String Functions (Visual Basic)</span></span>

<span data-ttu-id="4fb99-103">V následující tabulce jsou uvedeny funkce, které Visual Basic poskytuje ve <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> třídě pro hledání a manipulaci s řetězci.</span><span class="sxs-lookup"><span data-stu-id="4fb99-103">The following table lists the functions that Visual Basic provides in the <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> class to search and manipulate strings.</span></span> <span data-ttu-id="4fb99-104">Je možné je považovat za Visual Basic vnitřních funkcí; To znamená, že je nemusíte volat jako explicitní členy třídy, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="4fb99-104">They can be regarded as Visual Basic intrinsic functions; that is, you do not have to call them as explicit members of a class, as the examples show.</span></span> <span data-ttu-id="4fb99-105">Další metody a v některých případech doplňkové metody jsou k dispozici ve <xref:System.String?displayProperty=nameWithType> třídě.</span><span class="sxs-lookup"><span data-stu-id="4fb99-105">Additional methods, and in some cases complementary methods, are available in the <xref:System.String?displayProperty=nameWithType> class.</span></span> 
  
|<span data-ttu-id="4fb99-106">.NET Framework – metoda</span><span class="sxs-lookup"><span data-stu-id="4fb99-106">.NET Framework method</span></span>|<span data-ttu-id="4fb99-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4fb99-107">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="4fb99-108"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="4fb99-108"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>|<span data-ttu-id="4fb99-109">`Integer` Vrátí hodnotu představující kód znaku odpovídající znaku.</span><span class="sxs-lookup"><span data-stu-id="4fb99-109">Returns an `Integer` value representing the character code corresponding to a character.</span></span>|  
|<span data-ttu-id="4fb99-110"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="4fb99-110"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>|<span data-ttu-id="4fb99-111">Vrátí znak přiřazený k určenému kódu znaku.</span><span class="sxs-lookup"><span data-stu-id="4fb99-111">Returns the character associated with the specified character code.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|<span data-ttu-id="4fb99-112">Vrací pole s nulovým základem obsahující podmnožinu `String` pole na základě zadaných kritérií filtru.</span><span class="sxs-lookup"><span data-stu-id="4fb99-112">Returns a zero-based array containing a subset of a `String` array based on specified filter criteria.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|<span data-ttu-id="4fb99-113">Vrátí řetězec formátovaný podle pokynů obsažených ve výrazu formátu `String` .</span><span class="sxs-lookup"><span data-stu-id="4fb99-113">Returns a string formatted according to instructions contained in a format `String` expression.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|<span data-ttu-id="4fb99-114">Vrací výraz formátovaný jako hodnota měny pomocí symbolu měny definovaného na ovládacím panelu systému.</span><span class="sxs-lookup"><span data-stu-id="4fb99-114">Returns an expression formatted as a currency value using the currency symbol defined in the system control panel.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|<span data-ttu-id="4fb99-115">Vrátí řetězcový výraz představující hodnotu data a času.</span><span class="sxs-lookup"><span data-stu-id="4fb99-115">Returns a string expression representing a date/time value.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|<span data-ttu-id="4fb99-116">Vrátí výraz formátovaný jako číslo.</span><span class="sxs-lookup"><span data-stu-id="4fb99-116">Returns an expression formatted as a number.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|<span data-ttu-id="4fb99-117">Vrátí výraz formátovaný jako procento (vynásobený 100) s koncovým znakem%.</span><span class="sxs-lookup"><span data-stu-id="4fb99-117">Returns an expression formatted as a percentage (that is, multiplied by 100) with a trailing % character.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|<span data-ttu-id="4fb99-118">Vrací celé číslo určující počáteční pozici prvního výskytu jednoho řetězce v rámci druhého.</span><span class="sxs-lookup"><span data-stu-id="4fb99-118">Returns an integer specifying the start position of the first occurrence of one string within another.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|<span data-ttu-id="4fb99-119">Vrátí pozici prvního výskytu jednoho řetězce v rámci druhého počínaje od pravé strany řetězce.</span><span class="sxs-lookup"><span data-stu-id="4fb99-119">Returns the position of the first occurrence of one string within another, starting from the right side of the string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|<span data-ttu-id="4fb99-120">Vrátí řetězec vytvořený spojením několika podřetězců obsažených v poli.</span><span class="sxs-lookup"><span data-stu-id="4fb99-120">Returns a string created by joining a number of substrings contained in an array.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|<span data-ttu-id="4fb99-121">Vrátí řetězec nebo znak převedený na malá písmena.</span><span class="sxs-lookup"><span data-stu-id="4fb99-121">Returns a string or character converted to lowercase.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|<span data-ttu-id="4fb99-122">Vrátí řetězec obsahující zadaný počet znaků od levé strany řetězce.</span><span class="sxs-lookup"><span data-stu-id="4fb99-122">Returns a string containing a specified number of characters from the left side of a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|<span data-ttu-id="4fb99-123">Vrátí celé číslo, které obsahuje počet znaků v řetězci.</span><span class="sxs-lookup"><span data-stu-id="4fb99-123">Returns an integer that contains the number of characters in a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|<span data-ttu-id="4fb99-124">Vrátí řetězec zarovnaný doleva obsahující zadaný řetězec upravený na zadanou délku.</span><span class="sxs-lookup"><span data-stu-id="4fb99-124">Returns a left-aligned string containing the specified string adjusted to the specified length.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|<span data-ttu-id="4fb99-125">Vrátí řetězec obsahující kopii zadaného řetězce bez počátečních mezer.</span><span class="sxs-lookup"><span data-stu-id="4fb99-125">Returns a string containing a copy of a specified string with no leading spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|<span data-ttu-id="4fb99-126">Vrátí řetězec obsahující zadaný počet znaků z řetězce.</span><span class="sxs-lookup"><span data-stu-id="4fb99-126">Returns a string containing a specified number of characters from a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|<span data-ttu-id="4fb99-127">Vrátí řetězec, ve kterém byl zadaný dílčí řetězec nahrazen jiným dílčím řetězcem, který je určený počtem opakování.</span><span class="sxs-lookup"><span data-stu-id="4fb99-127">Returns a string in which a specified substring has been replaced with another substring a specified number of times.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|<span data-ttu-id="4fb99-128">Vrátí řetězec obsahující zadaný počet znaků z pravé strany řetězce.</span><span class="sxs-lookup"><span data-stu-id="4fb99-128">Returns a string containing a specified number of characters from the right side of a string.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|<span data-ttu-id="4fb99-129">Vrátí řetězec zarovnaný doprava obsahující zadaný řetězec upravený na zadanou délku.</span><span class="sxs-lookup"><span data-stu-id="4fb99-129">Returns a right-aligned string containing the specified string adjusted to the specified length.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|<span data-ttu-id="4fb99-130">Vrátí řetězec obsahující kopii zadaného řetězce bez koncových mezer.</span><span class="sxs-lookup"><span data-stu-id="4fb99-130">Returns a string containing a copy of a specified string with no trailing spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|<span data-ttu-id="4fb99-131">Vrátí řetězec sestávající z určeného počtu mezer.</span><span class="sxs-lookup"><span data-stu-id="4fb99-131">Returns a string consisting of the specified number of spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|<span data-ttu-id="4fb99-132">Vrací jednorozměrné pole s nulovým základem obsahující určený počet podřetězců.</span><span class="sxs-lookup"><span data-stu-id="4fb99-132">Returns a zero-based, one-dimensional array containing a specified number of substrings.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|<span data-ttu-id="4fb99-133">Vrátí hodnotu-1, 0 nebo 1 na základě výsledku porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="4fb99-133">Returns -1, 0, or 1, based on the result of a string comparison.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|<span data-ttu-id="4fb99-134">Vrátí řetězec převedený podle zadání.</span><span class="sxs-lookup"><span data-stu-id="4fb99-134">Returns a string converted as specified.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|<span data-ttu-id="4fb99-135">Vrátí řetězec nebo objekt skládající se ze zadaného znaku, který se opakuje po zadaném počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="4fb99-135">Returns a string or object consisting of the specified character repeated the specified number of times.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|<span data-ttu-id="4fb99-136">Vrátí řetězec, ve kterém je obráceno pořadí znaků zadaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="4fb99-136">Returns a string in which the character order of a specified string is reversed.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|<span data-ttu-id="4fb99-137">Vrátí řetězec obsahující kopii zadaného řetězce bez mezer na začátku nebo na konci.</span><span class="sxs-lookup"><span data-stu-id="4fb99-137">Returns a string containing a copy of a specified string with no leading or trailing spaces.</span></span>|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|<span data-ttu-id="4fb99-138">Vrátí řetězec nebo znak obsahující určený řetězec převedený na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="4fb99-138">Returns a string or character containing the specified string converted to uppercase.</span></span>|  
  
 <span data-ttu-id="4fb99-139">Můžete použít příkaz [Compare Option](../../../visual-basic/language-reference/statements/option-compare-statement.md) k nastavení, zda jsou řetězce porovnány pomocí pořadí řazení textu bez ohledu na velikost písmen určeného národním prostředím systému (`Text`) nebo vnitřními binárními reprezentacemi znaků (`Binary`).</span><span class="sxs-lookup"><span data-stu-id="4fb99-139">You can use the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) statement to set whether strings are compared using a case-insensitive text sort order determined by your system's locale (`Text`) or by the internal binary representations of the characters (`Binary`).</span></span> <span data-ttu-id="4fb99-140">Výchozí metoda porovnání textu je `Binary`.</span><span class="sxs-lookup"><span data-stu-id="4fb99-140">The default text comparison method is `Binary`.</span></span>  
  
## <a name="example-ucase"></a><span data-ttu-id="4fb99-141">Příklad: UCase</span><span class="sxs-lookup"><span data-stu-id="4fb99-141">Example: UCase</span></span>

<span data-ttu-id="4fb99-142">Tento příklad používá `UCase` funkci k vrácení velkých a malých písmen řetězce.</span><span class="sxs-lookup"><span data-stu-id="4fb99-142">This example uses the `UCase` function to return an uppercase version of a string.</span></span>  
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]  
  
## <a name="example-ltrim"></a><span data-ttu-id="4fb99-143">Příklad: LTrim</span><span class="sxs-lookup"><span data-stu-id="4fb99-143">Example: LTrim</span></span>

<span data-ttu-id="4fb99-144">Tento příklad používá `LTrim` funkci k obložení úvodních mezer `RTrim` a funkce pro obložení koncových mezer z řetězcové proměnné.</span><span class="sxs-lookup"><span data-stu-id="4fb99-144">This example uses the `LTrim` function to strip leading spaces and the `RTrim` function to strip trailing spaces from a string variable.</span></span> <span data-ttu-id="4fb99-145">Používá `Trim` funkci pro odložení obou typů mezer.</span><span class="sxs-lookup"><span data-stu-id="4fb99-145">It uses the `Trim` function to strip both types of spaces.</span></span>  
  
[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]  
  
## <a name="example-mid"></a><span data-ttu-id="4fb99-146">Příklad: Mid</span><span class="sxs-lookup"><span data-stu-id="4fb99-146">Example: Mid</span></span>

<span data-ttu-id="4fb99-147">Tento příklad používá `Mid` funkci k vrácení zadaného počtu znaků z řetězce.</span><span class="sxs-lookup"><span data-stu-id="4fb99-147">This example uses the `Mid` function to return a specified number of characters from a string.</span></span>  

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]  

## <a name="example-len"></a><span data-ttu-id="4fb99-148">Příklad: Funkce</span><span class="sxs-lookup"><span data-stu-id="4fb99-148">Example: Len</span></span>

<span data-ttu-id="4fb99-149">Tento příklad používá `Len` k vrácení počtu znaků v řetězci.</span><span class="sxs-lookup"><span data-stu-id="4fb99-149">This example uses `Len` to return the number of characters in a string.</span></span>  
  
[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]  
  
## <a name="example-instr"></a><span data-ttu-id="4fb99-150">Příklad: InStr</span><span class="sxs-lookup"><span data-stu-id="4fb99-150">Example: InStr</span></span>

<span data-ttu-id="4fb99-151">Tento příklad používá `InStr` funkci k vrácení pozice prvního výskytu jednoho řetězce v jiném.</span><span class="sxs-lookup"><span data-stu-id="4fb99-151">This example uses the `InStr` function to return the position of the first occurrence of one string within another.</span></span>  
  
[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]  
  
## <a name="example-format"></a><span data-ttu-id="4fb99-152">Příklad: Formát</span><span class="sxs-lookup"><span data-stu-id="4fb99-152">Example: Format</span></span>

<span data-ttu-id="4fb99-153">Tento příklad ukazuje různá použití `Format` funkce pro formátování hodnot `String` pomocí formátů i uživatelsky definovaných formátů.</span><span class="sxs-lookup"><span data-stu-id="4fb99-153">This example shows various uses of the `Format` function to format values using both `String` formats and user-defined formats.</span></span> <span data-ttu-id="4fb99-154">V případě oddělovače data`/`(), oddělovače`:`času () a indikátory AM/PM`t` ( `tt`a) je skutečný formátovaný výstup zobrazený systémem závislý na nastavení národního prostředí, které kód používá.</span><span class="sxs-lookup"><span data-stu-id="4fb99-154">For the date separator (`/`), time separator (`:`), and the AM/PM indicators (`t` and `tt`), the actual formatted output displayed by your system depends on the locale settings the code is using.</span></span> <span data-ttu-id="4fb99-155">Když jsou časy a kalendářní data zobrazeny ve vývojovém prostředí, je použit krátký formát času a formát krátkého data národního prostředí kódu.</span><span class="sxs-lookup"><span data-stu-id="4fb99-155">When times and dates are displayed in the development environment, the short time format and short date format of the code locale are used.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fb99-156">Pro národní prostředí, která používají 24hodinové hodiny, se indikátory AM/PM (`t` a `tt`) nezobrazí nic.</span><span class="sxs-lookup"><span data-stu-id="4fb99-156">For locales that use a 24-hour clock, the AM/PM indicators (`t` and `tt`) display nothing.</span></span>  
  
 [!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="4fb99-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fb99-157">See also</span></span>

- [<span data-ttu-id="4fb99-158">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="4fb99-158">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="4fb99-159">Členové knihovny modulu runtime jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4fb99-159">Visual Basic Runtime Library Members</span></span>](../../../visual-basic/language-reference/runtime-library-members.md)
- [<span data-ttu-id="4fb99-160">Souhrn manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="4fb99-160">String Manipulation Summary</span></span>](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
- <span data-ttu-id="4fb99-161">[Metody třídy System. String]<xref:System.String#methods?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4fb99-161">[System.String class methods]<xref:System.String#methods?displayProperty=nameWithType></span></span>
