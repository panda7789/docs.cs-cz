---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: dbd99997fed33c192a2160fb45a739addbae254a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524620"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="95c9d-102">\<typeparam > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95c9d-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="95c9d-103">Definuje název a popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="95c9d-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95c9d-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="95c9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95c9d-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="95c9d-106">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="95c9d-106">The name of the type parameter.</span></span> <span data-ttu-id="95c9d-107">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="95c9d-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="95c9d-108">Popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="95c9d-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95c9d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95c9d-109">Remarks</span></span>  
 <span data-ttu-id="95c9d-110">Použijte značku `<typeparam>` v komentáři pro obecný typ nebo deklaraci obecného člena k popisu jednoho z parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="95c9d-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="95c9d-111">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="95c9d-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95c9d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="95c9d-112">Example</span></span>  
 <span data-ttu-id="95c9d-113">V tomto příkladu se používá značka `<typeparam>` k popisu `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="95c9d-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="95c9d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95c9d-114">See also</span></span>

- [<span data-ttu-id="95c9d-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="95c9d-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
