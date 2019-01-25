---
title: Chybné číslo záznamu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: fbf1a2db97d0474fb758ff5ed572e94395a187da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664747"
---
# <a name="bad-record-number"></a>Chybné číslo záznamu
Číslo záznamu v `a FileGet`, `FilePut`, `FileGetObject`, nebo `FilePutObject` příkaz je menší než nebo rovna nule.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte výpočty použitého při generování číslo záznamu. Zkontrolujte pravopis proměnné obsahující číslo záznamu nebo používají při výpočtu čísla záznamů. Chybně napsaná název proměnné implicitně deklarovány a inicializovány na nulu, pokud jste použili `Option Explicit On` v modulu.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Option Explicit](../../visual-basic/language-reference/statements/option-explicit-statement.md)
