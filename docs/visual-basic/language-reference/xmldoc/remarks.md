---
title: "&lt;Poznámky&gt; (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f70c2d7df190d2ff8187882a9176dbe98984296
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="89fae-102">&lt;Poznámky&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89fae-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="89fae-103">Určuje oddílu poznámky pro člena.</span><span class="sxs-lookup"><span data-stu-id="89fae-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89fae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89fae-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89fae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89fae-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="89fae-106">Popis člena.</span><span class="sxs-lookup"><span data-stu-id="89fae-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89fae-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89fae-107">Remarks</span></span>  
 <span data-ttu-id="89fae-108">Použití `<remarks>` značky k přidání informací o typu, dodávání zadaných s informací o [ \<souhrnné >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="89fae-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="89fae-109">Tato informace se zobrazí v prohlížeči objektů.</span><span class="sxs-lookup"><span data-stu-id="89fae-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="89fae-110">Informace o prohlížeči objektů najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="89fae-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="89fae-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="89fae-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89fae-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="89fae-112">Example</span></span>  
 <span data-ttu-id="89fae-113">Tento příklad používá `<remarks>` značka, které popisují, co `UpdateRecord` metoda nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="89fae-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="89fae-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="89fae-114">See Also</span></span>  
 [<span data-ttu-id="89fae-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="89fae-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
