---
title: '&lt;Zobrazit&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 78311651593d3d4a47c723f64a9a74d4660f7c90
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43535074"
---
# <a name="ltseegt-visual-basic"></a><span data-ttu-id="ecf92-102">&lt;Zobrazit&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecf92-102">&lt;see&gt; (Visual Basic)</span></span>
<span data-ttu-id="ecf92-103">Uvádí odkaz na jiný člen.</span><span class="sxs-lookup"><span data-stu-id="ecf92-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecf92-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecf92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecf92-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="ecf92-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="ecf92-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="ecf92-107">Kompilátor kontroluje, zda daný prvek kódu existuje a předá `member` do názvu prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="ecf92-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="ecf92-108">`member` musí být uvedena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="ecf92-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecf92-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecf92-109">Remarks</span></span>  
 <span data-ttu-id="ecf92-110">Použití `<see>` značka zadat odkaz v rámci textu.</span><span class="sxs-lookup"><span data-stu-id="ecf92-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="ecf92-111">Použití [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) označuje text, který chcete zobrazit v části "V části Viz také".</span><span class="sxs-lookup"><span data-stu-id="ecf92-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="ecf92-112">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="ecf92-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecf92-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecf92-113">Example</span></span>  
 <span data-ttu-id="ecf92-114">V tomto příkladu `<see>` značku `UpdateRecord` poznámky část neodkazuje na `DoesRecordExist` metoda.</span><span class="sxs-lookup"><span data-stu-id="ecf92-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ecf92-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecf92-115">See Also</span></span>  
 [<span data-ttu-id="ecf92-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="ecf92-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
