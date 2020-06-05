---
title: Chybné číslo záznamu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 44a11d95d33041de9d637684f41cb003dcc36b97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84367539"
---
# <a name="bad-record-number"></a>Chybné číslo záznamu
Číslo záznamu v `a FileGet` příkazu, `FilePut` , `FileGetObject` nebo `FilePutObject` je menší nebo rovno nule.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zkontroluje výpočty použité při generování čísla záznamu. Ověřte pravopis proměnných, které obsahují číslo záznamu nebo které se používají při výpočtu čísel záznamů. Nesprávně napsaný název proměnné se implicitně deklaruje a inicializuje na nulu, pokud se v modulu nepoužíváte `Option Explicit On` .  
  
## <a name="see-also"></a>Viz také

- [Option Explicit – příkaz](../language-reference/statements/option-explicit-statement.md)
