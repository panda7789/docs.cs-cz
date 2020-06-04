---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 2ad54845645172acb5b91935f5347a828510e3aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411483"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="9e078-101">\<typeparam> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e078-101">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="9e078-102">Definuje název a popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="9e078-102">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e078-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e078-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e078-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e078-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="9e078-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="9e078-105">The name of the type parameter.</span></span> <span data-ttu-id="9e078-106">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="9e078-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="9e078-107">Popis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="9e078-107">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e078-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e078-108">Remarks</span></span>  
 <span data-ttu-id="9e078-109">Použijte `<typeparam>` značku v komentáři pro obecný typ nebo deklaraci obecného člena k popisu jednoho z parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="9e078-109">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="9e078-110">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="9e078-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e078-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="9e078-111">Example</span></span>  
 <span data-ttu-id="9e078-112">Tento příklad používá `<typeparam>` značku k popisu `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="9e078-112">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="9e078-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e078-113">See also</span></span>

- [<span data-ttu-id="9e078-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="9e078-114">XML Comment Tags</span></span>](index.md)
