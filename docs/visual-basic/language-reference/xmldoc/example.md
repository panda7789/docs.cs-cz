---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 42f40581d252956433165789d6674234a295867c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400137"
---
# <a name="example-visual-basic"></a><span data-ttu-id="69a0f-101">\<example> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69a0f-101">\<example> (Visual Basic)</span></span>
<span data-ttu-id="69a0f-102">Určuje příklad člena.</span><span class="sxs-lookup"><span data-stu-id="69a0f-102">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69a0f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69a0f-103">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="69a0f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="69a0f-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="69a0f-105">Popis ukázky kódu.</span><span class="sxs-lookup"><span data-stu-id="69a0f-105">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69a0f-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69a0f-106">Remarks</span></span>  
 <span data-ttu-id="69a0f-107">`<example>`Značka umožňuje zadat příklad použití metody nebo jiného člena knihovny.</span><span class="sxs-lookup"><span data-stu-id="69a0f-107">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="69a0f-108">To běžně zahrnuje použití [\<code>](code.md) značky.</span><span class="sxs-lookup"><span data-stu-id="69a0f-108">This commonly involves using the [\<code>](code.md) tag.</span></span>  
  
 <span data-ttu-id="69a0f-109">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="69a0f-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69a0f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="69a0f-110">Example</span></span>  
 <span data-ttu-id="69a0f-111">Tento příklad používá `<example>` značku k zahrnutí příkladu pro použití `ID` pole.</span><span class="sxs-lookup"><span data-stu-id="69a0f-111">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="69a0f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="69a0f-112">See also</span></span>

- [<span data-ttu-id="69a0f-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="69a0f-113">XML Comment Tags</span></span>](index.md)
