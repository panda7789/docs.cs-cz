---
ms.openlocfilehash: c967a5b09b5e9ffeee7bff046f0c96469bc7fb02
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615634"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce podporuje SHA-256 na 4,0 cílené aplikace

#### <a name="details"></a>Podrobnosti

Dříve aplikace ClickOnce s certifikátem podepsaným SHA-256 by vyžadovala, aby byla k dispozici .NET Framework 4,5 nebo novější, i když aplikace cílí na 4,0. Nyní .NET Framework 4,0 cílené aplikace ClickOnce mohou běžet na .NET Framework 4,0 i v případě, že jsou podepsány pomocí algoritmu SHA-256.

#### <a name="suggestion"></a>Návrh

Tato změna odstraní tuto závislost a povolí použití certifikátů SHA-256 k podepisování aplikací ClickOnce, které cílí na .NET Framework 4 a starší verze.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6         |
| Typ    | Změna cílení |
