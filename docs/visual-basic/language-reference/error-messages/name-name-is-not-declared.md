---
title: Název &#39; &lt;název&gt; &#39; není deklarovaný
ms.date: 07/20/2015
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: e17017e84720a2581abc5115338352aacc02d473
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594816"
---
# <a name="name-39ltnamegt39-is-not-declared"></a><span data-ttu-id="007c5-102">Název &#39; &lt;název&gt; &#39; není deklarovaný</span><span class="sxs-lookup"><span data-stu-id="007c5-102">Name &#39;&lt;name&gt;&#39; is not declared</span></span>
<span data-ttu-id="007c5-103">Příkaz odkazuje na programovací element, ale kompilátor nelze najít element s tímto názvem přesný.</span><span class="sxs-lookup"><span data-stu-id="007c5-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="007c5-104">**ID chyby:** BC30451</span><span class="sxs-lookup"><span data-stu-id="007c5-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="007c5-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="007c5-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="007c5-106">Zkontrolujte správnost názvu v odkazující příkazu.</span><span class="sxs-lookup"><span data-stu-id="007c5-106">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="007c5-107">Visual Basic je velká a malá písmena, ale jiné variace v pravopis považuje za úplně jiný název.</span><span class="sxs-lookup"><span data-stu-id="007c5-107">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="007c5-108">Všimněte si, že podtržítko (`_`) je součástí názvu a proto součástí pravopis.</span><span class="sxs-lookup"><span data-stu-id="007c5-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2.  <span data-ttu-id="007c5-109">Zkontrolujte, že máte operátor přístupu členů (`.`) mezi objektem a jejího člena.</span><span class="sxs-lookup"><span data-stu-id="007c5-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="007c5-110">Pokud máte například <xref:System.Windows.Forms.TextBox> ovládací prvek s názvem `TextBox1`, přístup k jeho <xref:System.Windows.Forms.TextBoxBase.Text%2A> vlastnost byste měli zadat `TextBox1.Text`.</span><span class="sxs-lookup"><span data-stu-id="007c5-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="007c5-111">Pokud místo toho zadáte `TextBox1Text`, jste vytvořili jiný název.</span><span class="sxs-lookup"><span data-stu-id="007c5-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3.  <span data-ttu-id="007c5-112">Pokud správně a syntaxe žádné přístup ke členu objektu je správný, ověřte deklarován element.</span><span class="sxs-lookup"><span data-stu-id="007c5-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="007c5-113">Další informace najdete v tématu [deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="007c5-113">For more information, see [Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4.  <span data-ttu-id="007c5-114">Pokud bylo deklarováno programovací element, zkontrolujte, že je v oboru.</span><span class="sxs-lookup"><span data-stu-id="007c5-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="007c5-115">Pokud příkaz odkazující mimo oblast deklarace programovací element, možná budete muset kvalifikaci název elementu.</span><span class="sxs-lookup"><span data-stu-id="007c5-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="007c5-116">Další informace najdete v tématu [oboru v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="007c5-116">For more information, see [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="007c5-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="007c5-117">See Also</span></span>  
 [<span data-ttu-id="007c5-118">Souhrn deklarací a konstant</span><span class="sxs-lookup"><span data-stu-id="007c5-118">Declarations and Constants Summary</span></span>](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [<span data-ttu-id="007c5-119">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="007c5-119">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="007c5-120">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="007c5-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="007c5-121">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="007c5-121">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
