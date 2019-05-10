---
title: Příkazy 'Module' lze používat pouze na úrovni souboru nebo oboru názvů.
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: fc3c102dbfe7c55e66093421bc11379d48ba000d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592087"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="afdfc-102">Příkazy 'Module' lze používat pouze na úrovni souboru nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="afdfc-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="afdfc-103">`Module` příkazy musí být uvedena v horní části zdrojového souboru ihned po `Option` a `Imports` příkazy, globální atributy a deklarace oboru názvů, ale před ostatními deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="afdfc-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="afdfc-104">**ID chyby:** BC30617</span><span class="sxs-lookup"><span data-stu-id="afdfc-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="afdfc-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="afdfc-105">To correct this error</span></span>  
  
- <span data-ttu-id="afdfc-106">Přesunout `Module` příkaz do horní části obor názvů deklarace nebo zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="afdfc-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afdfc-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afdfc-107">See also</span></span>

- [<span data-ttu-id="afdfc-108">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="afdfc-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
