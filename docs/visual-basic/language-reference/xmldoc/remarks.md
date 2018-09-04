---
title: '&lt;Poznámky&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 97fca8758d9c21ac0b8f15bf9d5831750fbabe77
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43557073"
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="315aa-102">&lt;Poznámky&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="315aa-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="315aa-103">Určuje části poznámky pro tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="315aa-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="315aa-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="315aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="315aa-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="315aa-106">Popis člena.</span><span class="sxs-lookup"><span data-stu-id="315aa-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="315aa-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="315aa-107">Remarks</span></span>  
 <span data-ttu-id="315aa-108">Použití `<remarks>` značky pro přidání informací o typu, doplňující informace zadaným [ \<summary >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="315aa-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="315aa-109">Tyto informace se zobrazí v prohlížeči objektů.</span><span class="sxs-lookup"><span data-stu-id="315aa-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="315aa-110">Informace o prohlížeči objektů najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="315aa-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="315aa-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="315aa-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="315aa-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="315aa-112">Example</span></span>  
 <span data-ttu-id="315aa-113">V tomto příkladu `<remarks>` značka, které popisují, co `UpdateRecord` metodu.</span><span class="sxs-lookup"><span data-stu-id="315aa-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="315aa-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="315aa-114">See Also</span></span>  
 [<span data-ttu-id="315aa-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="315aa-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
