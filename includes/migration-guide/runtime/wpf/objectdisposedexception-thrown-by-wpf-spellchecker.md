---
ms.openlocfilehash: b836b26f3f52e9d0cc78feb764629bd2fa306657
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621785"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException vyvolaná nástrojem pro kontrolu pravopisu WPF

#### <a name="details"></a>Podrobnosti

V aplikacích WPF občas dochází k chybě při vypínání aplikace s <xref:System.ObjectDisposedException?displayProperty=fullName> vyvolaným nástrojem pro kontrolu pravopisu. Tato akce je opravena v .NET Framework 4,7 WPF tím, že zpracovává výjimku řádným způsobem, a zajišťuje tak, že aplikace již nebudou negativně ovlivněny. Je nutné poznamenat, že příležitostné výjimky s první pravděpodobností budou v aplikacích spuštěných v rámci ladicího programu nadále zachovány.

#### <a name="suggestion"></a>Návrh

Upgradovat na .NET Framework 4,7

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.6.1|
|Typ|Modul runtime|
