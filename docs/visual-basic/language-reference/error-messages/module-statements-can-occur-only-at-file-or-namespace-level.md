---
title: '&#39;Modul&#39; příkazy lze používat pouze na úrovni souboru nebo oboru názvů'
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: 53199c2d7081445dc5490d5c54c98f93ee7522eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593162"
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="b5549-102">&#39;Modul&#39; příkazy lze používat pouze na úrovni souboru nebo oboru názvů</span><span class="sxs-lookup"><span data-stu-id="b5549-102">&#39;Module&#39; statements can occur only at file or namespace level</span></span>
<span data-ttu-id="b5549-103">`Module` příkazy musí být v horní části souboru zdroje ihned po `Option` a `Imports` příkazy, globálními atributy a deklarace oboru názvů, ale před všechny ostatní deklarace.</span><span class="sxs-lookup"><span data-stu-id="b5549-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="b5549-104">**ID chyby:** BC30617</span><span class="sxs-lookup"><span data-stu-id="b5549-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5549-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b5549-105">To correct this error</span></span>  
  
-   <span data-ttu-id="b5549-106">Přesunout `Module` příkaz na začátek oboru názvů deklarace nebo zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="b5549-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5549-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5549-107">See Also</span></span>  
 [<span data-ttu-id="b5549-108">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="b5549-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
