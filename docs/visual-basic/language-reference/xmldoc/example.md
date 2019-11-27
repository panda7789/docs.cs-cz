---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f36ac1337dd0d1400180fbd3deae2bb24ad9c58
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348484"
---
# <a name="example-visual-basic"></a><span data-ttu-id="a54aa-101">\<příklad > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a54aa-101">\<example> (Visual Basic)</span></span>
<span data-ttu-id="a54aa-102">Určuje příklad člena.</span><span class="sxs-lookup"><span data-stu-id="a54aa-102">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a54aa-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a54aa-103">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a54aa-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="a54aa-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="a54aa-105">Popis ukázky kódu.</span><span class="sxs-lookup"><span data-stu-id="a54aa-105">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a54aa-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a54aa-106">Remarks</span></span>  
 <span data-ttu-id="a54aa-107">Značka `<example>` umožňuje zadat příklad použití metody nebo jiného člena knihovny.</span><span class="sxs-lookup"><span data-stu-id="a54aa-107">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="a54aa-108">To běžně zahrnuje použití značky [> kódu\<](../../../visual-basic/language-reference/xmldoc/code.md) .</span><span class="sxs-lookup"><span data-stu-id="a54aa-108">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="a54aa-109">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="a54aa-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a54aa-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a54aa-110">Example</span></span>  
 <span data-ttu-id="a54aa-111">V tomto příkladu se používá značka `<example>` k zahrnutí příkladu pro použití pole `ID`.</span><span class="sxs-lookup"><span data-stu-id="a54aa-111">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a54aa-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a54aa-112">See also</span></span>

- [<span data-ttu-id="a54aa-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="a54aa-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
