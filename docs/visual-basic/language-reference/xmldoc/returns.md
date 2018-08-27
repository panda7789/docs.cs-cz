---
title: '&lt;Vrátí&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 47debcef2c6ce56fda4c4a0818c8e813b41ebad1
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925015"
---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="e707b-102">&lt;Vrátí&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e707b-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="e707b-103">Určuje návratovou hodnotu vlastnosti nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="e707b-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e707b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e707b-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e707b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e707b-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="e707b-106">Popis návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e707b-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e707b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e707b-107">Remarks</span></span>  
 <span data-ttu-id="e707b-108">Použití `<returns>` značku komentáře pro deklaraci metody k popisu návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e707b-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="e707b-109">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="e707b-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e707b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e707b-110">Example</span></span>  
 <span data-ttu-id="e707b-111">V tomto příkladu `<returns>` značka, které popisují, co `DoesRecordExist` vrací funkce.</span><span class="sxs-lookup"><span data-stu-id="e707b-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e707b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e707b-112">See Also</span></span>  
 [<span data-ttu-id="e707b-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="e707b-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
