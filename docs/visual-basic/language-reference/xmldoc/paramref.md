---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 763e311dfb46ceeed358c3b3bebd6212d3e2489c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598659"
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="5a50d-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a50d-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="5a50d-103">Formátuje slovo jako parametr.</span><span class="sxs-lookup"><span data-stu-id="5a50d-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a50d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a50d-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a50d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a50d-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5a50d-106">Název parametru, který bude odkazovat na.</span><span class="sxs-lookup"><span data-stu-id="5a50d-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="5a50d-107">Uzavřete název do dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="5a50d-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a50d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a50d-108">Remarks</span></span>  
 <span data-ttu-id="5a50d-109">`<paramref>` Značky poskytuje způsob, jak znamenat, že slovo parametr.</span><span class="sxs-lookup"><span data-stu-id="5a50d-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="5a50d-110">Soubor XML lze zpracovat formátování tento parametr nějakým způsobem distinct.</span><span class="sxs-lookup"><span data-stu-id="5a50d-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="5a50d-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="5a50d-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a50d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a50d-112">Example</span></span>  
 <span data-ttu-id="5a50d-113">Tento příklad používá `<paramref>` značky k odkazování na `id` parametr.</span><span class="sxs-lookup"><span data-stu-id="5a50d-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5a50d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a50d-114">See Also</span></span>  
 [<span data-ttu-id="5a50d-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="5a50d-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
