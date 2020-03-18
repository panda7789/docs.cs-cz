---
title: Oddělovače pro značky dokumentace – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: dd4ddb3b324bd6d235efb541c90875dbe9ed4c2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789821"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="6027c-102">Oddělovače pro značky dokumentace (průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6027c-102">Delimiters for documentation tags (C# programming guide)</span></span>

<span data-ttu-id="6027c-103">Použití xml doc komentáře vyžaduje oddělovače, které označují kompilátoru, kde komentář dokumentace začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="6027c-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="6027c-104">S tagy dokumentace XML můžete použít následující typy oddělovačů:</span><span class="sxs-lookup"><span data-stu-id="6027c-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>

- `///`

  <span data-ttu-id="6027c-105">Jednořádkový oddělovač.</span><span class="sxs-lookup"><span data-stu-id="6027c-105">Single-line delimiter.</span></span> <span data-ttu-id="6027c-106">Toto je formulář, který je zobrazen v příkladech dokumentace a používá visual c# šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="6027c-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="6027c-107">Pokud je za oddělovačem mezera, není tento znak zahrnut do výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="6027c-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>

  > [!NOTE]
  > <span data-ttu-id="6027c-108">IDE sady Visual Studio má funkci nazvanou Inteligentní \<úpravy \<komentářů, která automaticky vloží značky souhrnných `///`> a /summary> a přesune kurzor v rámci těchto značek po zadání oddělovače v Editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="6027c-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="6027c-109">Tuto funkci můžete zapnout nebo vypnout v [dialogovém okně Možnosti](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="6027c-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>
  
- `/** */`

  <span data-ttu-id="6027c-110">Vícesměrové oddělovače.</span><span class="sxs-lookup"><span data-stu-id="6027c-110">Multiline delimiters.</span></span>

  <span data-ttu-id="6027c-111">Při použití `/** */` oddělovačů je třeba dodržovat určitá pravidla formátování:</span><span class="sxs-lookup"><span data-stu-id="6027c-111">There are some formatting rules to follow when you use the `/** */` delimiters:</span></span>
  
  - <span data-ttu-id="6027c-112">Na řádku, který `/**` obsahuje oddělovač, pokud je zbytek řádku prázdné místo, řádek není zpracován pro komentáře.</span><span class="sxs-lookup"><span data-stu-id="6027c-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="6027c-113">Pokud je první `/**` znak po oddělovači prázdné místo, tento znak prázdného místa je ignorován a zbytek řádku je zpracován.</span><span class="sxs-lookup"><span data-stu-id="6027c-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="6027c-114">V opačném případě je celý `/**` text řádku po oddělovači zpracován jako součást komentáře.</span><span class="sxs-lookup"><span data-stu-id="6027c-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>

  - <span data-ttu-id="6027c-115">Na řádku, který `*/` obsahuje oddělovač, pokud je pouze `*/` prázdné místo až k oddělovači, tento řádek je ignorován.</span><span class="sxs-lookup"><span data-stu-id="6027c-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="6027c-116">V opačném případě je text `*/` na řádku až k oddělovači zpracován jako součást komentáře, s výhradou pravidel pro porovnávání vzorů popsaných v následující odrážce.</span><span class="sxs-lookup"><span data-stu-id="6027c-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>
  
  - <span data-ttu-id="6027c-117">Pro řádky za ten, který `/**` začíná oddělovač, kompilátor hledá společný vzor na začátku každého řádku.</span><span class="sxs-lookup"><span data-stu-id="6027c-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="6027c-118">Vzorek se může skládat z volitelného`*`prázdného místa a hvězdičky ( ), následované volitelným prázdném místem.</span><span class="sxs-lookup"><span data-stu-id="6027c-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="6027c-119">Pokud kompilátor najde společný vzor na začátku každého řádku, který nezačíná `/**` oddělovač nebo `*/` oddělovač, ignoruje tento vzor pro každý řádek.</span><span class="sxs-lookup"><span data-stu-id="6027c-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>

  <span data-ttu-id="6027c-120">Následující příklady ilustrují tato pravidla.</span><span class="sxs-lookup"><span data-stu-id="6027c-120">The following examples illustrate these rules.</span></span>

  - <span data-ttu-id="6027c-121">Jediná část následující poznámky, která bude zpracována, je `<summary>`řádek, který začíná na .</span><span class="sxs-lookup"><span data-stu-id="6027c-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="6027c-122">Tři formáty značek vytvářejí stejné komentáře.</span><span class="sxs-lookup"><span data-stu-id="6027c-122">The three tag formats produce the same comments.</span></span>

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - <span data-ttu-id="6027c-123">Kompilátor identifikuje společný vzor \* " " na začátku druhého a třetího řádků.</span><span class="sxs-lookup"><span data-stu-id="6027c-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="6027c-124">Vzor není součástí výstupu.</span><span class="sxs-lookup"><span data-stu-id="6027c-124">The pattern is not included in the output.</span></span>

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - <span data-ttu-id="6027c-125">Kompilátor nenajde žádný společný vzor v následující komentář, protože druhý znak na třetím řádku není hvězdičkou.</span><span class="sxs-lookup"><span data-stu-id="6027c-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="6027c-126">Proto je veškerý text na druhém a třetím řádku zpracován jako součást komentáře.</span><span class="sxs-lookup"><span data-stu-id="6027c-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - <span data-ttu-id="6027c-127">Kompilátor nenajde žádný vzor v následující komentář ze dvou důvodů.</span><span class="sxs-lookup"><span data-stu-id="6027c-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="6027c-128">Za prvé, počet mezer před hvězdičkou není konzistentní.</span><span class="sxs-lookup"><span data-stu-id="6027c-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="6027c-129">Za druhé, pátý řádek začíná tabulátorem, který neodpovídá mezerám.</span><span class="sxs-lookup"><span data-stu-id="6027c-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="6027c-130">Proto je veškerý text z řádků dva až pět zpracován jako součást komentáře.</span><span class="sxs-lookup"><span data-stu-id="6027c-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6027c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="6027c-131">See also</span></span>

- [<span data-ttu-id="6027c-132">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6027c-132">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6027c-133">Komentáře dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="6027c-133">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="6027c-134">-doc (možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6027c-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
