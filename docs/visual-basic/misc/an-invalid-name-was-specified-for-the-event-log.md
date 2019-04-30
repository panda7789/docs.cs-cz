---
title: Byl zadán neplatný název protokolu událostí
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 2b9c934272d0f3392c845dcd2f0062a98dc50c7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940670"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Byl zadán neplatný název protokolu událostí
Pro protokol událostí byl zadán neplatný název. Obvykle to je výsledkem neplatných znaků v názvu, prázdný soubor název nebo název souboru, který je příliš dlouhý.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud se zadaným názvem více než osm znaků, ujistěte se, že nedojde ke konfliktu s názvy jiných protokolů událostí. Pouze prvních osm znaků se vyhodnocují při určování, jestli je název jedinečný.  
  
- Pokud se zadáním cesty, ujistěte se, že je správně parsovat.  
  
- Zkontrolujte, že neexistují žádné neplatné znaky v názvu. Znaky, které nelze použít v názvu souboru patří `<`, `>`, `:`, `"`, `/`, `\`, a `|`.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Analýza cest k souborům](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [Postupy: Přejmenovat soubor](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
