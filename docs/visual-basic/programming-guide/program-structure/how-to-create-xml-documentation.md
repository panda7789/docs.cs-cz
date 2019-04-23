---
title: 'Postupy: Vytvoření dokumentace XML v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 95f6c5b23deadc16eb1e81f274e2cc5149598fb7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59294481"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="34d09-102">Postupy: Vytvoření dokumentace XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34d09-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="34d09-103">Tento příklad ukazuje, jak přidat komentáře k dokumentaci XML do kódu.</span><span class="sxs-lookup"><span data-stu-id="34d09-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="34d09-104">K vytvoření dokumentace XML pro typ nebo člen</span><span class="sxs-lookup"><span data-stu-id="34d09-104">To create XML documentation for a type or member</span></span>  
  
1. <span data-ttu-id="34d09-105">V **Editor kódu**, umístěte kurzor na řádek nad tento typ nebo člen, pro kterou chcete vytvořit dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="34d09-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2. <span data-ttu-id="34d09-106">Typ `'''` (tří jednoduchých uvozovek).</span><span class="sxs-lookup"><span data-stu-id="34d09-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="34d09-107">Kostra XML pro typ nebo člen bude přidán do **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="34d09-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3. <span data-ttu-id="34d09-108">Přidáte popisné informace mezi odpovídající značky.</span><span class="sxs-lookup"><span data-stu-id="34d09-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="34d09-109">Pokud chcete přidat další řádky v rámci bloku dokumentace XML, musí začínat každého řádku `'''`.</span><span class="sxs-lookup"><span data-stu-id="34d09-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4. <span data-ttu-id="34d09-110">Přidejte další kód, který používá typ nebo člen pomocí nového komentáře k dokumentaci XML.</span><span class="sxs-lookup"><span data-stu-id="34d09-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="34d09-111">Technologie IntelliSense zobrazí text z \<summary > značky pro tento typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="34d09-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5. <span data-ttu-id="34d09-112">Zkompilujte kód a vygenerovat soubor XML obsahující komentáře k dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="34d09-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="34d09-113">Další informace najdete v tématu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="34d09-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d09-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34d09-114">See also</span></span>

- [<span data-ttu-id="34d09-115">Dokumentace kódu s XML</span><span class="sxs-lookup"><span data-stu-id="34d09-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="34d09-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="34d09-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
- [<span data-ttu-id="34d09-117">/doc</span><span class="sxs-lookup"><span data-stu-id="34d09-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
