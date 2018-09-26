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
ms.openlocfilehash: 8ee49009915273cc1e16917805f1801268ca0d26
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47173431"
---
# <a name="create-and-use-strong-named-assemblies"></a>Vytváření a používání sestavení se silným názvem

Silný název se skládá z identity sestavení – jeho jednoduchý textový název, číslo verze a informace o jazykové verzi (Pokud je poskytnuta) – plus veřejného klíče a digitální podpis. Je vygenerován ze souboru sestavení pomocí odpovídajícího soukromého klíče. (Tento soubor sestavení obsahuje manifest sestavení, který obsahuje názvy a hash hodnoty všech souborů, které tvoří sestavení).

> [!WARNING]
> Nespoléhejte na silných názvů pro zabezpečení. Poskytují jedinečné identity.

Sestavení se silným názvem lze použít pouze typy z jiných sestavení se silným názvem. V opačném případě by dojít k ohrožení integrity sestavení se silným názvem.

## <a name="strong-name-scenario"></a>Scénář silným názvem

Následující scénář popisuje proces podepisování sestavení silným názvem a pozdější odkazování s tímto názvem.

1.  Sestavení A vytvoření se silným názvem pomocí jedné z následujících metod:

    -   Použití vývojového prostředí, které podporuje vytváření silných názvů, jako je Visual Studio.

    -   Vytvoření páru kryptografických klíčů pomocí [nástroj Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) a přiřazení páru klíčů pro sestavení pomocí kompilátoru příkazového řádku nebo [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Windows Software Development Kit (SDK) poskytuje Sn.exe a Al.exe.

2.  Vývojové prostředí nebo nástroj podepíše hodnota hash souboru, který obsahuje manifest sestavení s privátním klíčem pro vývojáře. Tento digitální podpis je uložen v přenosné spustitelné (PE) souboru, který obsahuje manifest sestavení A.

3.  Sestavení B je příjemce sestavení A. Referenční části manifestu sestavení Assembly B obsahuje token, který představuje sestavení A veřejný klíč. Token je část veřejného klíče a používá místo vlastního klíče pro úsporu místa.

4.  Modul common language runtime ověří podpis silného názvu, když sestavení je umístěn v globální mezipaměti sestavení. Při vytváření vazby pomocí silného názvu v době běhu, modul common language runtime porovná s klíčem uloženým v manifestu sestavení B s klíč používaný ke generování silného názvu pro sestavení A. Pokud jsou splněné zabezpečení rozhraní .NET Framework a vazba úspěšná, sestavení Assembly B obsahuje záruku, že bylo neoprávněně manipulováno s bity sestavení a, že tyto bity skutečně pocházejí od vývojářů jazyka sestavení A.

> [!NOTE]
> Tento scénář nezabývá problémy s důvěryhodností. Sestavení mohou obsahovat úplnou signatur Microsoft Authenticode kromě silným názvem. Podpisů Authenticode selhalo zahrnout certifikát, který vytváří vztah důvěryhodnosti. Je důležité si uvědomit, že silné názvy nevyžadují kód tímto způsobem podepsat. Silné názvy poskytují jenom jedinečné identity.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>Obejít ověřování podpisů důvěryhodných sestavení

Počínaje [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], podpisy se silným názvem nejsou ověřovány, pokud je sestavení načteno do domény úplného vztahu důvěryhodnosti aplikace, jako je například výchozí domény aplikace pro `MyComputer` zóny. To se označuje jako silného názvu obejít funkce. V prostředí úplného vztahu důvěryhodnosti vyžaduje pro <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsané sestavení úplného vztahu důvěryhodnosti, bez ohledu na jejich podpisu. Funkce obejití silného názvu se vyhnete zbytečnou režii ověření podpisu se silným názvem sestavení úplného vztahu důvěryhodnosti v takovém případě umožňuje sestavení, které chcete načíst rychleji.

Funkce obejití vztahuje na všechny sestavení je podepsáno silným názvem a, který má následující vlastnosti:

-   Plně důvěryhodné bez <xref:System.Security.Policy.StrongName> důkazy (třeba `MyComputer` legitimace zóny).

-   Načíst do plně důvěryhodné <xref:System.AppDomain>.

-   Načtené z umístění pod <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost, která <xref:System.AppDomain>.

-   Není zpožděním.

Tuto funkci můžete zakázat pro jednotlivé aplikace nebo pro počítač. Zobrazit [postupy: Zákaz funkce obejití silného názvu](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Postupy: Vytvoření páru veřejného a soukromého klíče](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|Popisuje postup vytvoření páru kryptografických klíčů pro podepsání sestavení.|
|[Postupy: Podepsání sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|Popisuje, jak vytvořit sestavení se silným názvem.|
|[Vylepšené silné názvy](../../../docs/framework/app-domains/enhanced-strong-naming.md)|Popisuje vylepšení silných názvů v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].|
|[Postupy: Odkazování na sestavení se silným názvem](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|Popisuje, jak odkazovat na typy a prostředky v sestavení se silným názvem v době kompilace nebo běhu.|
|[Postupy: Zákaz funkce obejití silného názvu](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|Popisuje, jak zakázat funkci obchází ověření podpisy se silným názvem. Tuto funkci můžete zakázat pro všechny nebo pro určité aplikace.|
|[Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)|Poskytuje přehled o jeden soubor a vícesouborové sestavení.|
|[Jak zpoždění podepsání sestavení v sadě Visual Studio](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Vysvětluje, jak podepsat sestavení silným názvem po sestavení.|
|[Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|Popisuje nástroje, které jsou zahrnuty v rozhraní .NET Framework, která vám pomůže vytvořit sestavení se silnými názvy. Tento nástroj poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.|
|[Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)|Popisuje nástroj zahrnuty v rozhraní .NET Framework, která se vytvoří soubor obsahující manifest sestavení z modulů nebo zdrojových souborů.|
