---
ms.openlocfilehash: 418bcdca1e9a325894891d7b0e080ce035e2d1b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614460"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>Vylepšení přístupnosti ASP.NET v .NET Framework 4.7.1

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.7.1, ASP.NET zlepšila, jak webové ovládací prvky ASP.NET pracují s technologiemi usnadnění v aplikaci Visual Studio, aby lépe podporovaly ASP.NET zákazníky.  Mezi ně patří tyto změny:

- Změny pro implementaci chybějících vzorů přístupnosti uživatelského rozhraní v ovládacích prvcích, jako je dialogové okno Přidat pole v průvodci zobrazení podrobností nebo dialogové okno Konfigurovat ListView Průvodce ListView.
- Změny pro zlepšení zobrazení v režimu Vysoký kontrast, jako je například editor polí datového pageru.
- Změny pro zlepšení prostředí navigace klávesnicí pro ovládací prvky, jako je dialogové okno pole v průvodci úpravou polí stránkování ovládacího prvku DataPager, dialogové okno Konfigurovat ObjectContext nebo dialogové okno Konfigurovat výběr dat v Průvodci konfigurací zdroje dat.

#### <a name="suggestion"></a>Návrh

**Jak vyjádřit nebo odhlásit tyto změny** Aby mohl Návrhář sady Visual Studio těžit z těchto změn, musí běžet na .NET Framework 4.7.1 nebo novějším. Webová aplikace může tyto změny využít v jednom z následujících způsobů:

- Nainstalujte Visual Studio 2017 15,3 nebo novější, které ve výchozím nastavení podporují nové funkce usnadnění s následujícím přepínačem AppContext.
- Odsouhlasení se starším chováním funkce usnadnění přidáním `Switch.UseLegacyAccessibilityFeatures` přepínače AppContext do `<runtime>` oddílu v souboru devenv.exe.config a jeho nastavením na `false` , jak ukazuje následující příklad.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
<runtime>
...
<!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
...
</runtime>
</configuration>
```

Aplikace, které cílí na .NET Framework 4.7.1 nebo novější a chtějí zachovat starší funkce usnadnění, se můžou přihlásit k používání starších funkcí pro usnadnění přístupu tím, že explicitně nastaví tento přepínač AppContext na `true` .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.7.1       |
| Typ    | Změna cílení |
