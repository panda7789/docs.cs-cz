---
title: "&lt;kód&gt; (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7c1d8ab3db0c36c6a2935b9ffbef15e87df5ebc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="c6393-102">&lt;kód&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6393-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="c6393-103">Označuje, že je text více řádků kódu.</span><span class="sxs-lookup"><span data-stu-id="c6393-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6393-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6393-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6393-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6393-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="c6393-106">Text k označení jako kódu.</span><span class="sxs-lookup"><span data-stu-id="c6393-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6393-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6393-107">Remarks</span></span>  
 <span data-ttu-id="c6393-108">Použití `<code>` značky k označení jako kódu více řádků.</span><span class="sxs-lookup"><span data-stu-id="c6393-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="c6393-109">Použití [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) indikující, že text v rámci popis by měl být označen jako kód.</span><span class="sxs-lookup"><span data-stu-id="c6393-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="c6393-110">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="c6393-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6393-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6393-111">Example</span></span>  
 <span data-ttu-id="c6393-112">Tento příklad používá \<kód > značka, které zahrnují ukázkový kód pro použití `ID` pole.</span><span class="sxs-lookup"><span data-stu-id="c6393-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c6393-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6393-113">See Also</span></span>  
 [<span data-ttu-id="c6393-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="c6393-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
