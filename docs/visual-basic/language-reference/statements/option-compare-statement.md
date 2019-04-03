---
title: Option Compare – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: b092d54e6cf4d8a96a35e6b1cc818fad8f26e3ae
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834072"
---
# <a name="option-compare-statement"></a><span data-ttu-id="2b36a-102">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="2b36a-102">Option Compare Statement</span></span>
<span data-ttu-id="2b36a-103">Deklaruje výchozí metodu porovnání pro použití při porovnávání dat řetězců.</span><span class="sxs-lookup"><span data-stu-id="2b36a-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b36a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b36a-104">Syntax</span></span>  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="2b36a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="2b36a-105">Parts</span></span>  
  
|<span data-ttu-id="2b36a-106">Termín</span><span class="sxs-lookup"><span data-stu-id="2b36a-106">Term</span></span>|<span data-ttu-id="2b36a-107">Definice</span><span class="sxs-lookup"><span data-stu-id="2b36a-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="2b36a-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b36a-108">Optional.</span></span> <span data-ttu-id="2b36a-109">Výsledkem porovnání řetězců na základě pořadí řazení, odvozený z vnitřní binární reprezentace znaků.</span><span class="sxs-lookup"><span data-stu-id="2b36a-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="2b36a-110">Tento typ porovnání je užitečný zejména v případě, že jsou řetězce mohou obsahovat znaky, které nemají být interpretován jako text.</span><span class="sxs-lookup"><span data-stu-id="2b36a-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="2b36a-111">V takovém případě nechcete na posunu omezení porovnání s abecedním ekvivalence, jako je nerozlišování velikosti písmen.</span><span class="sxs-lookup"><span data-stu-id="2b36a-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="2b36a-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2b36a-112">Optional.</span></span> <span data-ttu-id="2b36a-113">Výsledky v závislosti na pořadí řazení nerozlišujícího velikost písmen textu určuje podle národního prostředí systému porovnávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="2b36a-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="2b36a-114">Tento typ porovnání je užitečné, pokud vaše řetězce obsahují všechny textové znaky, a vy chcete jejich porovnání s ohledem na abecední ekvivalence účtu, jako je nerozlišování velikosti písmen a úzce související písmena.</span><span class="sxs-lookup"><span data-stu-id="2b36a-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="2b36a-115">Například můžete chtít zvážit `A` a `a` musí rovnat, a `Ä` a `ä` před `B` a `b`.</span><span class="sxs-lookup"><span data-stu-id="2b36a-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b36a-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b36a-116">Remarks</span></span>  
 <span data-ttu-id="2b36a-117">Pokud použijete, `Option Compare` příkazu musí být uvedena v soubor předtím, než všechny ostatní příkazy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="2b36a-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="2b36a-118">`Option Compare` Příkaz určuje metodu porovnání řetězce (`Binary` nebo `Text`).</span><span class="sxs-lookup"><span data-stu-id="2b36a-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="2b36a-119">Výchozí metoda porovnání textu je `Binary`.</span><span class="sxs-lookup"><span data-stu-id="2b36a-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="2b36a-120">A `Binary` porovnání porovnává každý znak v každém řetězci číselnou hodnotu Unicode.</span><span class="sxs-lookup"><span data-stu-id="2b36a-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="2b36a-121">A `Text` porovnání porovnává každý znak Unicode podle jeho lexikální význam v aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="2b36a-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="2b36a-122">V Microsoft Windows pořadí řazení se určuje podle kódové stránky.</span><span class="sxs-lookup"><span data-stu-id="2b36a-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="2b36a-123">Další informace najdete v tématu [znakové stránky](/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="2b36a-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="2b36a-124">V následujícím příkladu, znaků v znakové stránce (ANSI 1252) Angličtina/Evropské řazená pomocí `Option Compare Binary`, který vytváří typické binární řazení.</span><span class="sxs-lookup"><span data-stu-id="2b36a-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="2b36a-125">Pokud řazená stejné znaky na stejné stránce kód pomocí `Option Compare Text`, je vytvořen textové řazení.</span><span class="sxs-lookup"><span data-stu-id="2b36a-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="2b36a-126">Když Option Compare – příkaz není k dispozici</span><span class="sxs-lookup"><span data-stu-id="2b36a-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="2b36a-127">Pokud zdrojový kód neobsahuje `Option Compare` příkazu **Option Compare** nastavení [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá.</span><span class="sxs-lookup"><span data-stu-id="2b36a-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="2b36a-128">Pokud používáte kompilátoru příkazového řádku, nastavení určená [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) – možnost kompilátoru je používá.</span><span class="sxs-lookup"><span data-stu-id="2b36a-128">If you use the command-line compiler, the setting specified by the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="2b36a-129">Nastavení Option Compare v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="2b36a-129">To set Option Compare in the IDE</span></span>  
  
1.  <span data-ttu-id="2b36a-130">V **Průzkumníka řešení**, vyberte projekt.</span><span class="sxs-lookup"><span data-stu-id="2b36a-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="2b36a-131">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="2b36a-131">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2b36a-132">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="2b36a-132">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="2b36a-133">Nastavte hodnotu **Option Compare** pole.</span><span class="sxs-lookup"><span data-stu-id="2b36a-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="2b36a-134">Při vytváření projektu, **Option Compare** nastavení **kompilaci** karty nastavená na **Option Compare** nastavení **možnosti** Dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="2b36a-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="2b36a-135">Chcete-li změnit toto nastavení, na **nástroje** nabídky, klikněte na tlačítko **možnosti**.</span><span class="sxs-lookup"><span data-stu-id="2b36a-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="2b36a-136">V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**.</span><span class="sxs-lookup"><span data-stu-id="2b36a-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="2b36a-137">Počáteční výchozí nastavení v **výchozí hodnoty pro VB** je **binární**.</span><span class="sxs-lookup"><span data-stu-id="2b36a-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="2b36a-138">Nastavení Option Compare na příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="2b36a-138">To set Option Compare on the command line</span></span>  
  
-   <span data-ttu-id="2b36a-139">Zahrnout [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) – možnost kompilátoru v **Vbc –** příkazu.</span><span class="sxs-lookup"><span data-stu-id="2b36a-139">Include the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b36a-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b36a-140">Example</span></span>  
 <span data-ttu-id="2b36a-141">V následujícím příkladu `Option Compare` příkaz nastavit jako výchozí metodu porovnání řetězce binární porovnání.</span><span class="sxs-lookup"><span data-stu-id="2b36a-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="2b36a-142">Chcete-li tento kód použít, Odkomentujte `Option Compare Binary` příkaz a umístěte ho na začátku zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="2b36a-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="2b36a-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b36a-143">Example</span></span>  
 <span data-ttu-id="2b36a-144">V následujícím příkladu `Option Compare` příkaz pro nastavení pořadí řazení nerozlišujícího velikost písmen textu jako výchozí metodu porovnání řetězce.</span><span class="sxs-lookup"><span data-stu-id="2b36a-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="2b36a-145">Chcete-li tento kód použít, Odkomentujte `Option Compare Text` příkaz a umístěte ho na začátku zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="2b36a-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="2b36a-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b36a-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="2b36a-147">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="2b36a-147">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="2b36a-148">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="2b36a-148">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="2b36a-149">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b36a-149">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="2b36a-150">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="2b36a-150">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="2b36a-151">Řetězcové funkce</span><span class="sxs-lookup"><span data-stu-id="2b36a-151">String Functions</span></span>](../../../visual-basic/language-reference/functions/string-functions.md)
- [<span data-ttu-id="2b36a-152">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="2b36a-152">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="2b36a-153">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="2b36a-153">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
