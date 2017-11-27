---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e57cae8fd4b93fee59992d717135ad7d3d78be5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="3f2db-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f2db-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="3f2db-103">Označuje, že je text v rámci popis kódu.</span><span class="sxs-lookup"><span data-stu-id="3f2db-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f2db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f2db-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f2db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f2db-105">Parameters</span></span>  
  
|<span data-ttu-id="3f2db-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="3f2db-106">Parameter</span></span>|<span data-ttu-id="3f2db-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3f2db-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="3f2db-108">Text, který chcete označit jako kód.</span><span class="sxs-lookup"><span data-stu-id="3f2db-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f2db-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f2db-109">Remarks</span></span>  
 <span data-ttu-id="3f2db-110">`<c>` Značky poskytuje způsob, jak znamenat, že text v rámci popis by měl být označen jako kód.</span><span class="sxs-lookup"><span data-stu-id="3f2db-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="3f2db-111">Použití [ \<kód >](../../../visual-basic/language-reference/xmldoc/code.md) k označení jako kódu více řádků.</span><span class="sxs-lookup"><span data-stu-id="3f2db-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="3f2db-112">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="3f2db-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f2db-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f2db-113">Example</span></span>  
 <span data-ttu-id="3f2db-114">Tento příklad používá `<c>` značky v části Souhrn k označení, že `Counter` je kód.</span><span class="sxs-lookup"><span data-stu-id="3f2db-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3f2db-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f2db-115">See Also</span></span>  
 [<span data-ttu-id="3f2db-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="3f2db-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
