---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4405fdf2defbb27aa2146d20083fd406d1f07236
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352288"
---
# <a name="param-visual-basic"></a><span data-ttu-id="faa8d-101">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="faa8d-101">\<param> (Visual Basic)</span></span>
<span data-ttu-id="faa8d-102">Defines a parameter name and description.</span><span class="sxs-lookup"><span data-stu-id="faa8d-102">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faa8d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faa8d-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="faa8d-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="faa8d-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="faa8d-105">The name of a method parameter.</span><span class="sxs-lookup"><span data-stu-id="faa8d-105">The name of a method parameter.</span></span> <span data-ttu-id="faa8d-106">Enclose the name in double quotation marks (" ").</span><span class="sxs-lookup"><span data-stu-id="faa8d-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="faa8d-107">A description for the parameter.</span><span class="sxs-lookup"><span data-stu-id="faa8d-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faa8d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="faa8d-108">Remarks</span></span>  
 <span data-ttu-id="faa8d-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span><span class="sxs-lookup"><span data-stu-id="faa8d-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="faa8d-110">The text for the `<param>` tag will appear in the following locations:</span><span class="sxs-lookup"><span data-stu-id="faa8d-110">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="faa8d-111">Parameter Info of IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="faa8d-111">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="faa8d-112">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="faa8d-112">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="faa8d-113">Object Browser.</span><span class="sxs-lookup"><span data-stu-id="faa8d-113">Object Browser.</span></span> <span data-ttu-id="faa8d-114">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="faa8d-114">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="faa8d-115">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span><span class="sxs-lookup"><span data-stu-id="faa8d-115">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="faa8d-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="faa8d-116">Example</span></span>  
 <span data-ttu-id="faa8d-117">This example uses the `<param>` tag to describe the `id` parameter.</span><span class="sxs-lookup"><span data-stu-id="faa8d-117">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="faa8d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="faa8d-118">See also</span></span>

- [<span data-ttu-id="faa8d-119">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="faa8d-119">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
