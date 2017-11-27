---
title: "Postupy: Vytvoření dokumentace XML v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 63b6485de5aba2ca49d54a057045bec2062d12dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="2849e-102">Postupy: Vytvoření dokumentace XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2849e-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="2849e-103">Tento příklad ukazuje, jak přidat dokumentační komentáře XML do vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="2849e-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="2849e-104">K vytvoření dokumentace XML pro typ nebo člen</span><span class="sxs-lookup"><span data-stu-id="2849e-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="2849e-105">V **Editor kódu**, umístěte kurzor na řádku výše typ nebo člen, pro který chcete vytvořit dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="2849e-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="2849e-106">Typ `'''` (tři jednoduchých uvozovek).</span><span class="sxs-lookup"><span data-stu-id="2849e-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="2849e-107">Kostru XML pro typ nebo člen je přidaný do **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="2849e-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="2849e-108">Přidejte popisné informace mezi odpovídající značky.</span><span class="sxs-lookup"><span data-stu-id="2849e-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2849e-109">Pokud chcete přidat další řádky uvnitř bloku dokumentace XML, musí každý řádek začínat `'''`.</span><span class="sxs-lookup"><span data-stu-id="2849e-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="2849e-110">Přidejte další kód, který používá typ nebo člen s nové dokumentační komentáře XML.</span><span class="sxs-lookup"><span data-stu-id="2849e-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="2849e-111">IntelliSense zobrazí text z \<souhrnné > značky pro typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="2849e-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="2849e-112">Zkompilujte kód generovat soubor XML obsahující dokumentační komentáře.</span><span class="sxs-lookup"><span data-stu-id="2849e-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="2849e-113">Další informace najdete v tématu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="2849e-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2849e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2849e-114">See Also</span></span>  
 [<span data-ttu-id="2849e-115">Dokumentace kódu s XML</span><span class="sxs-lookup"><span data-stu-id="2849e-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="2849e-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="2849e-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [<span data-ttu-id="2849e-117">/ DOC</span><span class="sxs-lookup"><span data-stu-id="2849e-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
