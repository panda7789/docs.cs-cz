---
title: Referenční sestavení
description: Informace o referenčních sestaveních, což je zvláštní typ sestavení v rozhraní .NET, která obsahují pouze veřejný povrch rozhraní API knihovny.
author: MSDN-WhiteKnight
ms.date: 09/12/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 938942caf81c54a8aa9207dbe87559438ffb252e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79141065"
---
# <a name="reference-assemblies"></a>Referenční sestavení

*Referenční sestavení* jsou zvláštní typ sestavení, které obsahují pouze minimální množství metadat, které jsou nutné k reprezentaci veřejného povrchu rozhraní API knihovny. Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučit všechny implementace členů a deklarace soukromých členů, které nemají žádný pozorovatelný dopad na jejich smlouvy rozhraní API. Naproti tomu pravidelná sestavení se nazývají *sestavení implementace*.

Referenční sestavení nelze načíst pro spuštění, ale mohou být předány jako vstup kompilátoru stejným způsobem jako sestavení implementace. Referenční sestavení jsou obvykle distribuovány se sadou SDK (Software Development Kit) určité platformy nebo knihovny.

Použití referenčního sestavení umožňuje vývojářům vytvářet programy, které cílí na konkrétní verzi knihovny bez nutnosti sestavení úplné implementace pro tuto verzi. Předpokládejme, že máte v počítači pouze nejnovější verzi některé knihovny, ale chcete vytvořit program, který cílí na starší verzi této knihovny. Pokud kompilujete přímo proti sestavení implementace, můžete neúmyslně použít členy rozhraní API, které nejsou k dispozici v předchozí verzi. Tuto chybu najdete pouze při testování programu na cílovém počítači. Pokud zkompilujete proti referenčnísestavení pro starší verzi, budete okamžitě získat chybu kompilace.

Referenční sestavení může také představovat kontrakt, to znamená sadu api, které neodpovídají sestavení konkrétní implementace. Tato referenční sestavení, nazývaná *sestavení smlouvy*, lze použít k cílení na více platforem, které podporují stejnou sadu api. Například .NET Standard poskytuje sestavení smlouvy *netstandard.dll*, který představuje sadu společných rozhraní API sdílené mezi různými platformami .NET. Implementace těchto rozhraní API jsou obsaženy v různých sestaveních na různých platformách, jako je například *mscorlib.dll* na rozhraní .NET Framework nebo *System.Private.CoreLib.dll* na .NET Core. Knihovna, která cílí na standard .NET, může být spuštěna na všech platformách, které podporují standard .NET.

## <a name="using-reference-assemblies"></a>Použití referenčních sestav

Chcete-li použít určitá nastavení API z projektu, musíte přidat odkazy na jejich sestavení. Můžete přidat odkazy na sestavení implementace nebo na referenční sestavení. Doporučujeme používat referenční sestavení, kdykoli jsou k dispozici. Tím zajistíte, že používáte pouze podporované členy rozhraní API v cílové verzi, které mají používat návrháři rozhraní API. Použití referenčního sestavení zajišťuje, že nejste s závislostí na podrobnostech implementace.

