---
ms.openlocfilehash: 2bb40294685c987de84138ee889e6b88f7184bb0
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857232"
---
### <a name="chained-popups-with-staysopenfalse"></a>Zřetězené automaticky otevíraná okna s nastavením StaysOpen = False

|   |   |
|---|---|
|Podrobnosti|Automaticky otevíraného okna s nastavením StaysOpen = False by měl po kliknutí na mimo automaticky otevírané okno zavřít. Když jsou zřetězeny dva nebo více těchto automaticky otevíraná okna (to znamená jeden obsahuje další), došlo k mnoha problémům, včetně:<ul><li>Spusťte dvě úrovně, klikněte na mimo P2, ale uvnitř P1.  Nic se nestane.</li><li>Spusťte dvě úrovně, klikněte na vnější P1.  Zavřete obě automaticky otevíraná okna.</li><li>Otevření a zavření dvě úrovně.  Zkuste znovu otevřít P2.  Nic se nestane.</li><li>Došlo k pokusu o otevření tři úrovně.  Nemůžete.  (Nic se nestane nebo zavřete první dvě úrovně, v závislosti na tom, kde klikněte na.) Tyto případy (a další varianty) nyní fungovat podle očekávání.</li></ul>|
|Scope|Edge|
|Version|4.7.1|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|

