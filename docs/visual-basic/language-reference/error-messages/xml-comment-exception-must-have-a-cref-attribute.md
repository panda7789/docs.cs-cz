---
title: Výjimka komentáře XML musí mít atribut 'cref'.
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: a974df5d2305b88946981d0d258a8088b23d3fc3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813285"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="ade3e-102">Výjimka komentáře XML musí mít atribut 'cref'.</span><span class="sxs-lookup"><span data-stu-id="ade3e-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="ade3e-103">\<Výjimky > značky poskytuje způsob, jak dokumentovat výjimky, které mohou být vyvolány metodou.</span><span class="sxs-lookup"><span data-stu-id="ade3e-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="ade3e-104">Požadované `cref` atribut určuje název člena, který je zaškrtnuté políčko generátorem dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="ade3e-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="ade3e-105">Pokud existuje člen je přeložit název canonical elementu v souboru dokumentace.</span><span class="sxs-lookup"><span data-stu-id="ade3e-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="ade3e-106">**ID chyby:** BC42319</span><span class="sxs-lookup"><span data-stu-id="ade3e-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ade3e-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ade3e-107">To correct this error</span></span>  
  
-   <span data-ttu-id="ade3e-108">Přidat `cref` atribut na výjimku následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ade3e-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ade3e-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ade3e-109">See also</span></span>

- [<span data-ttu-id="ade3e-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="ade3e-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="ade3e-111">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="ade3e-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="ade3e-112">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="ade3e-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
