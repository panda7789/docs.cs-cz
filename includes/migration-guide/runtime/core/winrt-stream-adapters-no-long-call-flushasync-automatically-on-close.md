---
ms.openlocfilehash: 60937459b6f18e9abae87ad2dc97c3942325eedc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619996"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>Adaptéry WinRT streamu bez dlouhého volání FlushAsync automaticky při zavření

#### <a name="details"></a>Podrobnosti

V aplikacích pro Windows Store prostředí Windows Runtime adaptéry streamování již nevolají metodu FlushAsync z metody Dispose.

#### <a name="suggestion"></a>Návrh

Tato změna by měla být transparentní. Vývojáři mohou obnovit předchozí chování tak, že napíše kód takto:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Průhlednost|
|Verze|4.5.1|
|Typ|Modul runtime|
