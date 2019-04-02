---
ms.openlocfilehash: e613f0c52c77efebf250f5935d5cbfc29bc09a6b
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760423"
---
### <a name="wpf-printing-stack-update"></a>Aktualizace zásobníku tisk WPF

|   |   |
|---|---|
|Podrobnosti|Pomocí rozhraní API pro tisk na WPF <xref:System.Printing.PrintQueue?displayProperty=name> nyní volat okna Tisk dokumentu balíčku API ve prospěch teď zastaralé rozhraní API tisk XPS. Změny s použitelnost v úvahu; uživatelé ani vývojáři měli vidět všechny změny v chování nebo použití rozhraní API. Nový zásobník tisk je standardně povolená, když běží v systému Windows 10 Creators Update. Staré zásobníku tisku bude nadále fungovat stejně jako v minulosti ve starších verzích Windows.|
|Doporučení|Chcete-li použít staré zásobníku ve Windows 10 Creators Update, nastavte <code>UseXpsOMPrinting</code> hodnota REG_DWORD <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klíč registru, který <code>1</code>.|
|Rozsah|Edge|
|Version|4.7|
|Type|Modul runtime|

