---
title: Formát schránky není platný.
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: eef16096b269902dbaca6a344abf4c5f6a504fb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586218"
---
# <a name="clipboard-format-is-not-valid"></a>Formát schránky není platný.
Zadaný formát schránky není kompatibilní s metodu spouštěna. Mezi možné příčiny této chyby patří:  
  
-   Pomocí do schránky `GetText` nebo `SetText` metoda s formát schránky jinak než `vbCFText` nebo `vbCFLink`.  
  
-   Pomocí do schránky `GetData` nebo `SetData` metoda s formát schránky jinak než `vbCFBitmap`, `vbCFDIB`, nebo `vbCFMetafile`.  
  
-   Pomocí `DataObject``GetData` metoda nebo `SetData` metoda s formát schránky v rozsahu vyhrazený systémem Microsoft Windows pro registrované formátů (& HC000 & HFFFF), když tento formát schránky nebyl zaregistrován v systému Windows.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte neplatný formát a zadejte platný.  
  
## <a name="see-also"></a>Viz také  
 [Schránka: Přidání dalších formátů](/cpp/mfc/clipboard-adding-other-formats)
