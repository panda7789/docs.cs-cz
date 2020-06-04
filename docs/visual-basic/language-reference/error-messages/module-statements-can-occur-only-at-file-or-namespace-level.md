---
title: Příkazy 'Module' lze používat pouze na úrovni souboru nebo oboru názvů.
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: d01c30571fc34e142300ac8706c56d5e99175fcf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397204"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="0ab1c-102">Příkazy 'Module' lze používat pouze na úrovni souboru nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0ab1c-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="0ab1c-103">`Module`příkazy se musí nacházet v horní části zdrojového souboru hned po `Option` a `Imports` příkazy, globální atributy a deklarace oboru názvů, ale před všemi ostatními deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="0ab1c-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="0ab1c-104">**ID chyby:** BC30617</span><span class="sxs-lookup"><span data-stu-id="0ab1c-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0ab1c-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0ab1c-105">To correct this error</span></span>  
  
- <span data-ttu-id="0ab1c-106">Přesuňte `Module` příkaz na začátek deklarace oboru názvů nebo zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="0ab1c-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab1c-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ab1c-107">See also</span></span>

- [<span data-ttu-id="0ab1c-108">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="0ab1c-108">Module Statement</span></span>](../statements/module-statement.md)
