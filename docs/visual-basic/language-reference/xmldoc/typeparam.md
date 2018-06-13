---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 76e0e8d4757f29bb5df82ea1482beff3dd43c0e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598011"
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="7860a-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7860a-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="7860a-103">Definuje typ parametru název a popis.</span><span class="sxs-lookup"><span data-stu-id="7860a-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7860a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7860a-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7860a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7860a-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="7860a-106">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="7860a-106">The name of the type parameter.</span></span> <span data-ttu-id="7860a-107">Uzavřete název do dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="7860a-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="7860a-108">Popis parametr typu.</span><span class="sxs-lookup"><span data-stu-id="7860a-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7860a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7860a-109">Remarks</span></span>  
 <span data-ttu-id="7860a-110">Použití `<typeparam>` značku komentář pro obecný typ nebo deklarace obecné členů k popisu jeden z parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="7860a-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="7860a-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="7860a-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7860a-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7860a-112">Example</span></span>  
 <span data-ttu-id="7860a-113">Tento příklad používá `<typeparam>` značka, které popisují `id` parametr.</span><span class="sxs-lookup"><span data-stu-id="7860a-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7860a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="7860a-114">See Also</span></span>  
 [<span data-ttu-id="7860a-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="7860a-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
