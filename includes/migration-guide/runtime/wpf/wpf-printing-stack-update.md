---
ms.openlocfilehash: 5e2e8d1ec5d698d1c1649c2a0a1b4b77dbdf4022
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621118"
---
### <a name="wpf-printing-stack-update"></a>Aktualizace zásobníku pro tisk WPF

#### <a name="details"></a>Podrobnosti

Rozhraní API pro tisk v GRAFICKÉm rozhraní <xref:System.Printing.PrintQueue?displayProperty=fullName> API pomocí okna pro tisk balíčku. Tato změna se provedla s ohledem na službu. žádný z uživatelů ani vývojářů by neměl zobrazovat žádné změny v chování nebo použití rozhraní API. Při spuštění ve Windows 10 Creators Update je nový tiskový zásobník standardně povolený. Starý tiskový zásobník bude dál fungovat stejně jako dřív ve starších verzích Windows.

#### <a name="suggestion"></a>Návrh

Pokud chcete použít starou sadu Windows 10 Creators Update, nastavte <code>UseXpsOMPrinting</code> REG_DWORD hodnotu <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> klíče registru na <code>1</code> .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4,7|
|Typ|Modul runtime|
