---
title: '&lt;výjimka&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: f29b8e01239f46b0d56319ba3da1a8fe179a17e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601150"
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="78880-102">&lt;výjimka&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78880-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="78880-103">Určuje, výjimek, které může být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="78880-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78880-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78880-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78880-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78880-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="78880-106">Odkaz na výjimku, která je k dispozici z aktuální prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="78880-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="78880-107">Kompilátor kontroluje, zda výjimka existuje a překládá `member` na element kanonický název ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="78880-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="78880-108">`member` musí být v rámci dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="78880-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="78880-109">Popis.</span><span class="sxs-lookup"><span data-stu-id="78880-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78880-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78880-110">Remarks</span></span>  
 <span data-ttu-id="78880-111">Použití `<exception>` značky k určení výjimek, které může být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="78880-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="78880-112">Tato značka se použije k definici metody.</span><span class="sxs-lookup"><span data-stu-id="78880-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="78880-113">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="78880-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78880-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="78880-114">Example</span></span>  
 <span data-ttu-id="78880-115">Tento příklad používá `<exception>` značka, které popisují výjimku, `IntDivide` funkce můžete vyvolat.</span><span class="sxs-lookup"><span data-stu-id="78880-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="78880-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="78880-116">See Also</span></span>  
 [<span data-ttu-id="78880-117">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="78880-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
