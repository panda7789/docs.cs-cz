---
ms.openlocfilehash: acd87c6ad5de3621cc90e5f3e1566592a4eb7e46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747069"
---

<span data-ttu-id="f5138-101">Pokud chcete použít jako oddělovač úvodní znak podtržítka, je nutné přidat následující prvek do projektu jazyka Visual Basic (\*.vbproj) souboru:</span><span class="sxs-lookup"><span data-stu-id="f5138-101">To use the underscore character as a leading separator, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="f5138-102">Další informace najdete v části [nastavení verze jazyka Visual Basic](../docs/visual-basic/language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="f5138-102">For more information see [setting the Visual Basic language version](../docs/visual-basic/language-reference/configure-language-version.md).</span></span>
