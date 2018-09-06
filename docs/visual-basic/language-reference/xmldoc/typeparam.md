---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: d362f181921a39d274eaee78e85976522ce4fc15
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863186"
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="0b4be-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b4be-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="0b4be-103">Definuje typu parametru názvu a popisu.</span><span class="sxs-lookup"><span data-stu-id="0b4be-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b4be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b4be-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b4be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b4be-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="0b4be-106">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="0b4be-106">The name of the type parameter.</span></span> <span data-ttu-id="0b4be-107">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="0b4be-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="0b4be-108">Popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="0b4be-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b4be-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b4be-109">Remarks</span></span>  
 <span data-ttu-id="0b4be-110">Použití `<typeparam>` značku komentář pro obecný typ nebo deklarace obecného člena, popisující jeden z parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="0b4be-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="0b4be-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="0b4be-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b4be-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b4be-112">Example</span></span>  
 <span data-ttu-id="0b4be-113">V tomto příkladu `<typeparam>` značka, které popisují `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="0b4be-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0b4be-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b4be-114">See Also</span></span>  
 [<span data-ttu-id="0b4be-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="0b4be-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
