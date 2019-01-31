---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 7125f6079811421bc5a7abdce2e13d591a299630
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269325"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="443eb-102">\<REMARKS > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="443eb-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="443eb-103">Určuje části poznámky pro tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="443eb-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="443eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="443eb-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="443eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="443eb-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="443eb-106">Popis člena.</span><span class="sxs-lookup"><span data-stu-id="443eb-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="443eb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="443eb-107">Remarks</span></span>  
 <span data-ttu-id="443eb-108">Použití `<remarks>` značky pro přidání informací o typu, doplňující informace zadaným [ \<summary >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="443eb-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="443eb-109">Tyto informace se zobrazí v prohlížeči objektů.</span><span class="sxs-lookup"><span data-stu-id="443eb-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="443eb-110">Informace o prohlížeči objektů najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="443eb-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="443eb-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="443eb-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="443eb-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="443eb-112">Example</span></span>  
 <span data-ttu-id="443eb-113">V tomto příkladu `<remarks>` značka, které popisují, co `UpdateRecord` metodu.</span><span class="sxs-lookup"><span data-stu-id="443eb-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="443eb-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="443eb-114">See also</span></span>
- [<span data-ttu-id="443eb-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="443eb-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
