---
title: '&#39;Modul&#39; příkazy lze používat pouze na úrovni souboru nebo oboru názvů'
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: bdbf8df5942e9df4b9696aeea4e3492121efe21a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746309"
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="79cc4-102">&#39;Modul&#39; příkazy lze používat pouze na úrovni souboru nebo oboru názvů</span><span class="sxs-lookup"><span data-stu-id="79cc4-102">&#39;Module&#39; statements can occur only at file or namespace level</span></span>
<span data-ttu-id="79cc4-103">`Module` příkazy musí být uvedena v horní části zdrojového souboru ihned po `Option` a `Imports` příkazy, globální atributy a deklarace oboru názvů, ale před ostatními deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="79cc4-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="79cc4-104">**ID chyby:** BC30617</span><span class="sxs-lookup"><span data-stu-id="79cc4-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="79cc4-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="79cc4-105">To correct this error</span></span>  
  
-   <span data-ttu-id="79cc4-106">Přesunout `Module` příkaz do horní části obor názvů deklarace nebo zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="79cc4-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79cc4-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79cc4-107">See also</span></span>
- [<span data-ttu-id="79cc4-108">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="79cc4-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
