---
title: '&lt;para&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e2a034974ed94b18da374fbd372063ea4d575440
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="ac542-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac542-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="ac542-103">Určuje, že obsah je formátován jako odstavec.</span><span class="sxs-lookup"><span data-stu-id="ac542-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac542-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac542-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac542-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac542-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="ac542-106">Text odstavce.</span><span class="sxs-lookup"><span data-stu-id="ac542-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac542-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac542-107">Remarks</span></span>  
 <span data-ttu-id="ac542-108">`<para>` Značka je pro použití uvnitř značky, jako například [ \<souhrnné >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<Poznámky >](../../../visual-basic/language-reference/xmldoc/remarks.md), nebo [ \<vrátí >](../../../visual-basic/language-reference/xmldoc/returns.md), a umožňuje přidat struktura na text.</span><span class="sxs-lookup"><span data-stu-id="ac542-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="ac542-109">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="ac542-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac542-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac542-110">Example</span></span>  
 <span data-ttu-id="ac542-111">Tento příklad používá `<para>` značka oddílu poznámky pro rozdělení `UpdateRecord` metoda do dva odstavce.</span><span class="sxs-lookup"><span data-stu-id="ac542-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ac542-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac542-112">See Also</span></span>  
 [<span data-ttu-id="ac542-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="ac542-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
