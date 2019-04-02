---
ms.openlocfilehash: 9ad283af76085c228bedceb6db723a1d18b10210
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761027"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Názvy událostí trasování událostí pro Windows nelze odlišit pouze podle přípony "Start" nebo "Stop"

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 a 4.6.1, modul runtime vyvolá <xref:System.ArgumentException> při dva názvy událostí trasování událostí pro Windows (ETW) se liší pouze &quot;Start&quot; nebo &quot;Zastavit&quot; příponu (jako když je jedna událost s názvem <code>LogUser</code>a druhou s názvem <code>LogUserStart</code>). V takovém případě modul runtime nelze vytvořit zdroj události, které nelze generovat žádné protokolování.|
|Doporučení|Aby se zabránilo výjimku, ujistěte se, že žádné názvy dvou událostí se liší pouze &quot;Start&quot; nebo &quot;Zastavit&quot; příponu. Tento požadavek je odebrána od verze rozhraní .NET Framework 4.6.2; modul runtime může rozlišit názvy událostí, které se liší pouze &quot;Start&quot; a &quot;Zastavit&quot; příponu.|
|Rozsah|Edge|
|Version|4.6|
|Type|Změna cílení|

