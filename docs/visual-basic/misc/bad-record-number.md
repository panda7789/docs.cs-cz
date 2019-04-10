---
title: Chybné číslo záznamu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: abd0a1467c0991a40b93e74a1d7a7889367fb8ca
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59340799"
---
# <a name="bad-record-number"></a>Chybné číslo záznamu
Číslo záznamu v `a FileGet`, `FilePut`, `FileGetObject`, nebo `FilePutObject` příkaz je menší než nebo rovna nule.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zkontrolujte výpočty použitého při generování číslo záznamu. Zkontrolujte pravopis proměnné obsahující číslo záznamu nebo používají při výpočtu čísla záznamů. Chybně napsaná název proměnné implicitně deklarovány a inicializovány na nulu, pokud jste použili `Option Explicit On` v modulu.  
  
## <a name="see-also"></a>Viz také:

- [Option Explicit – příkaz](../../visual-basic/language-reference/statements/option-explicit-statement.md)
