---
title: Výjimka komentáře XML musí mít atribut 'cref'.
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 54965f3796b6c5ef0e387cd354abcb5740476257
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321176"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="e9819-102">Výjimka komentáře XML musí mít atribut 'cref'.</span><span class="sxs-lookup"><span data-stu-id="e9819-102">XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="e9819-103">Značka > \<výjimka poskytuje způsob, jak zdokumentovat výjimky, které mohou být vyvolány metodou.</span><span class="sxs-lookup"><span data-stu-id="e9819-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="e9819-104">Požadovaný atribut `cref` Určuje název členu, který je kontrolován generátorem dokumentace.</span><span class="sxs-lookup"><span data-stu-id="e9819-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="e9819-105">Pokud člen existuje, je přeložen na kanonický název elementu v souboru dokumentace.</span><span class="sxs-lookup"><span data-stu-id="e9819-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="e9819-106">**ID chyby:** BC42319</span><span class="sxs-lookup"><span data-stu-id="e9819-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e9819-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e9819-107">To correct this error</span></span>

<span data-ttu-id="e9819-108">Přidejte atribut `cref` k výjimce následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e9819-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="e9819-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9819-109">See also</span></span>

- [<span data-ttu-id="e9819-110">\<exception></span><span class="sxs-lookup"><span data-stu-id="e9819-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="e9819-111">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="e9819-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="e9819-112">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="e9819-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
