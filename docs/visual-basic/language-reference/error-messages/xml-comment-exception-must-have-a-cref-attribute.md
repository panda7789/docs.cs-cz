---
title: Výjimka komentáře XML musí mít &#39;cref&#39; atribut
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: abe9fe0f6216f81fa223fe83a122b580577e1c32
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930025"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="df629-102">Výjimka komentáře XML musí mít &#39;cref&#39; atribut</span><span class="sxs-lookup"><span data-stu-id="df629-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="df629-103">\<Výjimky > značky poskytuje způsob, jak dokumentovat výjimky, které mohou být vyvolány metodou.</span><span class="sxs-lookup"><span data-stu-id="df629-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="df629-104">Požadované `cref` atribut určuje název člena, který je zaškrtnuté políčko generátorem dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="df629-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="df629-105">Pokud existuje člen je přeložit název canonical elementu v souboru dokumentace.</span><span class="sxs-lookup"><span data-stu-id="df629-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="df629-106">**ID chyby:** BC42319</span><span class="sxs-lookup"><span data-stu-id="df629-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="df629-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="df629-107">To correct this error</span></span>  
  
-   <span data-ttu-id="df629-108">Přidat `cref` atribut na výjimku následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="df629-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="df629-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="df629-109">See Also</span></span>  
 [<span data-ttu-id="df629-110">\<výjimky ></span><span class="sxs-lookup"><span data-stu-id="df629-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="df629-111">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="df629-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="df629-112">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="df629-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
