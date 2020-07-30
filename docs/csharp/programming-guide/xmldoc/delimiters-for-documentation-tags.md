---
title: Oddělovače pro dokumentační značky – Průvodce programováním v C#
description: Seznamte se s oddělovači pro dokumentaci k dokumentaci. Oddělovače označují kompilátoru, kde komentář k dokumentaci začíná a končí.
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 3191e32b0ff2dbde004abaab0b699cd61fcbb150
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381980"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="b4250-104">Oddělovače pro dokumentační značky (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b4250-104">Delimiters for documentation tags (C# programming guide)</span></span>

<span data-ttu-id="b4250-105">Použití komentářů dokumentu XML vyžaduje oddělovače, které označují kompilátoru, kde komentář k dokumentaci začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="b4250-105">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="b4250-106">Pomocí značek dokumentace XML můžete použít následující typy oddělovačů:</span><span class="sxs-lookup"><span data-stu-id="b4250-106">You can use the following kinds of delimiters with the XML documentation tags:</span></span>

- `///`

  <span data-ttu-id="b4250-107">Jeden řádek oddělovače.</span><span class="sxs-lookup"><span data-stu-id="b4250-107">Single-line delimiter.</span></span> <span data-ttu-id="b4250-108">Jedná se o formulář, který je zobrazen v příkladech dokumentace a používá šablony projektů v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="b4250-108">This is the form that is shown in documentation examples and used by the C# project templates.</span></span> <span data-ttu-id="b4250-109">Pokud je za oddělovačem mezera, tento znak není zahrnutý ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="b4250-109">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b4250-110">Integrované vývojové prostředí (IDE) sady Visual Studio `<summary>` `</summary>` po zadání `///` oddělovače v editoru kódu automaticky vloží značky a a přesune kurzor do těchto značek.</span><span class="sxs-lookup"><span data-stu-id="b4250-110">The Visual Studio integrated development environment (IDE) automatically inserts the `<summary>` and `</summary>` tags and moves your cursor within these tags after you type the `///` delimiter in the code editor.</span></span> <span data-ttu-id="b4250-111">Tuto funkci můžete zapnout nebo vypnout v [dialogovém okně Možnosti](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="b4250-111">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>
  
- `/** */`

  <span data-ttu-id="b4250-112">Víceřádkové oddělovače.</span><span class="sxs-lookup"><span data-stu-id="b4250-112">Multiline delimiters.</span></span>

  <span data-ttu-id="b4250-113">Existují určitá pravidla formátování, která se použijí při použití `/** */` oddělovačů:</span><span class="sxs-lookup"><span data-stu-id="b4250-113">There are some formatting rules to follow when you use the `/** */` delimiters:</span></span>
  
  - <span data-ttu-id="b4250-114">Na řádku, který obsahuje `/**` oddělovač, pokud je zbývající část řádku prázdným znakem, není řádek pro komentáře zpracován.</span><span class="sxs-lookup"><span data-stu-id="b4250-114">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="b4250-115">Je-li první znak za `/**` oddělovačem prázdné znaky, bude prázdný znak ignorován a zbytek řádku je zpracován.</span><span class="sxs-lookup"><span data-stu-id="b4250-115">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="b4250-116">V opačném případě bude celý text řádku po `/**` oddělovači zpracován jako součást komentáře.</span><span class="sxs-lookup"><span data-stu-id="b4250-116">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>

  - <span data-ttu-id="b4250-117">Na řádku, který obsahuje `*/` oddělovač, pokud je pouze mezera do `*/` oddělovače, tento řádek je ignorován.</span><span class="sxs-lookup"><span data-stu-id="b4250-117">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="b4250-118">V opačném případě se text na řádku do `*/` oddělovače zpracuje jako součást komentáře.</span><span class="sxs-lookup"><span data-stu-id="b4250-118">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment.</span></span>
  
  - <span data-ttu-id="b4250-119">Pro řádky po jednom, který začíná `/**` oddělovačem, kompilátor hledá společný vzor na začátku každého řádku.</span><span class="sxs-lookup"><span data-stu-id="b4250-119">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="b4250-120">Vzor se může skládat z volitelného prázdného místa a hvězdičky ( `*` ) následovaný více volitelnými prázdnými znaky.</span><span class="sxs-lookup"><span data-stu-id="b4250-120">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="b4250-121">Pokud kompilátor najde společný vzor na začátku každého řádku, který nezačíná `/**` oddělovačem nebo oddělovačem `*/` , ignoruje tento model pro každý řádek.</span><span class="sxs-lookup"><span data-stu-id="b4250-121">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>

  <span data-ttu-id="b4250-122">Tato pravidla ilustrují následující příklady.</span><span class="sxs-lookup"><span data-stu-id="b4250-122">The following examples illustrate these rules.</span></span>

  - <span data-ttu-id="b4250-123">Jediná část následujícího komentáře, který je zpracována, je řádek, který začíná `<summary>` .</span><span class="sxs-lookup"><span data-stu-id="b4250-123">The only part of the following comment that's processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="b4250-124">Tři formáty značek vytváří stejné komentáře.</span><span class="sxs-lookup"><span data-stu-id="b4250-124">The three tag formats produce the same comments.</span></span>

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - <span data-ttu-id="b4250-125">Kompilátor identifikuje společný vzor " \* " na začátku druhého a třetího řádku.</span><span class="sxs-lookup"><span data-stu-id="b4250-125">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="b4250-126">Vzorek není zahrnut ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="b4250-126">The pattern is not included in the output.</span></span>

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - <span data-ttu-id="b4250-127">Kompilátor nenajde žádný společný vzor v následujícím komentáři, protože druhý znak na třetím řádku není hvězdička.</span><span class="sxs-lookup"><span data-stu-id="b4250-127">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="b4250-128">Proto je veškerý text na druhém a třetím řádku zpracován jako součást komentáře.</span><span class="sxs-lookup"><span data-stu-id="b4250-128">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - <span data-ttu-id="b4250-129">Kompilátor nenajde z následujících komentářů žádný vzor, ze dvou důvodů.</span><span class="sxs-lookup"><span data-stu-id="b4250-129">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="b4250-130">Za prvé je počet mezer před hvězdičkou nekonzistentní.</span><span class="sxs-lookup"><span data-stu-id="b4250-130">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="b4250-131">Za druhé, pátá čára začíná tabulátorem, který se neshoduje s mezerami.</span><span class="sxs-lookup"><span data-stu-id="b4250-131">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="b4250-132">Proto se veškerý text z řádků dvou až pěti zpracovává jako součást komentáře.</span><span class="sxs-lookup"><span data-stu-id="b4250-132">Therefore, all text from lines two through five is processed as part of the comment.</span></span>

    <!-- markdownlint-disable MD010 -->
    ```csharp
    /**
      * <summary>
      * text
     *  text2
        *  </summary>
    */
    ```
    <!-- markdownlint-enable MD010 -->

## <a name="see-also"></a><span data-ttu-id="b4250-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4250-133">See also</span></span>

- [<span data-ttu-id="b4250-134">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b4250-134">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="b4250-135">Komentáře dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="b4250-135">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="b4250-136">-doc (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="b4250-136">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
