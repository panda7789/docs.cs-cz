---
title: Vytváření a používání sestavení se silným názvem
ms.date: 08/01/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, about strong-named assemblies
- strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, scenarios
- assemblies [.NET Framework], strong-named
- strong-named assemblies, loading into trusted application domains
- assembly binding, strong-named
ms.assetid: ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dcdf6a88b12d12e67056657fd532dfa28c40299
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566813"
---
# <a name="create-and-use-strong-named-assemblies"></a>Vytváření a používání sestavení se silným názvem

Silný název se skládá z identity sestavení – jednoduchý textový název, číslo verze a informace o jazykové verzi (Pokud je k dispozici) – plus veřejný klíč a digitální podpis. Je vygenerován ze souboru sestavení pomocí odpovídajícího privátního klíče. (Soubor sestavení obsahuje manifest sestavení, který obsahuje názvy a hodnoty hash všech souborů, které tvoří sestavení.)

> [!WARNING]
> Nespoléhá se na silné názvy zabezpečení. Poskytují pouze jedinečnou identitu.

Sestavení se silným názvem může používat pouze typy z jiných sestavení se silným názvem. V opačném případě by došlo k ohrožení integrity sestavení se silným názvem.

## <a name="strong-name-scenario"></a>Scénář se silným názvem

Následující scénář popisuje proces podepisování sestavení silným názvem a pozdějšího odkazování na něj tímto názvem.

1. Sestavení A je vytvořeno se silným názvem pomocí jedné z následujících metod:

    - Použití vývojového prostředí, které podporuje vytváření silných názvů, jako je například Visual Studio.

    - Vytvoření páru kryptografických klíčů pomocí [nástroje Strong Name (Sn. exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) a přiřazení páru klíčů k sestavení pomocí kompilátoru příkazového řádku nebo [linkeru sestavení (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Windows SDK poskytuje sn. exe i Al. exe.

2. Vývojové prostředí nebo nástroj podepíše hodnotu hash souboru obsahujícího manifest sestavení pomocí privátního klíče vývojáře. Tento digitální podpis je uložen v přenositelném spustitelném souboru (PE), který obsahuje manifest sestavení A.

3. Sestavení B je příjemcem sestavení A. Referenční oddíl manifestu sestavení B obsahuje token, který představuje veřejný klíč sestavení A. Token je část úplného veřejného klíče a používá se místo toho, aby ušetřil místo samotný klíč.

4. Modul CLR ověří podpis silného názvu, pokud je sestavení umístěno v globální mezipaměti sestavení (GAC). Při vytváření vazby pomocí silného názvu za běhu porovná modul common language runtime klíč uložený v manifestu sestavení B s klíčem použitým k vygenerování silného názvu pro sestavení A. Pokud jsou kontroly zabezpečení .NET Framework úspěšné a vazba je úspěšná, sestavení B zaručí, že bity sestavení A nebyly úmyslně manipulovány a že tyto bity skutečně pochází od vývojářů sestavení A.

> [!NOTE]
> Tento scénář neřeší problémy důvěryhodnosti. Sestavení mohou mít kromě silného názvu také úplné signatury technologie Microsoft Authenticode. Podpisy Authenticode obsahují certifikát, který vytváří vztah důvěryhodnosti. Je důležité si uvědomit, že silné názvy nevyžadují, aby byl kód podepsán tímto způsobem. Silné názvy poskytují pouze jedinečnou identitu.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>Obejít ověření podpisu důvěryhodných sestavení

Počínaje verzí .NET Framework 3,5 Service Pack 1 nejsou signatury se silným názvem ověřovány, když je sestavení načteno do domény aplikace s plnou důvěryhodností, jako je například výchozí aplikační doména pro `MyComputer` zónu. To se označuje jako funkce obcházení silného názvu. V prostředí s úplným vztahem důvěryhodnosti požadavky <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsaná, plně důvěryhodná sestavení, bez ohledu na jejich podpis. Funkce obcházení silného názvu brání zbytečné režii při ověřování signatury silného názvu v plně důvěryhodném sestavení v této situaci, což umožňuje rychlejší načítání sestavení.

Funkce obcházení se vztahuje na jakékoli sestavení, které je podepsáno silným názvem a které má následující vlastnosti:

- Plně důvěryhodné bez <xref:System.Security.Policy.StrongName> legitimace (například má `MyComputer` legitimaci zóny).

- Načteno do plně důvěryhodného <xref:System.AppDomain>.

- Načteno z umístění pod <xref:System.AppDomainSetup.ApplicationBase%2A> vlastností. <xref:System.AppDomain>

- Nepodepsaná se zpožděním.

Tato funkce se dá zakázat pro jednotlivé aplikace nebo pro počítač. Viz [jak: Zakažte funkci](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)obcházení silného názvu.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Postupy: Vytvoření páru klíčů veřejného a soukromého](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|Popisuje, jak vytvořit pár kryptografických klíčů pro podepsání sestavení.|
|[Postupy: Podepsat sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|Popisuje, jak vytvořit sestavení se silným názvem.|
|[Vylepšené silné názvy](../../../docs/framework/app-domains/enhanced-strong-naming.md)|Popisuje vylepšení pro silné názvy v .NET Framework 4,5.|
|[Postupy: Odkazování na sestavení se silným názvem](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|Popisuje, jak odkazovat na typy nebo prostředky v sestavení se silným názvem v době kompilace nebo v době běhu.|
|[Postupy: Zakázat funkci obcházení silného názvu](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|Popisuje, jak zakázat funkci, která obchází ověřování podpisů se silným názvem. Tuto funkci je možné zakázat pro všechny nebo pro konkrétní aplikace.|
|[Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)|Poskytuje přehled o jednom souboru a vícesouborové sestavení.|
|[Jak zpozdit podepsání sestavení v aplikaci Visual Studio](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Vysvětluje, jak podepsat sestavení se silným názvem poté, co bylo sestavení vytvořeno.|
|[Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|Popisuje nástroj, který je součástí .NET Framework, který pomáhá vytvářet sestavení se silnými názvy. Tento nástroj poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.|
|[Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)|Popisuje nástroj, který je součástí .NET Framework, který generuje soubor s manifestem sestavení z modulů nebo souborů prostředků.|
