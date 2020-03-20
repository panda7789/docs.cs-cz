---
ms.openlocfilehash: 22c4b61b293ac2366cae1dc73e0f6805a4a5fb8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857232"
---
### <a name="chained-popups-with-staysopenfalse"></a>Zřetězená vyskakovací okno s pobytyOtevřené= False

|   |   |
|---|---|
|Podrobnosti|Místní okno s staysopen=false má zavřít, když kliknete mimo popup. Když jsou dvě nebo více takových vyskakovacích zařízení zřetězena (tj. jedna obsahuje další), došlo k mnoha problémům, včetně:<ul><li>Otevřete dvě úrovně, klikněte mimo P2, ale uvnitř P1.  Nic se neděje.</li><li>Otevřete dvě úrovně, klepněte mimo P1.  Obě vyskakovací okno blízko.</li><li>Otevřete a zavřete dvě úrovně.  Pak zkuste znovu otevřít P2.  Nic se neděje.</li><li>Pokuste se otevřít tři úrovně.  To nemůžeš.  (Buď se nic nestane, nebo první dvě úrovně blízko, v závislosti na tom, kde kliknete.) Tyto případy (a další varianty) nyní fungují podle očekávání.</li></ul>|
|Rozsah|Edge|
|Version|4.7.1|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
