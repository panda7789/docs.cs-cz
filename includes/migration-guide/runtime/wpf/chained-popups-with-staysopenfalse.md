---
ms.openlocfilehash: 22c4b61b293ac2366cae1dc73e0f6805a4a5fb8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236202"
---
### <a name="chained-popups-with-staysopenfalse"></a>Zřetězené automaticky otevíraná okna s nastavením StaysOpen = False

|   |   |
|---|---|
|Podrobnosti|Automaticky otevíraného okna s nastavením StaysOpen = False by měl po kliknutí na mimo automaticky otevírané okno zavřít. Když jsou zřetězeny dva nebo více těchto automaticky otevíraná okna (to znamená jeden obsahuje další), došlo k mnoha problémům, včetně:<ul><li>Spusťte dvě úrovně, klikněte na mimo P2, ale uvnitř P1.  Nic se nestane.</li><li>Spusťte dvě úrovně, klikněte na vnější P1.  Zavřete obě automaticky otevíraná okna.</li><li>Otevření a zavření dvě úrovně.  Zkuste znovu otevřít P2.  Nic se nestane.</li><li>Došlo k pokusu o otevření tři úrovně.  Nemůžete.  (Nic se nestane nebo zavřete první dvě úrovně, v závislosti na tom, kde klikněte na.) Tyto případy (a další varianty) nyní fungovat podle očekávání.</li></ul>|
|Rozsah|Edge|
|Version|4.7.1|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
