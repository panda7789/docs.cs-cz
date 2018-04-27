---
title: Název &#39; &lt;název&gt; &#39; není deklarovaný
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26245952a2dc5341dedba6c497c47773b882b49b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="name-39ltnamegt39-is-not-declared"></a><span data-ttu-id="c5acf-102">Název &#39; &lt;název&gt; &#39; není deklarovaný</span><span class="sxs-lookup"><span data-stu-id="c5acf-102">Name &#39;&lt;name&gt;&#39; is not declared</span></span>
<span data-ttu-id="c5acf-103">Příkaz odkazuje na programovací element, ale kompilátor nelze najít element s tímto názvem přesný.</span><span class="sxs-lookup"><span data-stu-id="c5acf-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="c5acf-104">**ID chyby:** BC30451</span><span class="sxs-lookup"><span data-stu-id="c5acf-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c5acf-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c5acf-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="c5acf-106">Zkontrolujte správnost názvu v odkazující příkazu.</span><span class="sxs-lookup"><span data-stu-id="c5acf-106">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="c5acf-107">Visual Basic je velká a malá písmena, ale jiné variace v pravopis považuje za úplně jiný název.</span><span class="sxs-lookup"><span data-stu-id="c5acf-107">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="c5acf-108">Všimněte si, že podtržítko (`_`) je součástí názvu a proto součástí pravopis.</span><span class="sxs-lookup"><span data-stu-id="c5acf-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2.  <span data-ttu-id="c5acf-109">Zkontrolujte, že máte operátor přístupu členů (`.`) mezi objektem a jejího člena.</span><span class="sxs-lookup"><span data-stu-id="c5acf-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="c5acf-110">Pokud máte například <xref:System.Windows.Forms.TextBox> ovládací prvek s názvem `TextBox1`, přístup k jeho <xref:System.Windows.Forms.TextBoxBase.Text%2A> vlastnost byste měli zadat `TextBox1.Text`.</span><span class="sxs-lookup"><span data-stu-id="c5acf-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="c5acf-111">Pokud místo toho zadáte `TextBox1Text`, jste vytvořili jiný název.</span><span class="sxs-lookup"><span data-stu-id="c5acf-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3.  <span data-ttu-id="c5acf-112">Pokud správně a syntaxe žádné přístup ke členu objektu je správný, ověřte deklarován element.</span><span class="sxs-lookup"><span data-stu-id="c5acf-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="c5acf-113">Další informace najdete v tématu [deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="c5acf-113">For more information, see [Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4.  <span data-ttu-id="c5acf-114">Pokud bylo deklarováno programovací element, zkontrolujte, že je v oboru.</span><span class="sxs-lookup"><span data-stu-id="c5acf-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="c5acf-115">Pokud příkaz odkazující mimo oblast deklarace programovací element, možná budete muset kvalifikaci název elementu.</span><span class="sxs-lookup"><span data-stu-id="c5acf-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="c5acf-116">Další informace najdete v tématu [oboru v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="c5acf-116">For more information, see [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5acf-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5acf-117">See Also</span></span>  
 [<span data-ttu-id="c5acf-118">Souhrn deklarací a konstant</span><span class="sxs-lookup"><span data-stu-id="c5acf-118">Declarations and Constants Summary</span></span>](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [<span data-ttu-id="c5acf-119">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5acf-119">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="c5acf-120">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="c5acf-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="c5acf-121">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="c5acf-121">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
