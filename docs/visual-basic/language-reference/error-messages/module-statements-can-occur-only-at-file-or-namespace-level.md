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
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a>&#39;Modul&#39; příkazy lze používat pouze na úrovni souboru nebo oboru názvů
`Module` příkazy musí být v horní části souboru zdroje ihned po `Option` a `Imports` příkazy, globálními atributy a deklarace oboru názvů, ale před všechny ostatní deklarace.  
  
 **ID chyby:** BC30617  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přesunout `Module` příkaz na začátek oboru názvů deklarace nebo zdrojový soubor.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)
