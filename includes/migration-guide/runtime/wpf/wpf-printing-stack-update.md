---
ms.openlocfilehash: 6fafb689af5d50b31b19f5d1fe7090a6c256ca45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802460"
---
### <a name="wpf-printing-stack-update"></a>Aktualizace zásobníku tisku WPF

|   |   |
|---|---|
|Podrobnosti|WPF je tisková rozhraní <xref:System.Printing.PrintQueue?displayProperty=name> API pomocí nyní volání okna rozhraní API balíčku tiskových dokumentů ve prospěch nyní zastaralé XPS Print API. Změna byla provedena s ohledem na použitelnost; uživatelé ani vývojáři by měli vidět žádné změny v chování nebo využití rozhraní API. Nový tiskový zásobník je ve výchozím nastavení povolen při spuštění v aktualizaci Windows 10 Creators Update. Starý tiskový zásobník bude i nadále fungovat stejně jako dříve ve starších verzích systému Windows.|
|Návrh|Chcete-li použít starý zásobník v aktualizaci <code>UseXpsOMPrinting</code> Windows 10 <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> Creators <code>1</code>Update, nastavte REG_DWORD hodnotu klíče registru na .|
|Rozsah|Edge|
|Version|4.7|
|Typ|Modul runtime|
