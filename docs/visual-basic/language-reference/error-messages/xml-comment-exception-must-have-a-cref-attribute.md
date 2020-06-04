---
title: Výjimka komentáře XML musí mít atribut 'cref'.
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: c498675ab6ae616fb63d3d76ef60bcac7e247145
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406505"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="4d583-102">Výjimka komentáře XML musí mít atribut 'cref'.</span><span class="sxs-lookup"><span data-stu-id="4d583-102">XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="4d583-103">\<exception>Značka poskytuje způsob, jak zdokumentovat výjimky, které mohou být vyvolány metodou.</span><span class="sxs-lookup"><span data-stu-id="4d583-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="4d583-104">Požadovaný `cref` atribut určuje název členu, který je kontrolován generátorem dokumentace.</span><span class="sxs-lookup"><span data-stu-id="4d583-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="4d583-105">Pokud člen existuje, je přeložen na kanonický název elementu v souboru dokumentace.</span><span class="sxs-lookup"><span data-stu-id="4d583-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="4d583-106">**ID chyby:** BC42319</span><span class="sxs-lookup"><span data-stu-id="4d583-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4d583-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4d583-107">To correct this error</span></span>

<span data-ttu-id="4d583-108">Přidejte `cref` atribut k výjimce následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4d583-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="4d583-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d583-109">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="4d583-110">Postupy: Vytvoření dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="4d583-110">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="4d583-111">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="4d583-111">XML Comment Tags</span></span>](../xmldoc/index.md)
