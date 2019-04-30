---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 014623be84f9d7eb8a25ac4aadcce450f158c154
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940748"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="e53c1-102">\<typeparam > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e53c1-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="e53c1-103">Definuje typu parametru názvu a popisu.</span><span class="sxs-lookup"><span data-stu-id="e53c1-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e53c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e53c1-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e53c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e53c1-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e53c1-106">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="e53c1-106">The name of the type parameter.</span></span> <span data-ttu-id="e53c1-107">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="e53c1-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="e53c1-108">Popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="e53c1-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e53c1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e53c1-109">Remarks</span></span>  
 <span data-ttu-id="e53c1-110">Použití `<typeparam>` značku komentář pro obecný typ nebo deklarace obecného člena, popisující jeden z parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="e53c1-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="e53c1-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="e53c1-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e53c1-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e53c1-112">Example</span></span>  
 <span data-ttu-id="e53c1-113">V tomto příkladu `<typeparam>` značka, které popisují `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="e53c1-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="e53c1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e53c1-114">See also</span></span>

- [<span data-ttu-id="e53c1-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="e53c1-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
