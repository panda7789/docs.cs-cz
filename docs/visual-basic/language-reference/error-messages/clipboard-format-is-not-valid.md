---
title: Formát schránky není platný.
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 0a5d06b381df3af8de1d092b600239c9acfce39a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735776"
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
