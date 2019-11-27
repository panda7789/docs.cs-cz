---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: b327e548bcdce1522a888855bd88e3150695147b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352248"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="0bc33-101">\<poznámky > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bc33-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="0bc33-102">Určuje oddíl poznámky pro člena.</span><span class="sxs-lookup"><span data-stu-id="0bc33-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc33-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bc33-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bc33-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bc33-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="0bc33-105">Popis člena</span><span class="sxs-lookup"><span data-stu-id="0bc33-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bc33-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bc33-106">Remarks</span></span>  
 <span data-ttu-id="0bc33-107">Pomocí značky `<remarks>` přidáte informace o typu a doplníte informace zadané pomocí [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="0bc33-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="0bc33-108">Tyto informace se zobrazí v Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="0bc33-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="0bc33-109">Informace o Prohlížeč objektů naleznete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="0bc33-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="0bc33-110">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="0bc33-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bc33-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="0bc33-111">Example</span></span>  
 <span data-ttu-id="0bc33-112">V tomto příkladu se používá značka `<remarks>` k vysvětlení toho, co metoda `UpdateRecord` dělá.</span><span class="sxs-lookup"><span data-stu-id="0bc33-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0bc33-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bc33-113">See also</span></span>

- [<span data-ttu-id="0bc33-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="0bc33-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
