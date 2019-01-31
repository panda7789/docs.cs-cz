---
title: Příkazy 'Module' lze používat pouze na úrovni souboru nebo oboru názvů.
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: 0820763cce9cc27f9a379ed5e766e0691a75f36b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271262"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="21123-102">Příkazy 'Module' lze používat pouze na úrovni souboru nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="21123-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="21123-103">`Module` příkazy musí být uvedena v horní části zdrojového souboru ihned po `Option` a `Imports` příkazy, globální atributy a deklarace oboru názvů, ale před ostatními deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="21123-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="21123-104">**ID chyby:** BC30617</span><span class="sxs-lookup"><span data-stu-id="21123-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="21123-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="21123-105">To correct this error</span></span>  
  
-   <span data-ttu-id="21123-106">Přesunout `Module` příkaz do horní části obor názvů deklarace nebo zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="21123-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21123-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21123-107">See also</span></span>
- [<span data-ttu-id="21123-108">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="21123-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
