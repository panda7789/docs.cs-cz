---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235313"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>Nyní je dodržena MinFreeMemoryPercentageToActiveService

|   |   |
|---|---|
|Podrobnosti|Toto nastavení vytváří minimální velikost paměti, které musí být k dispozici na serveru, před aktivací služby WCF. Slouží k zabránění <xref:System.OutOfMemoryException?displayProperty=name> výjimky. Toto nastavení v rozhraní .NET Framework 4.5, nemělo žádný vliv. V rozhraní .NET Framework 4.5.1 nezaznamenáme nastavení.|
|Doporučení|Pokud volné paměti dostupné na webovém serveru je nižší než procento definované v nastavení konfigurace, dojde k výjimce. Některé služby WCF, které úspěšně spuštěny a byl spuštěn v prostředí omezené paměti teď může selhat.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Type|Modul runtime|
