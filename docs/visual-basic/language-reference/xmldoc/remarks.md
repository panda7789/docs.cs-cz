---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 38549b2fcce0740b2b9cfd42d950e56b343e7a30
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524677"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="70043-102">\<remarks > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70043-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="70043-103">Určuje oddíl poznámky pro člena.</span><span class="sxs-lookup"><span data-stu-id="70043-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70043-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70043-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="70043-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70043-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="70043-106">Popis člena</span><span class="sxs-lookup"><span data-stu-id="70043-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70043-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70043-107">Remarks</span></span>  
 <span data-ttu-id="70043-108">Pomocí značky `<remarks>` můžete přidat informace o typu a doplnit informace zadané pomocí [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="70043-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="70043-109">Tyto informace se zobrazí v Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="70043-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="70043-110">Informace o Prohlížeč objektů naleznete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="70043-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="70043-111">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="70043-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70043-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="70043-112">Example</span></span>  
 <span data-ttu-id="70043-113">V tomto příkladu se používá značka `<remarks>` k vysvětlení toho, co metoda `UpdateRecord` dělá.</span><span class="sxs-lookup"><span data-stu-id="70043-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="70043-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70043-114">See also</span></span>

- [<span data-ttu-id="70043-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="70043-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
