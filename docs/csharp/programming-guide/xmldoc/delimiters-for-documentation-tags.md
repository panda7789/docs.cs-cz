---
title: Oddělovače pro dokumentační značky – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: 064519e6d849736690f28c78e0efbc4067f9e6a9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711789"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="8a7ac-102">Oddělovače pro dokumentační značky (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8a7ac-102">Delimiters for Documentation Tags (C# Programming Guide)</span></span>
<span data-ttu-id="8a7ac-103">Použití komentářů dokumentu XML vyžaduje oddělovače, které označují kompilátoru, kde komentář k dokumentaci začíná a končí.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="8a7ac-104">Pomocí značek dokumentace XML můžete použít následující typy oddělovačů:</span><span class="sxs-lookup"><span data-stu-id="8a7ac-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>  
  
 `///`  
 <span data-ttu-id="8a7ac-105">Jeden řádek oddělovače.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-105">Single-line delimiter.</span></span> <span data-ttu-id="8a7ac-106">Jedná se o formulář, který je zobrazen v příkladech dokumentace a který se C# používá v šablonách Visual Project.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-106">This is the form that is shown in documentation examples and used by the Visual C# project templates.</span></span> <span data-ttu-id="8a7ac-107">Pokud je za oddělovačem mezera, tento znak není zahrnutý ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a7ac-108">Integrované vývojové prostředí (IDE) sady Visual Studio obsahuje funkci s názvem úpravy inteligentních komentářů, která automaticky vkládá \<souhrn > a \</Summary > značky a přesune kurzor do těchto značek po zadání `///` oddělovače v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-108">The Visual Studio IDE has a feature called Smart Comment Editing that automatically inserts the \<summary> and \</summary> tags and moves your cursor within these tags after you type the `///` delimiter in the Code Editor.</span></span> <span data-ttu-id="8a7ac-109">Tuto funkci můžete zapnout nebo vypnout v [dialogovém okně Možnosti](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="8a7ac-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>  
  
 `/** */`  
 <span data-ttu-id="8a7ac-110">Víceřádkové oddělovače.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-110">Multiline delimiters.</span></span>  
  
 <span data-ttu-id="8a7ac-111">Existují určitá pravidla formátování, která se použijí při použití oddělovačů `/** */`.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-111">There are some formatting rules to follow when you use the `/** */` delimiters.</span></span>  
  
- <span data-ttu-id="8a7ac-112">Na řádku, který obsahuje oddělovač `/**`, pokud je zbývající část řádku mezera, řádek není zpracován pro komentáře.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="8a7ac-113">Je-li první znak za oddělovačem `/**` prázdný znak, bude mezera ignorována a zbytek řádku bude zpracován.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="8a7ac-114">V opačném případě bude celý text řádku po `/**` oddělovači zpracován jako součást komentáře.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>  
  
- <span data-ttu-id="8a7ac-115">Pokud je v řádku, který obsahuje oddělovač `*/`, pouze prázdné místo do oddělovače `*/`, tento řádek je ignorován.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="8a7ac-116">V opačném případě je text na řádku až do oddělovače `*/` zpracován jako součást komentáře v souladu s pravidly pro porovnávání vzorů popsanými v následující odrážce.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment, subject to the pattern-matching rules described in the following bullet.</span></span>  
  
- <span data-ttu-id="8a7ac-117">Pro řádky po jednom, který začíná oddělovačem `/**`, kompilátor hledá společný vzor na začátku každého řádku.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="8a7ac-118">Vzor se může skládat z volitelného prázdného místa a hvězdičky (`*`) následovaný více volitelnými prázdnými znaky.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="8a7ac-119">Pokud kompilátor najde společný vzor na začátku každého řádku, který nezačíná oddělovačem `/**` nebo oddělovačem `*/`, ignoruje tento model pro každý řádek.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>  
  
 <span data-ttu-id="8a7ac-120">Tato pravidla ilustrují následující příklady.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-120">The following examples illustrate these rules.</span></span>  
  
- <span data-ttu-id="8a7ac-121">Jediná část následujícího komentáře, který bude zpracována, je řádek, který začíná na `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-121">The only part of the following comment that will be processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="8a7ac-122">Tři formáty značek vytváří stejné komentáře.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-122">The three tag formats produce the same comments.</span></span>  
  
    ```csharp  
    /** <summary>text</summary> */   
  
    /**   
    <summary>text</summary>   
    */   
  
    /**   
     * <summary>text</summary>   
    */  
    ```  
  
- <span data-ttu-id="8a7ac-123">Kompilátor identifikuje běžný vzor "\*" na začátku druhého a třetího řádku.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="8a7ac-124">Vzorek není zahrnut ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-124">The pattern is not included in the output.</span></span>  
  
    ```csharp  
    /**   
     * <summary>   
     * text </summary>*/   
    ```  
  
- <span data-ttu-id="8a7ac-125">Kompilátor nenajde žádný společný vzor v následujícím komentáři, protože druhý znak na třetím řádku není hvězdička.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="8a7ac-126">Proto je veškerý text na druhém a třetím řádku zpracován jako součást komentáře.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>  
  
    ```csharp  
    /**   
     * <summary>   
       text </summary>  
    */   
    ```  
  
- <span data-ttu-id="8a7ac-127">Kompilátor nenajde z následujících komentářů žádný vzor, ze dvou důvodů.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="8a7ac-128">Za prvé je počet mezer před hvězdičkou nekonzistentní.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="8a7ac-129">Za druhé, pátá čára začíná tabulátorem, který se neshoduje s mezerami.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="8a7ac-130">Proto se veškerý text z řádků dvou až pěti zpracovává jako součást komentáře.</span><span class="sxs-lookup"><span data-stu-id="8a7ac-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>  
  
    ```csharp  
    /**   
      * <summary>   
      * text   
     *  text2   
        *  </summary>   
    */   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8a7ac-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a7ac-131">See also</span></span>

- [<span data-ttu-id="8a7ac-132">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8a7ac-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8a7ac-133">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="8a7ac-133">XML Documentation Comments</span></span>](./index.md)
- [<span data-ttu-id="8a7ac-134">-doc (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="8a7ac-134">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="8a7ac-135">Dokumentační komentáře XML</span><span class="sxs-lookup"><span data-stu-id="8a7ac-135">XML Documentation Comments</span></span>](./index.md)
