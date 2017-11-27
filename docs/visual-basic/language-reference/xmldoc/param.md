---
title: '&lt;Param&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09c7473cd88a701d8e46251be9b1c268c2dc8805
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="b55c2-102">&lt;Param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b55c2-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="b55c2-103">Definuje parametr název a popis.</span><span class="sxs-lookup"><span data-stu-id="b55c2-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b55c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b55c2-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b55c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b55c2-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b55c2-106">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="b55c2-106">The name of a method parameter.</span></span> <span data-ttu-id="b55c2-107">Uzavřete název do dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="b55c2-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="b55c2-108">Popis parametru.</span><span class="sxs-lookup"><span data-stu-id="b55c2-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b55c2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b55c2-109">Remarks</span></span>  
 <span data-ttu-id="b55c2-110">`<param>` Značky je třeba používat v komentář pro deklaraci metody k popisu jeden z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="b55c2-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="b55c2-111">Text pro `<param>` značky se zobrazí v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="b55c2-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="b55c2-112">Informace o parametrech technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="b55c2-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="b55c2-113">Další informace najdete v tématu [pomocí IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="b55c2-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="b55c2-114">Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="b55c2-114">Object Browser.</span></span> <span data-ttu-id="b55c2-115">Další informace najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="b55c2-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="b55c2-116">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="b55c2-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b55c2-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="b55c2-117">Example</span></span>  
 <span data-ttu-id="b55c2-118">Tento příklad používá `<param>` značka, které popisují `id` parametr.</span><span class="sxs-lookup"><span data-stu-id="b55c2-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b55c2-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b55c2-119">See Also</span></span>  
 [<span data-ttu-id="b55c2-120">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="b55c2-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
