---
ms.openlocfilehash: fbc39b6e1cc19f6c2846caaabb9a8a721494b4e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803716"
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
