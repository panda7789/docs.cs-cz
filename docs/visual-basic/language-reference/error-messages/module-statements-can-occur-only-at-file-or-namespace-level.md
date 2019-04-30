---
title: Příkazy 'Module' lze používat pouze na úrovni souboru nebo oboru názvů.
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: bf0239422fb5a98e4670aea407f684753d3a7ea4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920858"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a>Příkazy 'Module' lze používat pouze na úrovni souboru nebo oboru názvů.
`Module` příkazy musí být uvedena v horní části zdrojového souboru ihned po `Option` a `Imports` příkazy, globální atributy a deklarace oboru názvů, ale před ostatními deklaracemi.  
  
 **ID chyby:** BC30617  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přesunout `Module` příkaz do horní části obor názvů deklarace nebo zdrojový soubor.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)
