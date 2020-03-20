---
ms.openlocfilehash: fbc39b6e1cc19f6c2846caaabb9a8a721494b4e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67856952"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Povolit kódování Unicode v identifikátorech URI, které se podobají sdíleným položkům UNC

|   |   |
|---|---|
|Podrobnosti|V <xref:System.Uri?displayProperty=fullName>oblasti , vytvoření identifikátoru URI souboru obsahujícího název sdílené složky UNC i znaků Unicode již nebude mít za následek identifikátor URI s neplatným vnitřním stavem. Chování se změní pouze v případě, že jsou splněny všechny následující:<ul><li>Identifikátor URI má <code>file:</code> schéma a následuje čtyři nebo více lomítka.</li><li>Název hostitele začíná podtržítkem nebo jiným nevyhrazeným symbolem.</li><li>Identifikátor URI obsahuje znaky Unicode.</li></ul>|
|Návrh|Aplikace pracující s identifikátory URI, které konzistentně obsahují kódování Unicode, mohly toto chování pravděpodobně použít k nepovolení odkazů na sdílené složky UNC. Tyto aplikace <xref:System.Uri.IsUnc> by měly používat místo.|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|
