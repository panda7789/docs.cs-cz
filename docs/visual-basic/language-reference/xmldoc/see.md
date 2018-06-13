---
title: '&lt;v tématu&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: e790f8abd216e198ff5077beab6f857e39981d2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602077"
---
# <a name="ltseegt-visual-basic"></a><span data-ttu-id="49b1b-102">&lt;v tématu&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49b1b-102">&lt;see&gt; (Visual Basic)</span></span>
<span data-ttu-id="49b1b-103">Určuje odkaz na druhý člen.</span><span class="sxs-lookup"><span data-stu-id="49b1b-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49b1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49b1b-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49b1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49b1b-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="49b1b-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="49b1b-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="49b1b-107">Kompilátor ověří, že element daného kódu existuje a předá `member` k názvu elementu ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="49b1b-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="49b1b-108">`member` musí být v rámci dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="49b1b-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49b1b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49b1b-109">Remarks</span></span>  
 <span data-ttu-id="49b1b-110">Použití `<see>` značku zadejte odkaz z v textu.</span><span class="sxs-lookup"><span data-stu-id="49b1b-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="49b1b-111">Použití [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) označíte, text, který chcete zobrazit v části "V části Viz také".</span><span class="sxs-lookup"><span data-stu-id="49b1b-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="49b1b-112">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="49b1b-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49b1b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="49b1b-113">Example</span></span>  
 <span data-ttu-id="49b1b-114">Tento příklad používá `<see>` značky v `UpdateRecord` remarks části k odkazování na `DoesRecordExist` metoda.</span><span class="sxs-lookup"><span data-stu-id="49b1b-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="49b1b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="49b1b-115">See Also</span></span>  
 [<span data-ttu-id="49b1b-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="49b1b-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
