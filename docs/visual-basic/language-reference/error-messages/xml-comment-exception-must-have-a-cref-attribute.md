---
title: Výjimka komentáře XML musí mít atribut 'cref'.
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592029"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="7801a-102">Výjimka komentáře XML musí mít atribut 'cref'.</span><span class="sxs-lookup"><span data-stu-id="7801a-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="7801a-103">Značka > \<exception poskytuje způsob, jak zdokumentovat výjimky, které mohou být vyvolány metodou.</span><span class="sxs-lookup"><span data-stu-id="7801a-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="7801a-104">Požadovaný atribut `cref` určuje název členu, který je kontrolován generátorem dokumentace.</span><span class="sxs-lookup"><span data-stu-id="7801a-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="7801a-105">Pokud člen existuje, je přeložen na kanonický název elementu v souboru dokumentace.</span><span class="sxs-lookup"><span data-stu-id="7801a-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="7801a-106">**ID chyby:** BC42319</span><span class="sxs-lookup"><span data-stu-id="7801a-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7801a-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7801a-107">To correct this error</span></span>  
  
- <span data-ttu-id="7801a-108">Přidejte atribut `cref` pro výjimku následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7801a-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    <span data-ttu-id="7801a-109">xml</span><span class="sxs-lookup"><span data-stu-id="7801a-109">xml</span></span>  
    <span data-ttu-id="7801a-110"><exception cref="member">Popis</exception></span><span class="sxs-lookup"><span data-stu-id="7801a-110">'''<exception cref="member">description</exception></span></span>  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
