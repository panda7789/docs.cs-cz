---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 153f5ddeeb7d09159049af4d466b0695f5cb6f23
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331356"
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="347c1-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="347c1-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="347c1-103">Formátuje slova jako parametr.</span><span class="sxs-lookup"><span data-stu-id="347c1-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="347c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="347c1-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="347c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="347c1-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="347c1-106">Název parametru jako reference.</span><span class="sxs-lookup"><span data-stu-id="347c1-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="347c1-107">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="347c1-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="347c1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="347c1-108">Remarks</span></span>  
 <span data-ttu-id="347c1-109">`<paramref>` Značky poskytuje způsob, jak určit, že je slovo parametru.</span><span class="sxs-lookup"><span data-stu-id="347c1-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="347c1-110">Soubor XML mohou být zpracovány k nějakým způsobem odlišné formátování tento parametr.</span><span class="sxs-lookup"><span data-stu-id="347c1-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="347c1-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="347c1-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="347c1-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="347c1-112">Example</span></span>  
 <span data-ttu-id="347c1-113">Tento příklad používá `<paramref>` značku k odkazování `id` parametr.</span><span class="sxs-lookup"><span data-stu-id="347c1-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="347c1-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="347c1-114">See Also</span></span>  
 [<span data-ttu-id="347c1-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="347c1-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
