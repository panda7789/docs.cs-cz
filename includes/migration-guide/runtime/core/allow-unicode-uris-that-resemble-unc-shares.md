---
ms.openlocfilehash: fbc39b6e1cc19f6c2846caaabb9a8a721494b4e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236120"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Povolit kódování Unicode v identifikátory URI, které se podobají UNC sdílené složky

|   |   |
|---|---|
|Podrobnosti|V <xref:System.Uri?displayProperty=fullName>sestavením souboru identifikátory URI obsahující oba UNC název sdílené složky a znaky znakové sady Unicode již nebude v identifikátoru URI se neplatný vnitřní stav. Chování se změní, pouze pokud všechny tyto jsou splněny:<ul><li>Identifikátor URI obsahuje schéma <code>file:</code> a je následována čtyři nebo více lomítek.</li><li>Název hostitele začíná podtržítkem nebo jiný nerezervované symbol.</li><li>Identifikátor URI obsahuje znaky kódování Unicode.</li></ul>|
|Doporučení|Aplikace pracující s identifikátory URI obsahující konzistentně Unicode mohli případně použít toto chování Pokud chcete zakázat odkazy na sdílené složky UNC. Tyto aplikace by měly používat <xref:System.Uri.IsUnc> místo.|
|Rozsah|Edge|
|Version|4.7.2|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|