Referenční sestavení pro knihovny rozhraní .NET Framework jsou distribuována s balíčky cílení. Můžete je získat stažením samostatného instalačního programu nebo výběrem součásti v instalačním programu sady Visual Studio. Další informace naleznete [v tématu Instalace rozhraní .NET Framework pro vývojáře](../../framework/install/guide-for-developers.md). Pro .NET Core a .NET Standard jsou referenční sestavení automaticky stažena podle potřeby (přes NuGet) a odkazována. Pro .NET Core 3.0 a vyšší referenční sestavení pro základní rozhraní jsou v balíčku [Microsoft.NETCore.App.Ref](https://www.nuget.org/packages/Microsoft.NETCore.App.Ref) (balíček [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) se používá místo pro verze před 3.0). Další informace naleznete [v tématu Balíčky, metabalíčky a architektury](../../core/packages.md) v průvodci jádrem rozhraní .NET.

Když přidáte odkazy na sestavení rozhraní .NET Framework v sadě Visual Studio pomocí dialogového okna **Přidat odkaz,** vyberete sestavení ze seznamu a Visual Studio automaticky vyhledá referenční sestavení, která odpovídají verzi cílového rozhraní vybrané v projektu. Totéž platí pro přidávání odkazů přímo do projektu MSBuild pomocí položky [projektu Reference:](/visualstudio/msbuild/common-msbuild-project-items#reference) stačí zadat název sestavení, nikoli úplnou cestu k souboru. `-reference` Přidáte-li odkazy na tato sestavení v příkazovém řádku pomocí možnosti kompilátoru[(v jazyce C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) a v [jazyce Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md)) nebo pomocí <xref:Microsoft.CodeAnalysis.Compilation.AddReferences%2A?displayProperty=nameWithType> metody v rozhraní API Roslyn, je nutné ručně zadat soubory sestavení odkazu pro správnou verzi cílové platformy. Soubory referenčních sestavení rozhraní .NET Framework jsou *umístěny\\v %ProgramFiles(x86)% Reference Assemblies\\Microsoft\\Framework\\. NETFramework.* Pro .NET Core můžete vynutit operaci publikování ke kopírování referenčních sestavení pro cílovou platformu `PreserveCompilationContext` do podadresáře *publikování/refs* výstupního adresáře nastavením vlastnosti projektu na `true`. Potom můžete předat tyto soubory referenčního sestavení kompilátoru. Pomocí `DependencyContext` z [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/) balíček může pomoci najít jejich cesty.

Vzhledem k tomu, že neobsahují žádnou implementaci, referenční sestavení nelze načíst pro spuštění. Při pokusu o <xref:System.BadImageFormatException?displayProperty=nameWithType>to má za následek . Pokud chcete prozkoumat obsah referenčního sestavení, můžete jej načíst do kontextu pouze reflexe v rozhraní .NET Framework (pomocí <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> metody) nebo do jádra <xref:System.Reflection.MetadataLoadContext> in .NET Core.

## <a name="generating-reference-assemblies"></a>Generování referenčních sestavení

Generování referenčních sestavení pro knihovny může být užitečné, když spotřebitelé knihovny potřebují vytvářet své programy podle mnoha různých verzí knihovny. Distribuce sestavení implementace pro všechny tyto verze může být nepraktické z důvodu jejich velké velikosti. Referenční sestavení mají menší velikost a jejich distribuce jako součást sady SDK knihovny zmenšuje velikost stahování a šetří místo na disku.

IDE a nástroje sestavení také můžete využít referenční sestavení ke zkrácení doby sestavení v případě velkých řešení skládající se z více knihoven tříd. Obvykle ve scénářích přírůstkového sestavení je projekt znovu sestaven při změně některého z jeho vstupních souborů, včetně sestavení, na kterých závisí. Sestavení implementace se změní vždy, když programátor změní implementaci libovolného člena. Referenční sestavení se změní pouze v případě, že je ovlivněno jeho veřejné rozhraní API. Takže pomocí referenčního sestavení jako vstupního souboru namísto sestavení implementace umožňuje v některých případech přeskočení sestavení závislého projektu.

Můžete generovat referenční sestavení:

- V projektu MSBuild pomocí [ `ProduceReferenceAssembly` vlastnosti projektu](/visualstudio/msbuild/common-msbuild-project-properties).
- Při kompilaci programu z příkazového řádku, `-refonly` podle specifiying `-refout` ([C#](../../csharp/language-reference/compiler-options/refonly-compiler-option.md) / Visual[Basic](../../visual-basic/reference/command-line-compiler/refonly-compiler-option.md) ) nebo ([C#](../../csharp/language-reference/compiler-options/refout-compiler-option.md) / [Visual Basic](../../visual-basic/reference/command-line-compiler/refout-compiler-option.md)) možnosti kompilátoru.
- Při použití rozhraní API Roslyn, <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.IncludePrivateMembers?displayProperty=nameWithType> `false` nastavením <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.EmitMetadataOnly?displayProperty=nameWithType> `true` a v <xref:Microsoft.CodeAnalysis.Compilation.Emit%2A?displayProperty=nameWithType> objektu předaným metodě.

Pokud chcete distribuovat referenční sestavení s balíčky NuGet, musíte je zahrnout do podadresáře *ref\\ * v adresáři balíčků namísto v podadresáři *lib\\ * používaném pro sestavení implementace.

## <a name="reference-assemblies-structure"></a>Struktura referenčních sestav

Referenční sestavení jsou rozšíření související koncepce, *pouze metadata sestavení*. Sestavení pouze metadata mají jejich těla metod `throw null` nahrazena jedním tělem, ale zahrnují všechny členy kromě anonymních typů. Důvodem pro `throw null` použití těla (na rozdíl od žádná těla) je tak, aby **PEVerify** můžete spustit a předat (tedy ověření úplnosti metadat).

Referenční sestavení dále odeberou metadata (soukromé členy) ze sestavení pouze metadat:

- Referenční sestavení obsahuje pouze odkazy na to, co potřebuje v povrchu rozhraní API. Skutečné sestavení může mít další odkazy týkající se konkrétní implementace. Například referenční sestavení `class C { private void M() { dynamic d = 1; ... } }` pro neodkazuje na žádné `dynamic`typy požadované pro .
- Soukromé členy funkce (metody, vlastnosti a události) jsou odebrány v případech, kdy jejich odebrání nemá pozorovatelný vliv na kompilaci. Pokud neexistují žádné [InternalsVisibleTo](xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute) atributy, vnitřní členy funkce jsou také odebrány.

Metadata v referenčních sestaveních nadále uchovává následující informace:

- Všechny typy, včetně soukromých a vnořených typů.
- Všechny atributy, dokonce i vnitřní.
- Všechny virtuální metody.
- Explicitní implementace rozhraní.
- Explicitně implementované vlastnosti a události, protože jejich přístupové objekty jsou virtuální.
- Všechna pole staveb.

Referenční sestavení obsahují atribut [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) na úrovni sestavení. Tento atribut může být zadán ve zdroji; pak kompilátor nebude muset syntetizovat. Z důvodu tohoto atributu budou runtimes odmítnout načíst referenční sestavení pro spuštění (ale mohou být načteny v režimu pouze reflexe).

Přesné podrobnosti struktury sestavení odkazu závisí na verzi kompilátoru. Novější verze se mohou rozhodnout vyloučit další metadata, pokud je zjištěno, že nemá vliv na veřejné rozhraní API.

> [!NOTE]
> Informace v této části je použitelná pouze pro referenční sestavení generovaná kompilátory Roslyn od c# verze 7.1 nebo Visual Basic verze 15.3. Struktura referenčních sestavení pro rozhraní .NET Framework a knihovny .NET Core se může v některých podrobnostech lišit, protože používají vlastní mechanismus generování referenčních sestavení. Například mohou mít zcela prázdná těla metod namísto těla. `throw null` Ale obecný princip stále platí: nemají použitelné implementace metod a obsahují metadata pouze pro členy, které mají pozorovatelný dopad z hlediska veřejného rozhraní API.

## <a name="see-also"></a>Viz také

- [Sestavení v .NET](index.md)
- [Přehled cílení na rozhraní](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Postup: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)
