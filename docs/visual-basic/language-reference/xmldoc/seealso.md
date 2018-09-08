---
title: '&lt;Viz také&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: a792bbea108bcdf33d430c47773466ef3dccdb0c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44182827"
---
# <a name="ltseealsogt-visual-basic"></a><span data-ttu-id="8c66e-102">&lt;Viz také&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c66e-102">&lt;seealso&gt; (Visual Basic)</span></span>
<span data-ttu-id="8c66e-103">Určuje odkaz, který se zobrazí v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="8c66e-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c66e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c66e-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c66e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c66e-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="8c66e-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="8c66e-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="8c66e-107">Kompilátor kontroluje, zda daný prvek kódu existuje a předá `member` do názvu prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="8c66e-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="8c66e-108">`member` musí být uvedena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="8c66e-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c66e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c66e-109">Remarks</span></span>  
 <span data-ttu-id="8c66e-110">Použití `<seealso>` značka, které určuje text, který se má zobrazit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="8c66e-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="8c66e-111">Použití [ \<naleznete v tématu >](../../../visual-basic/language-reference/xmldoc/see.md) zadat odkaz v rámci textu.</span><span class="sxs-lookup"><span data-stu-id="8c66e-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="8c66e-112">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="8c66e-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c66e-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c66e-113">Example</span></span>  
 <span data-ttu-id="8c66e-114">V tomto příkladu `<seealso>` značku `DoesRecordExist` poznámky část neodkazuje na `UpdateRecord` metoda.</span><span class="sxs-lookup"><span data-stu-id="8c66e-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8c66e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c66e-115">See Also</span></span>  
 [<span data-ttu-id="8c66e-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="8c66e-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
