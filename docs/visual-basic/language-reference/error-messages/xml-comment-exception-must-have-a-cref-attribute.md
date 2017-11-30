---
title: "Výjimka komentáře XML musí mít & č. 39; cref & č. 39; atribut"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords: BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c22c9cd9415faf17d027c3751d166662a92b50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="03c88-102">Výjimka komentáře XML musí mít & č. 39; cref & č. 39; atribut</span><span class="sxs-lookup"><span data-stu-id="03c88-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="03c88-103">\<Výjimka > Značka poskytuje způsob, jak dokumentu výjimky, které mohou být vyvolány metodou.</span><span class="sxs-lookup"><span data-stu-id="03c88-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="03c88-104">Požadované `cref` atribut určuje název člena, který je zaškrtnuta možnost generátorem dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="03c88-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="03c88-105">Pokud existuje člena, je přeložit název kanonický elementu v dokumentaci k souboru.</span><span class="sxs-lookup"><span data-stu-id="03c88-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="03c88-106">**ID chyby:** BC42319</span><span class="sxs-lookup"><span data-stu-id="03c88-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="03c88-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="03c88-107">To correct this error</span></span>  
  
-   <span data-ttu-id="03c88-108">Přidat `cref` atribut výjimka následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="03c88-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="03c88-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="03c88-109">See Also</span></span>  
 [<span data-ttu-id="03c88-110">\<Výjimka ></span><span class="sxs-lookup"><span data-stu-id="03c88-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="03c88-111">Postupy: vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="03c88-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="03c88-112">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="03c88-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
