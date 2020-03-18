---
title: Vytváření a používání sestavení se silným názvem
ms.date: 08/19/2019
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
ms.openlocfilehash: 18a0b7d657290835a34c705513d0d7a4ccbfc61c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75738679"
---
# <a name="create-and-use-strong-named-assemblies"></a>Vytváření a používání sestavení se silným názvem

Silný název se skládá z identity sestavení – jeho jednoduchého textového názvu, čísla verze a informací o jazykové verzi (pokud jsou k dispozici) – plus veřejného klíče a digitálního podpisu. Je generována ze souboru sestavení pomocí odpovídajícího soukromého klíče. (Soubor sestavení obsahuje manifest sestavení, který obsahuje názvy a hashy všech souborů, které tvoří sestavení.)

> [!WARNING]
> Nespoléhejte se na silné názvy pro zabezpečení. Poskytují pouze jedinečnou identitu.

Sestavení se silným názvem může používat pouze typy z jiných sestavení se silným názvem. V opačném případě by byla ohrožena integrita sestavení se silným názvem.

> [!NOTE]
> Přestože .NET Core podporuje sestavení se silným názvem a všechna sestavení v knihovně .NET Core jsou podepsána, většina sestavení třetích stran nepotřebují silné názvy. Další informace najdete [v tématu Podpis silného názvu](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) na GitHubu.

## <a name="strong-name-scenario"></a>Scénář silného názvu

Následující scénář popisuje proces podepisování sestavení se silným názvem a později odkazování na tento název.

1. Sestava A je vytvořena se silným názvem pomocí jedné z následujících metod:

    - Použití vývojového prostředí, které podporuje vytváření silných názvů, jako je například Visual Studio.

    - Vytvoření dvojice kryptografických klíčů pomocí [nástroje Silný název (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) a přiřazení této dvojice klíčů k sestavení pomocí kompilátoru příkazového řádku nebo [propojovacího zařízení sestavení (Al.exe).](../../framework/tools/al-exe-assembly-linker.md) Sada Windows SDK poskytuje sn.exe i al.exe.

2. Vývojové prostředí nebo nástroj podepisuje hash souboru obsahující manifest sestavení s vlastní klíč vývojáře. Tento digitální podpis je uložen v přenosném spustitelném souboru (PE), který obsahuje manifest sestavení A.

3. Sestava B je spotřebitelem sestavy A. Referenční část manifestu sestavení B obsahuje token, který představuje veřejný klíč sestavení A. Token je část úplného veřejného klíče a používá se spíše než samotný klíč k úspoře místa.

4. Běžný jazyk runtime ověří podpis silného názvu při sestavení je umístěn v globální mezipaměti sestavení. Při vazbě silným názvem za běhu, za běhu common jazyk porovná klíč uložený v manifestu sestavení B s klíčem používaným ke generování silného názvu pro sestavení A. Pokud kontroly zabezpečení rozhraní .NET Framework projít a vazba úspěšné, sestavení B má záruku, že bity sestavení A nebyly zfalšovány a že tyto bity skutečně pocházejí od vývojářů sestavení A.

> [!NOTE]
> Tento scénář neřeší problémy důvěryhodnosti. Sestavení mohou kromě silného názvu přenášet úplné podpisy Microsoft Authenticode. Podpisy Authenticode obsahují certifikát, který vytváří vztah důvěryhodnosti. Je důležité si uvědomit, že silné názvy nevyžadují kód, který má být podepsán tímto způsobem. Silné názvy poskytují pouze jedinečnou identitu.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>Obejít ověření podpisu důvěryhodných sestavení

Počínaje rozhraním .NET Framework 3.5 Service Pack 1 nejsou podpisy se silným názvem ověřeny při načtení sestavení do `MyComputer` plně důvěryhodné aplikační domény, jako je například výchozí aplikační doména pro zónu. Tato funkce se označuje jako funkce obejití silného názvu. V prostředí s plnou důvěryhodností požadavky na <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsaná sestavení s plnou důvěryhodností, bez ohledu na jejich podpis. Funkce obejití silného názvu zabraňuje zbytečné režii ověření podpisu silného názvu plně důvěryhodných sestavení v této situaci, což umožňuje rychlejší načítání sestavení.

Funkce obtokse se vztahuje na všechny sestavy, které jsou podepsány silným názvem a které má následující vlastnosti:

- Plně důvěryhodný <xref:System.Security.Policy.StrongName> bez důkazů (například má `MyComputer` zóny důkazy).

- Načteno do <xref:System.AppDomain>plně důvěryhodného .

- Načteno z umístění <xref:System.AppDomainSetup.ApplicationBase%2A> pod <xref:System.AppDomain>vlastností tohoto .

- Ne odkládání podepsané.

Tuto funkci lze zakázat pro jednotlivé aplikace nebo pro počítač. Viz [Postup: Zakažte funkci obejití silného názvu](disable-strong-name-bypass-feature.md).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postup: Vytvoření páru klíčů veřejného a soukromého sektoru](create-public-private-key-pair.md)|Popisuje, jak vytvořit pár kryptografických klíčů pro podepsání sestavení.|
|[Postup: Podepsání sestavení se silným názvem](sign-strong-name.md)|Popisuje, jak vytvořit sestavení se silným názvem.|
|[Vylepšené silné pojmenování](enhanced-strong-naming.md)|Popisuje vylepšení silných názvů v rozhraní .NET Framework 4.5.|
|[Postup: Odkaz na sestavení se silným názvem](reference-strong-named.md)|Popisuje, jak odkazovat na typy nebo prostředky v sestavení se silným názvem v době kompilace nebo běhu.|
|[Postup: Zakázání funkce obejití silného názvu](disable-strong-name-bypass-feature.md)|Popisuje, jak zakázat funkci, která obchází ověřování podpisů se silným názvem. Tuto funkci lze zakázat pro všechny nebo pro konkrétní aplikace.|
|[Vytváření sestavení](create.md)|Poskytuje přehled jednosouborových a vícesouborových sestavení.|
|[Jak zpoždění podepsání sestavení v sadě Visual Studio](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Vysvětluje, jak podepsat sestavení se silným názvem po vytvoření sestavení.|
|[Sn.exe (nástroj silný název)](../../framework/tools/sn-exe-strong-name-tool.md)|Popisuje nástroj obsažený v rozhraní .NET Framework, který pomáhá vytvářet sestavení se silnými názvy. Tento nástroj poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.|
|[Al.exe (propojovací zařízení sestavení)](../../framework/tools/al-exe-assembly-linker.md)|Popisuje nástroj obsažený v rozhraní .NET Framework, který generuje soubor, který má manifest sestavení z modulů nebo souborů prostředků.|
