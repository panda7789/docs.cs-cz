---
title: '&lt;Vrátí&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: effc55bd65ae6c54575b7931529499505a9523cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598362"
---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="e89ff-102">&lt;Vrátí&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e89ff-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="e89ff-103">Určuje vrácenou hodnotu vlastnosti nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="e89ff-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e89ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e89ff-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e89ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e89ff-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="e89ff-106">Popis návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e89ff-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e89ff-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e89ff-107">Remarks</span></span>  
 <span data-ttu-id="e89ff-108">Použití `<returns>` značku komentář pro deklaraci metody k popisu návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e89ff-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="e89ff-109">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="e89ff-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e89ff-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e89ff-110">Example</span></span>  
 <span data-ttu-id="e89ff-111">Tento příklad používá `<returns>` značka, které popisují, co `DoesRecordExist` funkce vrátí.</span><span class="sxs-lookup"><span data-stu-id="e89ff-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e89ff-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e89ff-112">See Also</span></span>  
 [<span data-ttu-id="e89ff-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="e89ff-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
