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
ms.openlocfilehash: 76e4082710a6786ec5e743ce606e849637c26512
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Byl zadán neplatný název protokolu událostí
Pro protokol událostí byl zadaný neplatný název. To je obvykle způsobeno neplatných znaků v názvu, prázdný soubor název nebo název souboru, který je příliš dlouhý.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud zadaný název je více než osm znaků, ujistěte se, že nedojde ke konfliktu s názvy jiné protokoly událostí. Při určování, pokud je název jedinečný vyhodnocují pouze prvních 8 znaků.  
  
-   Pokud poskytuje cestu, ujistěte se, že je správně analyzovat.  
  
-   Zkontrolujte, že neexistují žádné neplatné znaky v názvu. Znaky, které nelze použít v názvu souboru obsahovat `<`, `>`, `:`, `"`, `/`, `\`, a `|`.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Analýza cest k souborům](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [Postupy: Přejmenování souboru](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 
