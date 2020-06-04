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
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a>Příkazy 'Module' lze používat pouze na úrovni souboru nebo oboru názvů.
`Module`příkazy se musí nacházet v horní části zdrojového souboru hned po `Option` a `Imports` příkazy, globální atributy a deklarace oboru názvů, ale před všemi ostatními deklaracemi.  
  
 **ID chyby:** BC30617  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přesuňte `Module` příkaz na začátek deklarace oboru názvů nebo zdrojového souboru.  
  
## <a name="see-also"></a>Viz také

- [Module – příkaz](../statements/module-statement.md)
