---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614517"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a>Resgen odmítá načíst obsah z webu.

#### <a name="details"></a>Podrobnosti

soubory RESX mohou obsahovat binární formátovaný vstup. Pokud se pokusíte použít Resgen k načtení souboru staženého z nedůvěryhodného umístění, ve výchozím nastavení se nepodaří načíst vstup.

#### <a name="suggestion"></a>Návrh

Uživatelé Resgen, kteří vyžadují načítání binárního formátovaného vstupu z nedůvěryhodných umístění, mohou buď odebrat značku webu ze vstupního souboru, nebo použít Quirk pro odhlášení. Přidejte následující nastavení registru, aby bylo možné použít Quirk pro místní počítač: [HKEY_LOCAL_MACHINE \software\microsoft.netframework\sdk] &quot; AllowProcessOfUntrustedResourceFiles &quot; = &quot; true&quot;

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.2       |
| Typ    | Změna cílení |
