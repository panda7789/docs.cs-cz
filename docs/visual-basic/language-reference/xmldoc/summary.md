---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 3bc4393d2fa14f804c6383780e238b1ac2610a94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352204"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="c5153-101">\<summary> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5153-101">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="c5153-102">Specifies the summary of the member.</span><span class="sxs-lookup"><span data-stu-id="c5153-102">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5153-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5153-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5153-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5153-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="c5153-105">A summary of the object.</span><span class="sxs-lookup"><span data-stu-id="c5153-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5153-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5153-106">Remarks</span></span>  
 <span data-ttu-id="c5153-107">Use the `<summary>` tag to describe a type or a type member.</span><span class="sxs-lookup"><span data-stu-id="c5153-107">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="c5153-108">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span><span class="sxs-lookup"><span data-stu-id="c5153-108">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="c5153-109">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span><span class="sxs-lookup"><span data-stu-id="c5153-109">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="c5153-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="c5153-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="c5153-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span><span class="sxs-lookup"><span data-stu-id="c5153-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5153-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5153-112">Example</span></span>  
 <span data-ttu-id="c5153-113">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span><span class="sxs-lookup"><span data-stu-id="c5153-113">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c5153-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5153-114">See also</span></span>

- [<span data-ttu-id="c5153-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="c5153-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
