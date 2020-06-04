---
title: Pro protokol událostí byl zadán neplatný název.
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 70b1de2a3776a9c68260cc431b65e754d7247a0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412920"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Pro protokol událostí byl zadán neplatný název.
Pro protokol událostí byl zadán neplatný název. Obvykle se jedná o výsledek neplatných znaků v názvu, prázdný název souboru nebo název souboru, který je příliš dlouhý.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud je zadaný název delší než osm znaků, ujistěte se, že nedochází ke konfliktu s názvy jiných protokolů událostí. Při určování, jestli je název jedinečný, se vyhodnotí jenom prvních osm znaků.  
  
- Pokud zadáváte cestu, ujistěte se, že je správně analyzovaná.  
  
- Ověřte, zda název neobsahuje neplatné znaky. Mezi znaky, které nelze použít v názvu souboru `<` , patří, `>` , `:` , `"` ,, a `/` `\` `|` .  
  
## <a name="see-also"></a>Viz také

- [Postupy: Analýza cest k souborům](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [Postupy: Přejmenování souboru](../developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
