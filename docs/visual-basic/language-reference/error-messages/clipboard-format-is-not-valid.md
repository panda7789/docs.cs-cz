---
title: Formát schránky není platný.
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 5ec077be30b0afc8917d431dc9bd73c8dd41be89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817172"
---
# <a name="clipboard-format-is-not-valid"></a>Formát schránky není platný.
Zadaný formát schránky není kompatibilní s metoda se spouští. Mezi možné příčiny této chyby patří:  
  
-   Pomocí do schránky `GetText` nebo `SetText` metodu s formát schránky jiných než `vbCFText` nebo `vbCFLink`.  
  
-   Pomocí do schránky `GetData` nebo `SetData` metodu s formát schránky jiných než `vbCFBitmap`, `vbCFDIB`, nebo `vbCFMetafile`.  
  
-   Pomocí `GetData` nebo `SetData` metody `DataObject` formátu schránky v oblasti vyhrazené Microsoft Windows registrované formáty (& HC000 - & HFFFF), když tento formát schránky není zaregistrován s Microsoft Windows .  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte neplatný formát a zadejte platný.  
  
## <a name="see-also"></a>Viz také:

- [Schránka: Přidání dalších formátů](/cpp/mfc/clipboard-adding-other-formats)
