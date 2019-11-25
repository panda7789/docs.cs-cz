---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 78227a17584271f91283198e95f5aa389b3ef14b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352284"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="28981-101">\<paramref> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28981-101">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="28981-102">Formats a word as a parameter.</span><span class="sxs-lookup"><span data-stu-id="28981-102">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28981-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28981-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="28981-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="28981-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="28981-105">The name of the parameter to refer to.</span><span class="sxs-lookup"><span data-stu-id="28981-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="28981-106">Enclose the name in double quotation marks (" ").</span><span class="sxs-lookup"><span data-stu-id="28981-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28981-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28981-107">Remarks</span></span>  
 <span data-ttu-id="28981-108">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span><span class="sxs-lookup"><span data-stu-id="28981-108">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="28981-109">The XML file can be processed to format this parameter in some distinct way.</span><span class="sxs-lookup"><span data-stu-id="28981-109">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="28981-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span><span class="sxs-lookup"><span data-stu-id="28981-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28981-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="28981-111">Example</span></span>  
 <span data-ttu-id="28981-112">This example uses the `<paramref>` tag to refer to the `id` parameter.</span><span class="sxs-lookup"><span data-stu-id="28981-112">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="28981-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28981-113">See also</span></span>

- [<span data-ttu-id="28981-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="28981-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
