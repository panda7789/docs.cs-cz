---
title: Příznaky funkcí
description: Implementace příznaků funkcí v cloudových nativních aplikacích s využitím konfigurace aplikací Azure
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 607bd14a415a25b382f550e697542cf749a21772
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614068"
---
# <a name="feature-flags"></a>Příznaky funkcí

V kapitole 1 jsme tvrdili, že nativní Cloud je mnohem o rychlosti a flexibilitě. Uživatelé očekávají rychlou odezvu, inovativní funkce a nulové výpadky. `Feature flags`jsou moderní techniky nasazení, které pomáhají zvýšit flexibilitu pro aplikace nativní pro Cloud. Umožňují nasazovat nové funkce do produkčního prostředí, ale omezují jejich dostupnost. Pomocí rychlého pohybu přepínače můžete aktivovat novou funkci pro konkrétní uživatele bez restartování aplikace nebo nasazení nového kódu. Oddělují vydání nových funkcí od jejich nasazení kódu.

Příznaky funkcí jsou postavené na podmíněné logice, které ovládají viditelnost funkcí pro uživatele za běhu. V moderních cloudových nativních systémech je běžné nasadit nové funkce do produkčního prostředí, ale testovat je s omezeným cílovou skupinou. Jak se zvyšuje spolehlivost, funkce se dá přírůstkově vymezit širším cílovým skupinám.

K dalším případům použití pro příznaky funkcí patří:

- Omezte prémiové funkce na konkrétní skupiny zákazníků ochotné uhradit vyšší poplatky za předplatné.
- Umožňuje stabilizovat systém tím, že se rychle deaktivuje funkce problému, což vyloučí rizika vrácení zpět nebo okamžité opravy hotfix.
- Zakážete volitelnou funkci s vysokou spotřebou prostředků během období špičky využití.
- Pro účely `experimental feature releases` ověření možnosti proveditelnost a oblíbenosti můžete provádět malé uživatelské segmenty.

Příznaky funkcí také povýší `trunk-based` vývoj. Jedná se o model větvení správy zdrojového kódu, ve kterém vývojáři spolupracují na funkcích v jedné větvi. Tento přístup minimalizuje riziko a složitost slučování velkého počtu dlouhotrvajících větví funkcí. Funkce nejsou k dispozici, dokud nejsou aktivovány.

## <a name="implementing-feature-flags"></a>Implementace příznaků funkcí

Ve svém jádru je příznak funkce odkazem na jednoduchý `decision object` . Vrátí logický stav `on` nebo `off` . Příznak obvykle zabalí blok kódu, který zapouzdřuje schopnost funkce. Stav příznaku určuje, zda se pro daného uživatele spustí blok kódu. Obrázek 10-11 ukazuje implementaci.

```c#
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

**Obrázek 10-11** – implementace příznaku jednoduché funkce

Všimněte si, jak tento přístup odděluje rozhodovací logiku od kódu funkce.

V kapitole 1 jsme probrali `Twelve-Factor App` . Návod doporučuje zachovat nastavení konfigurace externě ze spustitelného kódu aplikace. V případě potřeby je možné číst nastavení z externího zdroje. Hodnoty konfigurace příznaku funkce by měly být také nezávislé na základu kódu. Konfigurací příznaku přenesení v samostatném úložišti můžete změnit stav příznaku bez změny a nasazení aplikace.

[Azure App Configuration](https://docs.microsoft.com/azure/azure-app-configuration/overview) poskytuje centralizované úložiště pro příznaky funkcí. Pomocí této funkce můžete definovat různé druhy příznaků funkcí a rychle a bez obav manipulovat se svými stavy. Přidáním klientských knihoven konfigurace aplikace do aplikace povolíte funkci příznaku funkcí. Podporovány jsou různé programovací jazykové prostředí.

Příznaky funkcí lze snadno implementovat ve [službě ASP.NET Core](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core). Když nainstalujete knihovny pro správu funkcí .NET a poskytovatele konfigurace aplikace, umožníte deklarativní Přidání příznaků funkcí do kódu. Povolují `FeatureGate` atributy, takže nemusíte vytvářet příkazy if v rámci vašeho základu kódu ručně.

Po nakonfigurování ve vaší spouštěcí třídě můžete přidat funkce příznaků funkcí na úrovni kontroleru, akce nebo middleware. Obrázek 10-12 představuje implementaci kontroléru a akce:

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public class ProductController : Controller
{
    ...
}
```

```c#
[FeatureGate(MyFeatureFlags.FeatureA)]
public IActionResult UpdateProductStatus()
{
    return ObjectResult(ProductDto);
}
```

**Obrázek 10-12** – implementace příznaků funkcí v kontroleru a akci.

Pokud je příznak funkce zakázán, bude uživatel dostávat stavový kód 404 (Nenalezeno) bez těla odpovědi.

Příznaky funkcí lze také vložit přímo do tříd jazyka C#. Obrázek 10-13 ukazuje vkládání příznaků funkcí:

```c#
public class ProductController : Controller
{
    private readonly IFeatureManager _featureManager;

    public ProductController(IFeatureManager featureManager)
    {
        _featureManager = featureManager;
    }
}
```

**Obrázek 10-13** – příznak funkce pro vkládání do třídy.

Knihovny správy funkcí spravují životní cyklus příznaků funkcí na pozadí. Například pro minimalizaci vysokého počtu volání do úložiště konfigurace jsou po určitou dobu v mezipaměti knihoven označeny stavy. Můžou zaručit neměnnosti stavů příznaků během volání žádosti. Nabízejí také `Point-in-time snapshot` . Historii jakékoli hodnoty klíč-hodnota můžete kdykoli znovu sestavit a zadat její dřívější hodnotu během posledních sedmi dnů.

>[!div class="step-by-step"]
>[Předchozí](devops.md) 
> [Další](infrastructure-as-code.md)
