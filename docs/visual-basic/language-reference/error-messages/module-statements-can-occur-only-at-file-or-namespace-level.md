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
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a>&#39;Modul&#39; příkazy lze používat pouze na úrovni souboru nebo oboru názvů
`Module` příkazy musí být uvedena v horní části zdrojového souboru ihned po `Option` a `Imports` příkazy, globální atributy a deklarace oboru názvů, ale před ostatními deklaracemi.  
  
 **ID chyby:** BC30617  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přesunout `Module` příkaz do horní části obor názvů deklarace nebo zdrojový soubor.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)
