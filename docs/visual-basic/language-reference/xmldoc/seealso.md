---
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 27bb2c271631170082709d9e3d76cd39eefbc860
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352219"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="4e06f-101">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e06f-101">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="4e06f-102">Specifies a link that appears in the See Also section.</span><span class="sxs-lookup"><span data-stu-id="4e06f-102">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e06f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e06f-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e06f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e06f-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="4e06f-105">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="4e06f-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="4e06f-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span><span class="sxs-lookup"><span data-stu-id="4e06f-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="4e06f-107">`member` must appear within double quotation marks (" ").</span><span class="sxs-lookup"><span data-stu-id="4e06f-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e06f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e06f-108">Remarks</span></span>  
 <span data-ttu-id="4e06f-109">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span><span class="sxs-lookup"><span data-stu-id="4e06f-109">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="4e06f-110">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span><span class="sxs-lookup"><span data-stu-id="4e06f-110">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="4e06f-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span><span class="sxs-lookup"><span data-stu-id="4e06f-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e06f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e06f-112">Example</span></span>  
 <span data-ttu-id="4e06f-113">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span><span class="sxs-lookup"><span data-stu-id="4e06f-113">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="4e06f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e06f-114">See also</span></span>

- [<span data-ttu-id="4e06f-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="4e06f-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
