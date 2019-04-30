---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649037"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>Adaptéry WinRT stream už se nejedná volání FlushAsync automaticky při zavření

|   |   |
|---|---|
|Podrobnosti|Adaptéry datového proudu Windows Runtime v aplikacích pro Windows Store, už nebude volat metodu FlushAsync z metody Dispose.|
|Doporučení|Tato změna by měl být průhledná. Vývojářům můžete obnovit předchozí chování napsáním kódu takto:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|Rozsah|Transparentní|
|Version|4.5.1|
|Type|Modul runtime|
