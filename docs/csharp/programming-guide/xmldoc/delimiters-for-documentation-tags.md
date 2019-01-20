---
title: Oddělovače pro dokumentační značky - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: c14b0470f7ea488fcb813b68174b5d1cb0d95786
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415582"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="dfd4d-102">Oddělovače pro dokumentační značky (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="dfd4d-102">Delimiters for Documentation Tags (C# Programming Guide)</span></span>
<span data-ttu-id="dfd4d-103">Použití komentáře XML vyžaduje oddělovače, které označují kompilátoru kde Dokumentační komentář začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="dfd4d-104">Můžete použít následující typy oddělovače se značkami dokumentace XML:</span><span class="sxs-lookup"><span data-stu-id="dfd4d-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>  
  
 `///`  
 <span data-ttu-id="dfd4d-105">Oddělovač jedním řádkem.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-105">Single-line delimiter.</span></span> <span data-ttu-id="dfd4d-106">Toto je formulář, který je uvedeno v dokumentaci příklady a používá šablony projektů Visual C#.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="dfd4d-107">Pokud je znak mezery za oddělovačem, tento znak není součástí výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfd4d-108">Integrované vývojové prostředí sady Visual Studio obsahuje funkci s názvem inteligentní úpravy komentářů, který automaticky vloží \<summary > a \</summary > značky a přesune kurzor v rámci těchto značek po zadání `///` oddělovač v editoru kódu .</span><span class="sxs-lookup"><span data-stu-id="dfd4d-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="dfd4d-109">Tuto funkci můžete zapnout nebo vypnout [dialogové okno Možnosti](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="dfd4d-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>  
  
 `/** */`  
 <span data-ttu-id="dfd4d-110">Víceřádkový oddělovače.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-110">Multiline delimiters.</span></span>  
  
 <span data-ttu-id="dfd4d-111">Existují některá pravidla formátování při použití `/** */` oddělovače.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-111">There are some formatting rules to follow when you use the `/** */` delimiters.</span></span>  
  
-   <span data-ttu-id="dfd4d-112">Na řádku, který obsahuje `/**` oddělovač, pokud zbytek řádku je prázdný znak řádku není zpracovávána pro poznámky.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="dfd4d-113">Pokud po prvním znakem `/**` oddělovač je prázdný znak, že znak bílého prostoru řádku je ignorován a zbytek řádku je zpracovat.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="dfd4d-114">V opačném případě celý text řádku po `/**` oddělovač zpracovávány jako součást komentář.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>  
  
-   <span data-ttu-id="dfd4d-115">Na řádku, který obsahuje `*/` oddělovač, pokud existuje jenom prázdné znaky až `*/` oddělovač, tento řádek se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="dfd4d-116">V opačném případě text na řádku až `*/` oddělovač zpracovávány jako součást komentář porovnávání vzorů podle pravidel popsaných v následující odrážky.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>  
  
-   <span data-ttu-id="dfd4d-117">Pro řádky za ten, který začíná `/**` oddělovač, hledá kompilátor běžný vzor na začátku každého řádku.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="dfd4d-118">Vzor se může skládat z volitelné prázdné místo a hvězdičku (`*`) a po něm další volitelné prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="dfd4d-119">Pokud kompilátor najde běžný vzor na začátku každého řádku, který nezačíná `/**` oddělovač nebo `*/` oddělovač, ignoruje tento vzor pro každý řádek.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>  
  
 <span data-ttu-id="dfd4d-120">Následující příklady znázorňují tato pravidla.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-120">The following examples illustrate these rules.</span></span>  
  
-   <span data-ttu-id="dfd4d-121">Řádek, který začíná je jediná součást následující komentář, který se zpracuje `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="dfd4d-122">Tři značky formáty vytvářejí stejné komentáře.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-122">The three tag formats produce the same comments.</span></span>  
  
    ```csharp  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
-   <span data-ttu-id="dfd4d-123">Kompilátor identifikuje běžné vzor "\*" na začátku druhé a třetí řádky.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="dfd4d-124">Vzor není zahrnut ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-124">The pattern is not included in the output.</span></span>  
  
    ```csharp  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
-   <span data-ttu-id="dfd4d-125">Kompilátor vyhledá žádné běžný vzor v následující komentář, protože druhý znak na třetím řádku není hvězdičku.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="dfd4d-126">Proto veškerý text na řádcích druhé a třetí zpracovávány jako součást komentář.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>  
  
    ```csharp  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
-   <span data-ttu-id="dfd4d-127">Kompilátor vyhledá žádný model v následující komentář dvou důvodů.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="dfd4d-128">Počet mezer před hvězdička nejprve není konzistentní.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="dfd4d-129">Za druhé pátý řádek začíná kartu, která se neshoduje s mezery.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="dfd4d-130">Proto veškerý text z řádky dvou až pět zpracovávány jako součást komentář.</span><span class="sxs-lookup"><span data-stu-id="dfd4d-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>  
  
    ```csharp  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dfd4d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="dfd4d-131">See Also</span></span>

- [<span data-ttu-id="dfd4d-132">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dfd4d-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="dfd4d-133">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="dfd4d-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
- [<span data-ttu-id="dfd4d-134">/ DOC (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="dfd4d-134">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
- [<span data-ttu-id="dfd4d-135">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="dfd4d-135">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
