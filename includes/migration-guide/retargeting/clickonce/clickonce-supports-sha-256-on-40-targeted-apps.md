---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088455"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce podporuje SHA-256 na 4.0 cílové aplikace

|   |   |
|---|---|
|Podrobnosti|Dříve by aplikace ClickOnce s certifikátem podepsané pomocí algoritmu SHA-256 vyžaduje rozhraní .NET Framework 4.5 nebo novější bude k dispozici, i v případě, že aplikace cílené 4.0. Nyní aplikace ClickOnce cílové rozhraní .NET Framework 4.0 lze spustit v rozhraní .NET Framework 4.0, i v případě, že podepsané pomocí algoritmu SHA-256.|
|Doporučení|Tato změna odebere dané závislosti a umožňuje certifikáty SHA-256 k podepisování aplikací ClickOnce, určených pro rozhraní .NET Framework 4 a dřívějších verzích.|
|Rozsah|Vedlejší|
|Version|4.6|
|Type|Změna cílení|
