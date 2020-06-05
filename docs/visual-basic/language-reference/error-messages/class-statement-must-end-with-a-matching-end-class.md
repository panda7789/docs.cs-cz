---
title: Příkaz 'Class' musí být ukončen odpovídajícím příkazem 'End Class'.
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 01c231f577d21028e9ef92f37c7ac5f7f1fe2aa3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415385"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a>Příkaz 'Class' musí být ukončen odpovídajícím příkazem 'End Class'.
`Class`slouží k inicializaci bloku, `Class` takže se může vyskytovat pouze na začátku bloku s párovým příkazem, který `End Class` ukončuje blok. Buď máte redundantní `Class` příkaz, nebo jste svůj blok neukončili `Class` pomocí `End Class` .  
  
 **ID chyby:** BC30481  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Vyhledejte a odeberte nepotřebný `Class` příkaz.  
  
- `Class`Uzavřete blok se spárováním `End Class` .  
  
## <a name="see-also"></a>Viz také

- [\<keyword>Příkaz end](../statements/end-keyword-statement.md)
- [Class – příkaz](../statements/class-statement.md)
