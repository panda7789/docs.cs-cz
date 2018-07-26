---
title: Formát schránky není platný.
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: f2a0ab33c1749117d5de4987e85c44602ccd29ce
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245554"
---
# <a name="clipboard-format-is-not-valid"></a>Formát schránky není platný.
Zadaný formát schránky není kompatibilní s metoda se spouští. Mezi možné příčiny této chyby patří:  
  
-   Pomocí do schránky `GetText` nebo `SetText` metodu s formát schránky jiných než `vbCFText` nebo `vbCFLink`.  
  
-   Pomocí do schránky `GetData` nebo `SetData` metodu s formát schránky jiných než `vbCFBitmap`, `vbCFDIB`, nebo `vbCFMetafile`.  
  
-   Pomocí `GetData` nebo `SetData` metody `DataObject` formátu schránky v oblasti vyhrazené Microsoft Windows registrované formáty (& HC000 - & HFFFF), když tento formát schránky není zaregistrován s Microsoft Windows .  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte neplatný formát a zadejte platný.  
  
## <a name="see-also"></a>Viz také  
 [Schránka: Přidání dalších formátů](/cpp/mfc/clipboard-adding-other-formats)
