---
title: "Byl zadán neplatný název protokolu událostí"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fc5a2e93541063a129efaa0ce08fc19a98372126
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Byl zadán neplatný název protokolu událostí
Pro protokol událostí byl zadaný neplatný název. To je obvykle způsobeno neplatných znaků v názvu, prázdný soubor název nebo název souboru, který je příliš dlouhý.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud zadaný název je více než osm znaků, ujistěte se, že nedojde ke konfliktu s názvy jiné protokoly událostí. Při určování, pokud je název jedinečný vyhodnocují pouze prvních 8 znaků.  
  
-   Pokud poskytuje cestu, ujistěte se, že je správně analyzovat.  
  
-   Zkontrolujte, že neexistují žádné neplatné znaky v názvu. Znaky, které nelze použít v názvu souboru obsahovat `<`, `>`, `:`, `"`, `/`, `\`, a `|`.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Analýza cest k souborům](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [Postupy: přejmenování souboru](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [Postupy: vytváření a odebrání vlastní protokoly událostí](http://msdn.microsoft.com/en-us/af9b7da0-80c7-46ac-b7f7-897063ddd503)
