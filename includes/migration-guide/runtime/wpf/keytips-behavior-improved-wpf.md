---
ms.openlocfilehash: 9659068304eb208fd6a0a753273453bc669fbc56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621115"
---
### <a name="keytips-behavior-improved-in-wpf"></a>Vylepšení chování tipů v WPF

#### <a name="details"></a>Podrobnosti

Chování tipů kláves bylo upraveno tak, aby se v aplikacích Microsoft Word a Windows Explorer nastavila parita s chováním. Tím, že zkontrolujete, jestli je stav KeyTip povolený nebo ne v případě, že se <xref:System.Windows.Input.KeyEventArgs.SystemKey> stiskne (konkrétně <xref:System.Windows.Input.Key> nebo <xref:System.Windows.Input.Key.F11> ) stisknutí, WPF zpracuje KeyTip klíče správně. Pomocí klávesových tipů nyní můžete zavřít nabídku i v případě, že ji otevřete myší.

#### <a name="suggestion"></a>Návrh

–

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.7.2|
|Typ|Modul runtime|
