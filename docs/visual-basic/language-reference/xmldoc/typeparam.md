---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: d7fb980545a532e39310ea3e9d663a2b5a81a006
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968449"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="af3bd-102">\<typeparam > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af3bd-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="af3bd-103">Definuje typu parametru názvu a popisu.</span><span class="sxs-lookup"><span data-stu-id="af3bd-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af3bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af3bd-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af3bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af3bd-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="af3bd-106">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="af3bd-106">The name of the type parameter.</span></span> <span data-ttu-id="af3bd-107">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="af3bd-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="af3bd-108">Popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="af3bd-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af3bd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af3bd-109">Remarks</span></span>  
 <span data-ttu-id="af3bd-110">Použití `<typeparam>` značku komentář pro obecný typ nebo deklarace obecného člena, popisující jeden z parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="af3bd-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="af3bd-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="af3bd-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af3bd-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="af3bd-112">Example</span></span>  
 <span data-ttu-id="af3bd-113">V tomto příkladu `<typeparam>` značka, které popisují `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="af3bd-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="af3bd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af3bd-114">See also</span></span>
- [<span data-ttu-id="af3bd-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="af3bd-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
