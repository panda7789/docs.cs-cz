---
title: Algoritmus načítání satelitních sestavení – .NET Core
description: Popis podrobností algoritmu satelitního načítání sestavení v .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105313"
---
# <a name="satellite-assembly-loading-algorithm"></a>Algoritmus načítání satelitních sestavení

Satelitní sestavení se používají k ukládání lokalizovaných prostředků přizpůsobených pro jazyk a jazykovou verzi.

Satelitní sestavení používají jiný algoritmus načítání než obecná spravovaná sestavení.

## <a name="when-are-satellite-assemblies-loaded"></a>Kdy jsou satelitní sestavení načtena?

Satelitní sestavení jsou načtena při načítání lokalizovaného prostředku.

Základní rozhraní API pro načtení lokalizovaných prostředků je <xref:System.Resources.ResourceManager?displayProperty=fullName> třída. Nakonec třída zavolá metodu pro každý z nich <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>. <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> <xref:System.Resources.ResourceManager>

Rozhraní API vyšší úrovně můžou mít abstraktní rozhraní API nízké úrovně.

## <a name="algorithm"></a>Algoritmus

Záložní proces prostředku .NET Core zahrnuje následující kroky:

1. `active` Určete<xref:System.Runtime.Loader.AssemblyLoadContext> instanci. Ve všech případech `active` je instancí spouštěným <xref:System.Runtime.Loader.AssemblyLoadContext>sestavením.

2. `active` Instance se pokusí načíst satelitní sestavení pro požadovanou jazykovou verzi v pořadí podle priority podle:
    - Kontroluje se její mezipaměť.
    - Kontrola adresáře aktuálně spuštěného sestavení pro podadresář, který odpovídá požadovanému <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (například `es-MX`).

        > [!NOTE]
        > Tato funkce nebyla implementována v .NET Core před 3,0.
        >
        > [!NOTE]
        > V případě systému Linux a macOS se v podadresářích rozlišují malá a velká písmena a musí být buď:
        > - Přesně rozlišovat velká a malá písmena.
        > - V malých malých písmenech.

    - `active` Pokud<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> je instance, spusťte výchozí logiku pro [zjišťování sestavení (prostředků)](default-probing.md#satellite-resource-assembly-probing) .

    - <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> Volání funkce.

    - Vyvolává se <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> událost.

    - Vyvolává se <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost.

3. Pokud je načteno satelitní sestavení:
   - <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> Událost je vyvolána.
   - Sestavení je vyhledalo pro požadovaný prostředek. Pokud modul runtime nalezne prostředek v sestavení, použije ho. Pokud prostředek nenajde, pokračuje v hledání.

    > [!NOTE]
    > Chcete-li najít prostředek v rámci satelitního sestavení, modul runtime vyhledá soubor prostředků požadovaný <xref:System.Resources.ResourceManager> pro aktuální. <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> V rámci souboru prostředků vyhledá požadovaný název prostředku. Pokud buď není nalezen, bude prostředek považován za nenalezený.

4. Modul runtime Next prohledává sestavení nadřazené jazykové verze prostřednictvím mnoha potenciálních úrovní, pokaždé při opakování kroků 2 & 3.

    Každá jazyková verze má pouze jeden nadřazený prvek, který je definován <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> vlastností.

    Hledání nadřazených jazykových verzí se zastaví, pokud je <xref:System.Globalization.CultureInfo.Parent%2A> <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>vlastnost jazykové verze.

    V <xref:System.Globalization.CultureInfo.InvariantCulture>případě se nevrátíme k krokům 2 & 3, ale místo toho pokračujte krokem 5.

5. Pokud se prostředek ještě nenalezne, použije se prostředek pro výchozí (záložní) jazykovou verzi.

   Prostředky pro výchozí jazykovou verzi jsou obvykle zahrnuty v sestavení Main aplikace. Pro vlastnost však lze zadat <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> . Tato hodnota označuje, že konečné záložní umístění pro prostředky je satelitní sestavení, nikoli hlavní sestavení.

    > [!NOTE]
    > Výchozí jazyková verze je Ultimate Fallback. Proto doporučujeme vždy zahrnout vyčerpávající sadu prostředků do výchozího souboru prostředků. To pomáhá zabránit vyvolání výjimek. Díky úplnému nastavení zadáte zálohu pro všechny prostředky a zajistěte, aby měl uživatel vždy k dispozici alespoň jeden prostředek, a to i v případě, že není kulturně specifické.

6. Uznan
   - Pokud modul runtime nenajde soubor prostředků pro výchozí (záložní) jazykovou verzi, <xref:System.Resources.MissingManifestResourceException> je vyvolána výjimka nebo. <xref:System.Resources.MissingSatelliteAssemblyException>
   - Pokud je nalezen soubor prostředků, ale požadovaný prostředek není k dispozici, požadavek se `null`vrátí.
