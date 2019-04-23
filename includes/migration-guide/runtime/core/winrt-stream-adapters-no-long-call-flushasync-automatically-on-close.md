---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803721"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>Adaptéry WinRT stream už se nejedná volání FlushAsync automaticky při zavření

|   |   |
|---|---|
|Podrobnosti|Adaptéry datového proudu Windows Runtime v aplikacích pro Windows Store, už nebude volat metodu FlushAsync z metody Dispose.|
|Doporučení|Tato změna by měl být průhledná. Vývojářům můžete obnovit předchozí chování napsáním kódu takto:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|Rozsah|Transparentní|
|Version|4.5.1|
|Type|Modul runtime|
