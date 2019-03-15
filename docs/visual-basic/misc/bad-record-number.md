---
title: Chybné číslo záznamu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: c71d523406f3ffa420c36125847ab6d35a8f741c
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58037098"
---
# <a name="bad-record-number"></a>Chybné číslo záznamu
Číslo záznamu v `a FileGet`, `FilePut`, `FileGetObject`, nebo `FilePutObject` příkaz je menší než nebo rovna nule.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte výpočty použitého při generování číslo záznamu. Zkontrolujte pravopis proměnné obsahující číslo záznamu nebo používají při výpočtu čísla záznamů. Chybně napsaná název proměnné implicitně deklarovány a inicializovány na nulu, pokud jste použili `Option Explicit On` v modulu.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Option Explicit](../../visual-basic/language-reference/statements/option-explicit-statement.md)
