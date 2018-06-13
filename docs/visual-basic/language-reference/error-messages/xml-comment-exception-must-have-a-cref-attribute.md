---
title: Výjimka komentáře XML musí mít &#39;cref&#39; atribut
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: ee91513ef94e2abbe01d3ac09796b7fdf8e129ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597380"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="56e2a-102">Výjimka komentáře XML musí mít &#39;cref&#39; atribut</span><span class="sxs-lookup"><span data-stu-id="56e2a-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="56e2a-103">\<Výjimka > Značka poskytuje způsob, jak dokumentu výjimky, které mohou být vyvolány metodou.</span><span class="sxs-lookup"><span data-stu-id="56e2a-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="56e2a-104">Požadované `cref` atribut určuje název člena, který je zaškrtnuta možnost generátorem dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="56e2a-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="56e2a-105">Pokud existuje člena, je přeložit název kanonický elementu v dokumentaci k souboru.</span><span class="sxs-lookup"><span data-stu-id="56e2a-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="56e2a-106">**ID chyby:** BC42319</span><span class="sxs-lookup"><span data-stu-id="56e2a-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="56e2a-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="56e2a-107">To correct this error</span></span>  
  
-   <span data-ttu-id="56e2a-108">Přidat `cref` atribut výjimka následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="56e2a-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="56e2a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="56e2a-109">See Also</span></span>  
 [<span data-ttu-id="56e2a-110">\<Výjimka ></span><span class="sxs-lookup"><span data-stu-id="56e2a-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="56e2a-111">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="56e2a-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="56e2a-112">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="56e2a-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
