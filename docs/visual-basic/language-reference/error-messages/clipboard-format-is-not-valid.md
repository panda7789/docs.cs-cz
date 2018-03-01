---
title: "Formát schránky není platný."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
