---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 96b9754332b7b9c6c7823aecab6a93b0aa7ffd21
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975456"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="c5ada-102">\<Vrátí > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5ada-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="c5ada-103">Určuje návratovou hodnotu vlastnosti nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="c5ada-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5ada-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5ada-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5ada-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5ada-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="c5ada-106">Popis návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c5ada-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5ada-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5ada-107">Remarks</span></span>  
 <span data-ttu-id="c5ada-108">Použití `<returns>` značku komentáře pro deklaraci metody k popisu návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c5ada-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="c5ada-109">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="c5ada-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5ada-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5ada-110">Example</span></span>  
 <span data-ttu-id="c5ada-111">V tomto příkladu `<returns>` značka, které popisují, co `DoesRecordExist` vrací funkce.</span><span class="sxs-lookup"><span data-stu-id="c5ada-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c5ada-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5ada-112">See also</span></span>
- [<span data-ttu-id="c5ada-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="c5ada-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
