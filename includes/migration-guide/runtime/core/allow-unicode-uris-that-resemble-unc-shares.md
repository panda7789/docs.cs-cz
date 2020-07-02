---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621064"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Povoluje kódování Unicode v identifikátorech URI, které se podobají sdíleným složkám UNC

#### <a name="details"></a>Podrobnosti

V systému se <xref:System.Uri?displayProperty=fullName> konstrukce identifikátoru URI souboru, který obsahuje název sdílené složky UNC a znakům Unicode, již nevede k identifikátoru URI s neplatným vnitřním stavem. Chování se změní jenom v případě, že jsou splněné všechny následující podmínky:<ul><li>Identifikátor URI má schéma <code>file:</code> a je následován čtyřmi nebo více lomítky.</li><li>Název hostitele začíná podtržítkem nebo jiným nerezervovaným symbolem.</li><li>Identifikátor URI obsahuje znaky Unicode.</li></ul>

#### <a name="suggestion"></a>Návrh

Aplikace pracující se stejnými identifikátory URI, které obsahují Unicode, by mohly mít k dispozici toto chování k zakázání odkazů na sdílené složky UNC. Tyto aplikace by se měly používat <xref:System.Uri.IsUnc> místo toho.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.7.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
