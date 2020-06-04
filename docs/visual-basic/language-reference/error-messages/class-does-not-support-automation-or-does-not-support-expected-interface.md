---
title: Třída nepodporuje automatizaci nebo nepodporuje očekávané rozhraní.
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: 856c3f5ef503a7e5919e9e602532c56d9557482f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415398"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a>Třída nepodporuje automatizaci nebo nepodporuje očekávané rozhraní.
Buď třída, kterou jste zadali ve `GetObject` `CreateObject` volání funkce, nebyla vystavena rozhraní programovatelnosti nebo jste změnili projekt z. dll na. exe, nebo naopak.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Podívejte se na dokumentaci aplikace, která vytvořila objekt pro omezení použití automatizace s touto třídou objektu.  
  
2. Pokud jste změnili projekt z. dll na. exe nebo naopak, je nutné ručně zrušit registraci starého souboru. dll nebo. exe.  
  
## <a name="see-also"></a>Viz také

- [Typy chyb](../../programming-guide/language-features/error-types.md)
- [Kontaktujte nás](/visualstudio/ide/feedback-options)
