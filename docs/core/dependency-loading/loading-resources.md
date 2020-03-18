---
title: Algoritmus načítání satelitního sestavení - .NET Core
description: Popis podrobností algoritmu satelitního nakládacího systému v rozhraní .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70105313"
---
# <a name="satellite-assembly-loading-algorithm"></a>Algoritmus satelitního nakládacího systému

Satelitní sestavení se používají k ukládání lokalizovaných prostředků přizpůsobených pro jazyk a jazykovou verzi.

Satelitní sestavení používají jiný algoritmus načítání než obecně spravovaná sestavení.

## <a name="when-are-satellite-assemblies-loaded"></a>Kdy jsou satelitní sestavení načtena?

Satelitní sestavení jsou načteny při načítání lokalizovaného prostředku.

Základní rozhraní API pro načtení <xref:System.Resources.ResourceManager?displayProperty=fullName> lokalizovaných prostředků je třída. Nakonec <xref:System.Resources.ResourceManager> třída bude volat <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> metodu <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>pro každý .

Rozhraní API vyšší úrovně může abstrahujte rozhraní API nižší úrovně.

## <a name="algorithm"></a>Algoritmus

Záložní proces prostředku .NET Core zahrnuje následující kroky:

1. Určete `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instanci. Ve všech případech `active` instance je vykonávající <xref:System.Runtime.Loader.AssemblyLoadContext>sestavení .

2. Instance `active` se pokusí načíst satelitní sestavení pro požadovanou jazykovou verzi v pořadí podle priority:
    - Kontroluji jeho mezipaměť.
    - Kontrola adresáře aktuálně spuštěného sestavení pro podadresář, který <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> odpovídá `es-MX`požadovanému (například).

        > [!NOTE]
        > Tato funkce nebyla implementována v rozhraní .NET Core před 3.0.
        >
        > [!NOTE]
        > V Linuxu a macOS je podadresář rozlišován podle velkých a malých písmen a musí:
        > - Přesně tak, aby se shodoval.
        > - Buďte v malé písmeno.

    - Pokud `active` je <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, spuštěním [výchozí satelitní (prostředek) sondování](default-probing.md#satellite-resource-assembly-probing) logiky.

    - Volání <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> funkce.

    - Vyvolání <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> akce.

    - Vyvolání <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> akce.

3. Pokud je načteno satelitní sestavení:
   - Událost <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> je vyvolána.
   - Sestavení je prohledáno pro požadovaný prostředek. Pokud za běhu najde prostředek v sestavení, použije jej. Pokud zdroj nenajde, bude pokračovat v hledání.

    > [!NOTE]
    > Chcete-li najít prostředek v satelitním sestavení, hledá za běhu <xref:System.Resources.ResourceManager> soubor <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>prostředků požadovaný pro aktuální . V souboru prostředků vyhledá požadovaný název prostředku. Pokud buď nebyl nalezen, prostředek je považován za nebyl nalezen.

4. Další runtime prohledává nadřazená sestavení jazykové verze prostřednictvím mnoha potenciálních úrovní, pokaždé, když opakuje kroky 2 & 3.

    Každá jazyková verze má pouze jeden <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> nadřazený, který je definován vlastností.

    Hledání nadřazené jazykové verze <xref:System.Globalization.CultureInfo.Parent%2A> se <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>zastaví, když je vlastnost jazykové verze .

    Pro <xref:System.Globalization.CultureInfo.InvariantCulture>, nevracíme se k krokům 2 & 3, ale spíše pokračovat krokem 5.

5. Pokud prostředek stále nebyl nalezen, použije se prostředek pro výchozí (záložní) jazykovou verzi.

   Prostředky pro výchozí jazykovou verzi jsou obvykle zahrnuty v sestavení hlavní aplikace. Můžete však <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> zadat <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> pro vlastnost. Tato hodnota označuje, že konečné záložní umístění pro prostředky je satelitní sestavení spíše než hlavní sestavení.

    > [!NOTE]
    > Výchozí jazyková verze je konečný záložní. Proto doporučujeme vždy zahrnout vyčerpávající sadu prostředků ve výchozím souboru prostředků. To pomáhá zabránit vyvolání výjimek. Tím, že vyčerpávající sadu, poskytujete záložní pro všechny prostředky a ujistěte se, že alespoň jeden prostředek je vždy k dispozici pro uživatele, i když není kulturně specifické.

6. Konečně
   - Pokud runtime nenajde soubor prostředků pro výchozí (záložní) jazykovou <xref:System.Resources.MissingManifestResourceException> <xref:System.Resources.MissingSatelliteAssemblyException> verzi, je vyvolána výjimka nebo výjimka.
   - Pokud je soubor prostředků nalezen, ale požadovaný prostředek není `null`k dispozici, požadavek vrátí .
