---
title: "&lt;výjimka&gt; (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d718a7c2213a61f7f60ed80a04f9bd03f6c770a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltexceptiongt-visual-basic"></a><span data-ttu-id="8dde5-102">&lt;výjimka&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8dde5-102">&lt;exception&gt; (Visual Basic)</span></span>
<span data-ttu-id="8dde5-103">Určuje, výjimek, které může být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="8dde5-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dde5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dde5-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8dde5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dde5-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="8dde5-106">Odkaz na výjimku, která je k dispozici z aktuální prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="8dde5-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="8dde5-107">Kompilátor kontroluje, zda výjimka existuje a překládá `member` na element kanonický název ve výstupu XML.</span><span class="sxs-lookup"><span data-stu-id="8dde5-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="8dde5-108">`member`musí být v rámci dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="8dde5-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="8dde5-109">Popis.</span><span class="sxs-lookup"><span data-stu-id="8dde5-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dde5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8dde5-110">Remarks</span></span>  
 <span data-ttu-id="8dde5-111">Použití `<exception>` značky k určení výjimek, které může být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="8dde5-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="8dde5-112">Tato značka se použije k definici metody.</span><span class="sxs-lookup"><span data-stu-id="8dde5-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="8dde5-113">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="8dde5-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dde5-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="8dde5-114">Example</span></span>  
 <span data-ttu-id="8dde5-115">Tento příklad používá `<exception>` značka, které popisují výjimku, `IntDivide` funkce můžete vyvolat.</span><span class="sxs-lookup"><span data-stu-id="8dde5-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8dde5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8dde5-116">See Also</span></span>  
 [<span data-ttu-id="8dde5-117">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="8dde5-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
