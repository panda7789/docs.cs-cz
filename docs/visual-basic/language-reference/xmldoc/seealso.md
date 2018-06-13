---
title: '&lt;Viz také&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 1d45c0c5fa95de9cfa345c0bdbf496aa227b9af5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604676"
---
# <a name="ltseealsogt-visual-basic"></a><span data-ttu-id="35a3e-102">&lt;Viz také&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35a3e-102">&lt;seealso&gt; (Visual Basic)</span></span>
<span data-ttu-id="35a3e-103">Určuje odkaz, který se zobrazí v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="35a3e-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35a3e-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35a3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35a3e-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="35a3e-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="35a3e-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="35a3e-107">Kompilátor ověří, že element daného kódu existuje a předá `member` k názvu elementu ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="35a3e-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="35a3e-108">`member` musí být v rámci dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="35a3e-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35a3e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35a3e-109">Remarks</span></span>  
 <span data-ttu-id="35a3e-110">Použití `<seealso>` značku a zadejte text, který se má zobrazit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="35a3e-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="35a3e-111">Použití [ \<najdete v části >](../../../visual-basic/language-reference/xmldoc/see.md) zadat odkaz z v textu.</span><span class="sxs-lookup"><span data-stu-id="35a3e-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="35a3e-112">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="35a3e-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35a3e-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="35a3e-113">Example</span></span>  
 <span data-ttu-id="35a3e-114">Tento příklad používá `<seealso>` značky v `DoesRecordExist` remarks části k odkazování na `UpdateRecord` metoda.</span><span class="sxs-lookup"><span data-stu-id="35a3e-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="35a3e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="35a3e-115">See Also</span></span>  
 [<span data-ttu-id="35a3e-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="35a3e-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
