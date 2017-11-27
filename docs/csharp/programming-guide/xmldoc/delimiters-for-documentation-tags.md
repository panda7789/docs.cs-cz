---
title: "Oddělovače pro dokumentační značky (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a6ab03d220d1ef71605b83c529595dd986ea922a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="99d88-102">Oddělovače pro dokumentační značky (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="99d88-102">Delimiters for Documentation Tags (C# Programming Guide)</span></span>
<span data-ttu-id="99d88-103">Použití komentáře doc XML vyžaduje oddělovače, které označují kompilátoru kde komentáře dokumentace k zahájení a ukončení.</span><span class="sxs-lookup"><span data-stu-id="99d88-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="99d88-104">Můžete použít následující typy oddělovače s dokumentační značky XML:</span><span class="sxs-lookup"><span data-stu-id="99d88-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>  
  
 `///`  
 <span data-ttu-id="99d88-105">Oddělovač jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="99d88-105">Single-line delimiter.</span></span> <span data-ttu-id="99d88-106">Toto je formulář, který je zobrazeno v příkladech dokumentace a použít šablony projektů Visual C#.</span><span class="sxs-lookup"><span data-stu-id="99d88-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="99d88-107">Pokud je prázdný znak za oddělovačem, tento znak není zahrnut ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="99d88-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99d88-108">Visual Studio IDE má funkci inteligentního komentář úpravy, které automaticky vloží \<souhrnné > a \<nebo souhrnných > značky a přesune kurzor v rámci těchto značek po zadání `///` oddělovač v editoru kódu .</span><span class="sxs-lookup"><span data-stu-id="99d88-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="99d88-109">Přístup k této funkci z [možnosti, textový Editor, C#, formátování vzorků](/visualstudio/ide/reference/options-text-editor-csharp-formatting) na stránkách vlastností projektu.</span><span class="sxs-lookup"><span data-stu-id="99d88-109">Access this feature from the [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting) in your project property pages.</span></span>  
  
 `/** */`  
 <span data-ttu-id="99d88-110">Víceřádkový oddělovače.</span><span class="sxs-lookup"><span data-stu-id="99d88-110">Multiline delimiters.</span></span>  
  
 <span data-ttu-id="99d88-111">Existují některé formátování pravidla při použití `/** */` oddělovače.</span><span class="sxs-lookup"><span data-stu-id="99d88-111">There are some formatting rules to follow when you use the `/** */` delimiters.</span></span>  
  
-   <span data-ttu-id="99d88-112">Na řádku, který obsahuje `/**` oddělovač, pokud zbývající řádku je prázdné znaky, řádek není zpracován pro komentáře.</span><span class="sxs-lookup"><span data-stu-id="99d88-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="99d88-113">Pokud po první znak `/**` oddělovač je prázdný znak, že prázdný znak je ignorován a zbytek řádku je zpracovat.</span><span class="sxs-lookup"><span data-stu-id="99d88-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="99d88-114">V opačném celý text řádku po `/**` oddělovač zpracovávány jako součást komentář.</span><span class="sxs-lookup"><span data-stu-id="99d88-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>  
  
-   <span data-ttu-id="99d88-115">Na řádek, který obsahuje `*/` oddělovač, pokud je pouze mezera až `*/` oddělovač, daného řádku je ignorováno.</span><span class="sxs-lookup"><span data-stu-id="99d88-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="99d88-116">Jinak hodnota textu v řádku než `*/` oddělovač zpracovávány jako součást komentář, dodržování pravidel porovnávání popsané v následující odrážka.</span><span class="sxs-lookup"><span data-stu-id="99d88-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>  
  
-   <span data-ttu-id="99d88-117">Řádků po ten, který začíná `/**` oddělovač, kompilátor hledá společný vzorek na začátku každého řádku.</span><span class="sxs-lookup"><span data-stu-id="99d88-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="99d88-118">Vzor se může skládat z mezer volitelné a znak hvězdičky (`*`), za nímž následují další volitelné mezer.</span><span class="sxs-lookup"><span data-stu-id="99d88-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="99d88-119">Pokud kompilátor vyhledá společný vzorek na začátku každého řádku, který začíná `/**` oddělovač nebo `*/` oddělovač, ignoruje tento vzor pro každý řádek.</span><span class="sxs-lookup"><span data-stu-id="99d88-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>  
  
 <span data-ttu-id="99d88-120">Následující příklady znázorňují tato pravidla.</span><span class="sxs-lookup"><span data-stu-id="99d88-120">The following examples illustrate these rules.</span></span>  
  
-   <span data-ttu-id="99d88-121">Část pouze následující komentář, který bude zpracován je řádek, který začíná `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="99d88-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="99d88-122">Formáty tři označení vytvořit stejné komentáře.</span><span class="sxs-lookup"><span data-stu-id="99d88-122">The three tag formats produce the same comments.</span></span>  
  
    ```  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   <span data-ttu-id="99d88-123">Kompilátor identifikuje běžný vzor "*" na začátku druhé a třetí řádky.</span><span class="sxs-lookup"><span data-stu-id="99d88-123">The compiler identifies a common pattern of " * " at the beginning of the second and third lines.</span></span> <span data-ttu-id="99d88-124">Vzor není zahrnut ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="99d88-124">The pattern is not included in the output.</span></span>  
  
    ```  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   <span data-ttu-id="99d88-125">Kompilátor žádný společný vzorek najde v následující komentář protože znacích na ve třetím řádku není hvězdičku.</span><span class="sxs-lookup"><span data-stu-id="99d88-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="99d88-126">Proto je veškerý text na řádcích druhé a třetí zpracovat jako součást komentář.</span><span class="sxs-lookup"><span data-stu-id="99d88-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>  
  
    ```  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   <span data-ttu-id="99d88-127">Kompilátor vyhledá žádné vzor v následující komentář dvou důvodů.</span><span class="sxs-lookup"><span data-stu-id="99d88-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="99d88-128">Počet mezer, než se tedy hvězdička nejprve není konzistentní.</span><span class="sxs-lookup"><span data-stu-id="99d88-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="99d88-129">Druhý páté řádek začíná na kartě, který neodpovídá prostory.</span><span class="sxs-lookup"><span data-stu-id="99d88-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="99d88-130">Proto je veškerý text z čar dva až pět zpracovat jako součást komentář.</span><span class="sxs-lookup"><span data-stu-id="99d88-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>  
  
    ```  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="99d88-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="99d88-131">See Also</span></span>  
 [<span data-ttu-id="99d88-132">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="99d88-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="99d88-133">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="99d88-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [<span data-ttu-id="99d88-134">/ DOC (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="99d88-134">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="99d88-135">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="99d88-135">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
