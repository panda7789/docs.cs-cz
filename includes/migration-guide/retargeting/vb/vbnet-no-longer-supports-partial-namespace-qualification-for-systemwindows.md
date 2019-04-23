---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982121"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET už nepodporuje kvalifikace částečné obor názvů System.Windows rozhraní API

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5.2, VB.NET projekty nelze zadat System.Windows rozhraní API s částečně kvalifikované obory názvů. Například odkazující na <code>Windows.Forms.DialogResult</code> se nezdaří. Místo toho kód musí odkazovat na plně kvalifikovaný název (<xref:System.Windows.Forms.DialogResult>) nebo importovat konkrétní obor názvů a odkazovat pouze na <xref:System.Windows.Forms.DialogResult?displayProperty=name>.|
|Doporučení|Kód by měl aktualizovat o <code>System.Windows</code> rozhraní API pomocí jednoduchých názvy (a import oboru názvů relevantní) nebo s plně kvalifikované názvy.|
|Rozsah|Vedlejší|
|Version|4.5.2|
|Type|Změna cílení|
