---
ms.openlocfilehash: 6fafb689af5d50b31b19f5d1fe7090a6c256ca45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236210"
---
### <a name="wpf-printing-stack-update"></a>Aktualizace zásobníku tisk WPF

|   |   |
|---|---|
|Podrobnosti|Pomocí rozhraní API pro tisk na WPF <xref:System.Printing.PrintQueue?displayProperty=name> nyní volat okna Tisk dokumentu balíčku API ve prospěch teď zastaralé rozhraní API tisk XPS. Změny s použitelnost v úvahu; uživatelé ani vývojáři měli vidět všechny změny v chování nebo použití rozhraní API. Nový zásobník tisk je standardně povolená, když běží v systému Windows 10 Creators Update. Staré zásobníku tisku bude nadále fungovat stejně jako v minulosti ve starších verzích Windows.|
|Doporučení|Chcete-li použít staré zásobníku ve Windows 10 Creators Update, nastavte <code>UseXpsOMPrinting</code> hodnota REG_DWORD <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klíč registru, který <code>1</code>.|
|Rozsah|Edge|
|Version|4.7|
|Type|Modul runtime|
