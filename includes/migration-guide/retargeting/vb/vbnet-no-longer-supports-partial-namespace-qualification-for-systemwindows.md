---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804633"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET již nepodporuje částečnou kvalifikaci oboru názvů pro systémová api systému.Windows

|   |   |
|---|---|
|Podrobnosti|Počínaje rozhraním .NET Framework 4.5.2 nelze VB.NET projektů určit rozhraní API systému System.Windows s částečně kvalifikovanými obory názvů. Například odkazování <code>Windows.Forms.DialogResult</code> na se nezdaří. Místo toho musí kód odkazovat<xref:System.Windows.Forms.DialogResult>na plně kvalifikovaný název ( ) <xref:System.Windows.Forms.DialogResult?displayProperty=name>nebo importovat konkrétní obor názvů a odkazovat jednoduše na .|
|Návrh|Kód by měl být <code>System.Windows</code> aktualizován tak, aby odkazoval na api s jednoduchými názvy (a importem příslušného oboru názvů) nebo s plně kvalifikovanými názvy.|
|Rozsah|Vedlejší|
|Version|4.5.2|
|Typ|Změna cílení|
