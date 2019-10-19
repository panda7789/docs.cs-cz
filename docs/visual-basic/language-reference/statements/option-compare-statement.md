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
ms.openlocfilehash: 43d3faf3a6630cd308913ce2325a5f7fe96e474c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581589"
---
# <a name="option-compare-statement"></a><span data-ttu-id="54672-102">Option Compare – příkaz</span><span class="sxs-lookup"><span data-stu-id="54672-102">Option Compare Statement</span></span>
<span data-ttu-id="54672-103">Deklaruje výchozí metodu porovnání, která se má použít při porovnávání řetězcových dat.</span><span class="sxs-lookup"><span data-stu-id="54672-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54672-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54672-104">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="54672-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="54672-105">Parts</span></span>  
  
|<span data-ttu-id="54672-106">Termín</span><span class="sxs-lookup"><span data-stu-id="54672-106">Term</span></span>|<span data-ttu-id="54672-107">Definice</span><span class="sxs-lookup"><span data-stu-id="54672-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="54672-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="54672-108">Optional.</span></span> <span data-ttu-id="54672-109">Výsledkem porovnání řetězců na základě pořadí řazení odvozeného z interních binárních reprezentace znaků.</span><span class="sxs-lookup"><span data-stu-id="54672-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="54672-110">Tento typ porovnání je užitečný hlavně v případě, že řetězce můžou obsahovat znaky, které nemusíte interpretovat jako text.</span><span class="sxs-lookup"><span data-stu-id="54672-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="54672-111">V takovém případě nebudete chtít porovnání posunu s abecedními ekvivalenty, jako je například nerozlišování velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="54672-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="54672-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="54672-112">Optional.</span></span> <span data-ttu-id="54672-113">Výsledkem porovnání řetězců na základě pořadí řazení textu bez rozlišování velkých a malých písmen, které určuje národní prostředí vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="54672-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="54672-114">Tento typ porovnání je užitečný v případě, že řetězce obsahují všechny textové znaky a chcete je porovnat s ohledem na abecední ekvivalenty, jako je například nerozlišování velkých a malých písmen a úzce související písmena.</span><span class="sxs-lookup"><span data-stu-id="54672-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="54672-115">Například můžete chtít zvážit `A` a `a`, které mají být stejné, a `Ä` a `ä` k předcházet `B` a `b`.</span><span class="sxs-lookup"><span data-stu-id="54672-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54672-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54672-116">Remarks</span></span>  
 <span data-ttu-id="54672-117">Při použití musí být příkaz `Option Compare` uveden v souboru před jakýmkoli jiným příkazy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="54672-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="54672-118">Příkaz `Option Compare` určuje metodu porovnání řetězců (`Binary` nebo `Text`).</span><span class="sxs-lookup"><span data-stu-id="54672-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="54672-119">Výchozí metoda porovnání textu je `Binary`.</span><span class="sxs-lookup"><span data-stu-id="54672-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="54672-120">Porovnání `Binary` porovnává číselnou hodnotu Unicode každého znaku v každém řetězci.</span><span class="sxs-lookup"><span data-stu-id="54672-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="54672-121">Porovnání `Text` porovnává každý znak Unicode na základě jeho lexikálního významu v aktuální jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="54672-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="54672-122">V systému Microsoft Windows je pořadí řazení určeno znakovou stránkou.</span><span class="sxs-lookup"><span data-stu-id="54672-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="54672-123">Další informace najdete v tématu [znakové stránky](/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="54672-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="54672-124">V následujícím příkladu jsou znaky na znakové stránce angličtina/Evropa (ANSI 1252) řazeny pomocí `Option Compare Binary`, což vytváří typické binární pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="54672-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="54672-125">Když jsou stejné znaky na stejné znakové stránce seřazené pomocí `Option Compare Text`, vytvoří se následující textové pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="54672-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="54672-126">Pokud není k dispozici příkaz Option Compare</span><span class="sxs-lookup"><span data-stu-id="54672-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="54672-127">Pokud zdrojový kód neobsahuje příkaz `Option Compare`, je použita **možnost porovnat** nastavení na [stránce kompilovat, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) .</span><span class="sxs-lookup"><span data-stu-id="54672-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="54672-128">Použijete-li kompilátor příkazového řádku, je použito nastavení určené možností kompilátoru [/OptionCompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) .</span><span class="sxs-lookup"><span data-stu-id="54672-128">If you use the command-line compiler, the setting specified by the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="54672-129">Nastavení možnosti Compare v integrovaném vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="54672-129">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="54672-130">V **Průzkumník řešení**vyberte projekt.</span><span class="sxs-lookup"><span data-stu-id="54672-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="54672-131">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="54672-131">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="54672-132">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="54672-132">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="54672-133">Nastavte hodnotu v poli **Porovnat možnost** .</span><span class="sxs-lookup"><span data-stu-id="54672-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="54672-134">Při vytváření projektu je **možnost porovnat** nastavení na kartě **kompilovat** nastavena na **možnost porovnat** nastavení v dialogovém okně **Možnosti** .</span><span class="sxs-lookup"><span data-stu-id="54672-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="54672-135">Chcete-li toto nastavení změnit, v nabídce **nástroje** klikněte na příkaz **Možnosti**.</span><span class="sxs-lookup"><span data-stu-id="54672-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="54672-136">V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**.</span><span class="sxs-lookup"><span data-stu-id="54672-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="54672-137">Počáteční výchozí nastavení ve **výchozích hodnotách VB** je **binární**.</span><span class="sxs-lookup"><span data-stu-id="54672-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="54672-138">Nastavení možnosti Compare v příkazovém řádku</span><span class="sxs-lookup"><span data-stu-id="54672-138">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="54672-139">Do příkazu **Vbc** zahrňte možnost kompilátoru [/OptionCompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) .</span><span class="sxs-lookup"><span data-stu-id="54672-139">Include the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54672-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="54672-140">Example</span></span>  
 <span data-ttu-id="54672-141">Následující příklad používá příkaz `Option Compare` pro nastavení binárního porovnání jako výchozí metody porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="54672-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="54672-142">Chcete-li použít tento kód, odkomentujte příkaz `Option Compare Binary` a umístěte jej do horní části zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="54672-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="54672-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="54672-143">Example</span></span>  
 <span data-ttu-id="54672-144">Následující příklad používá příkaz `Option Compare` pro nastavení pořadí řazení textu bez rozlišení velkých a malých písmen jako výchozí metodu porovnání řetězců.</span><span class="sxs-lookup"><span data-stu-id="54672-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="54672-145">Chcete-li použít tento kód, odkomentujte příkaz `Option Compare Text` a umístěte jej do horní části zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="54672-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="54672-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54672-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="54672-147">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="54672-147">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="54672-148">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="54672-148">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="54672-149">Operátory porovnávání v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54672-149">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="54672-150">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="54672-150">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="54672-151">Funkce řetězce</span><span class="sxs-lookup"><span data-stu-id="54672-151">String Functions</span></span>](../../../visual-basic/language-reference/functions/string-functions.md)
- [<span data-ttu-id="54672-152">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="54672-152">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="54672-153">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="54672-153">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
