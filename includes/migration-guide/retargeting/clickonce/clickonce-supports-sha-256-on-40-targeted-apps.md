---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804422"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce podporuje SHA-256 na 4.0-cílené aplikace

|   |   |
|---|---|
|Podrobnosti|Dříve clickonce aplikace s certifikátem podepsaným SHA-256 by vyžadovala .NET Framework 4.5 nebo novější, i když aplikace cílené 4.0. Aplikace ClickOnce cílené na rozhraní .NET Framework 4.0 lze nyní spouštět v rozhraní .NET Framework 4.0, i když jsou podepsány sha-256.|
|Návrh|Tato změna odebere tuto závislost a povolí certifikáty SHA-256, které mají být použity k podpisu ClickOnce aplikace, které cílí na rozhraní .NET Framework 4 a starší verze.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna cílení|
