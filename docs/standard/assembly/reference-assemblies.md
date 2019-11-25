---
title: Referenční sestavení
description: Přečtěte si o referenčních sestaveních, speciálním typu sestavení v rozhraní .NET, která obsahují pouze plochu veřejného rozhraní API knihovny.
author: MSDN-WhiteKnight
ms.date: 09/12/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 7d2cc01861e8a3fdc260a2990ca0652878c386b0
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089272"
---
# <a name="reference-assemblies"></a>Referenční sestavení

*Referenční sestavení* jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny. Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API. Na rozdíl od jsou běžná sestavení označována jako *sestavení implementace*.

Referenční sestavení nelze načíst pro provedení, ale lze je předat jako vstup kompilátoru stejným způsobem jako sestavení implementace. Referenční sestavení jsou obvykle distribuována pomocí sady SDK (Software Development Kit) konkrétní platformy nebo knihovny.

Použití referenčního sestavení umožňuje vývojářům vytvářet programy, které cílí na konkrétní verzi knihovny bez použití úplného sestavení implementace pro tuto verzi. Předpokládejme, že máte na svém počítači pouze nejnovější verzi některé knihovny, ale chcete vytvořit program, který cílí na starší verzi této knihovny. Pokud kompilujete přímo proti implementačnímu sestavení, můžete nechtěně použít členy rozhraní API, kteří nejsou k dispozici v předchozí verzi. Tuto chybu najdete jenom při testování programu v cílovém počítači. Pokud kompilujete proti referenčnímu sestavení pro předchozí verzi, okamžitě se zobrazí chyba při kompilaci.

Referenční sestavení může také představovat kontrakt, to znamená sadu rozhraní API, která neodpovídají konkrétnímu sestavení implementace. Taková odkazovaná sestavení označovaná jako *sestavení kontraktu*lze použít k zacílení na více platforem, které podporují stejnou sadu rozhraní API. Například .NET Standard poskytuje sestavení kontraktu *netstandard. dll*, které představuje sadu společných rozhraní API sdílených mezi různými platformami .NET. Implementace těchto rozhraní API jsou obsaženy v různých sestaveních na různých platformách, například *mscorlib. dll* v .NET Framework nebo *System. Private. CoreLib. dll* v .NET Core. Knihovna, která cílí na .NET Standard, může běžet na všech platformách, které podporují .NET Standard.

## <a name="using-reference-assemblies"></a>Použití referenčních sestavení

Chcete-li použít určitá rozhraní API z projektu, je nutné přidat odkazy na jejich sestavení. Můžete přidat odkazy buď na sestavení implementace, nebo na referenční sestavení. Doporučuje se používat referenční sestavení, kdykoli jsou k dispozici. Tím zajistíte, že budete používat pouze podporované členy rozhraní API v cílové verzi, které mají být používány návrháři rozhraní API. Použití referenčního sestavení zajišťuje závislost na podrobnostech implementace.

Referenční sestavení pro knihovny .NET Framework jsou distribuována pomocí sad targeting pack. Můžete je získat stažením samostatného instalačního programu nebo výběrem komponenty v instalačním programu sady Visual Studio. Další informace najdete v tématu [instalace .NET Framework pro vývojáře](../../framework/install/guide-for-developers.md). V případě .NET Core a .NET Standard se referenční sestavení automaticky stáhnou podle potřeby (přes NuGet) a odkazuje na ně. Pro .NET Core 3,0 a novější se referenční sestavení pro základní rozhraní nacházejí v balíčku [Microsoft. NETCore. app. ref](https://www.nuget.org/packages/Microsoft.NETCore.App.Ref) (místo verzí starší než 3,0 se používá balíček [Microsoft. NETCore. app](https://www.nuget.org/packages/Microsoft.NETCore.App) ). Další informace najdete v tématu [balíčky, metabalíčky a rozhraní](../../core/packages.md) v příručce .NET Core.

Pokud přidáte odkazy na .NET Framework sestavení v aplikaci Visual Studio pomocí dialogu **Přidat odkaz** , vyberete sestavení ze seznamu a aplikace Visual Studio automaticky vyhledá referenční sestavení, která odpovídají verzi cílového rozhraní. vybráno v projektu. Totéž platí pro přidání odkazů přímo do projektu MSBuild pomocí položky [referenčního](/visualstudio/msbuild/common-msbuild-project-items#reference) projektu: stačí zadat pouze název sestavení, nikoli úplnou cestu k souboru. Pokud přidáte odkazy na tato sestavení v příkazovém řádku pomocí možnosti kompilátoru `-reference` ([v C# ](../../csharp/language-reference/compiler-options/reference-compiler-option.md) a v [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md)) nebo pomocí metody <xref:Microsoft.CodeAnalysis.Compilation.AddReferences%2A?displayProperty=nameWithType> v rozhraní API Roslyn, musíte ručně zadat soubory referenčního sestavení pro správnou verzi cílové platformy. Soubory referenčního sestavení .NET Framework jsou umístěny v *% ProgramFiles (x86)%\\referenční sestavení\\Microsoft\\Framework\\. Adresář NETFramework* Pro .NET Core můžete vynutit operaci publikování pro kopírování referenčních sestavení pro vaši cílovou platformu do podadresáře *Publish/ReFS* v adresáři výstupu nastavením vlastnosti `PreserveCompilationContext` projektu na `true`. Potom můžete do kompilátoru předat tyto soubory referenčních sestavení. Použití `DependencyContext` z balíčku [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/) vám může pomoci najít jejich cesty.

Vzhledem k tomu, že neobsahují žádnou implementaci, nelze načíst referenční sestavení pro provedení; Pokud to chcete udělat, výsledkem je <xref:System.BadImageFormatException?displayProperty=nameWithType>. Stále je však možné je načíst do kontextu pouze pro reflexi (pomocí metody <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType>), pokud potřebujete prošetřit jejich obsah.

## <a name="generating-reference-assemblies"></a>Generování referenčních sestavení

Generování referenčních sestavení pro vaše knihovny může být užitečné, pokud vaši uživatelé knihovny potřebují sestavit své programy s mnoha různými verzemi knihovny. Distribuce implementačních sestavení pro všechny tyto verze může být nepraktická z důvodu jejich velké velikosti. Referenční sestavení jsou menší velikosti a jejich distribuce jako součást sady SDK vaší knihovny zmenšuje velikost stahovaných souborů a šetří místo na disku.

Nástroje pro IDEs a vytváření sestavení také můžou využít referenční sestavení k omezení doby sestavení v případě rozsáhlých řešení, která se skládají z více knihoven tříd. Obvykle v případě přírůstkového sestavení se projekt znovu vytvoří, když se změní kterýkoli ze vstupních souborů, včetně sestavení, na kterých závisí. Implementace sestavení se změní vždy, když programátor změní implementaci kteréhokoli člena. Referenční sestavení se změní pouze v případě, že je ovlivněno jeho veřejné rozhraní API. Proto použití referenčního sestavení jako vstupního souboru namísto sestavení implementace umožňuje přeskočení sestavení závislého projektu v některých případech.

Můžete generovat referenční sestavení:

- V projektu MSBuild pomocí [vlastnosti `ProduceReferenceAssembly` projektu](/visualstudio/msbuild/common-msbuild-project-properties).
- Při kompilování programu z příkazového řádku, specifiying `-refonly`[C#](../../csharp/language-reference/compiler-options/refonly-compiler-option.md) ( / [Visual Basic](../../visual-basic/reference/command-line-compiler/refonly-compiler-option.md) ) nebo `-refout`[C#](../../csharp/language-reference/compiler-options/refout-compiler-option.md) ( [ / Visual Basic) možnosti](../../visual-basic/reference/command-line-compiler/refout-compiler-option.md)kompilátoru.
- Při použití rozhraní Roslyn API nastavením <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.EmitMetadataOnly?displayProperty=nameWithType> na `true` a <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.IncludePrivateMembers?displayProperty=nameWithType> na `false` v objektu předaného metodě <xref:Microsoft.CodeAnalysis.Compilation.Emit%2A?displayProperty=nameWithType>.

Chcete-li distribuovat referenční sestavení pomocí balíčků NuGet, je nutné je zahrnout do podadresáře *ref \\* v adresáři Package místo v podadresáři *lib \\* , který se používá pro sestavení implementace.

## <a name="reference-assemblies-structure"></a>Struktura referenčních sestavení

Referenční sestavení jsou rozšíření souvisejícího konceptu, *sestavení pouze metadat*. Sestavení pouze s metadaty mají své tělo metody nahrazené jediným `throw null`m textem, ale zahrnují všechny členy kromě anonymních typů. Důvodem použití `throw null`ch orgánů (na rozdíl od žádného těla) je, že **Nástroj PEVerify** lze spustit a předat (čímž ověří úplnost metadat).

Referenční sestavení dále odstraňují metadata (soukromá členové) od sestavení, která jsou pouze metadata:

- Referenční sestavení obsahuje pouze odkazy na to, co potřebuje na povrchu rozhraní API. Reálné sestavení může mít další odkazy týkající se konkrétních implementací. Například referenční sestavení pro `class C { private void M() { dynamic d = 1; ... } }` neodkazuje na žádné typy, které jsou požadovány pro `dynamic`.
- Soukromá funkce – členové (metody, vlastnosti a události) jsou odebrány v případech, kdy jejich odebrání nepozorovatelně ovlivní kompilaci. Pokud nejsou k dispozici žádné atributy [InternalsVisibleTo](xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute) , jsou také odebrány členy interní funkce.

Metadata v referenčních sestaveních stále zachovají následující informace:

- Všechny typy, včetně privátních a vnořených typů.
- Všechny atributy, i ty, které jsou interní.
- Všechny virtuální metody.
- Explicitní implementace rozhraní.
- Explicitně implementované vlastnosti a události, protože jejich přistupující objekty jsou virtuální.
- Všechna pole struktury.

Referenční sestavení obsahují atribut [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) na úrovni sestavení. Tento atribut lze zadat ve zdroji; pak kompilátor nebude muset syntetizovat. Z důvodu tohoto atributu modul runtime odmítne načíst referenční sestavení ke spuštění (ale mohou být načtena pouze v režimu reflexe).

Přesné podrobnosti struktury sestavení reference závisí na verzi kompilátoru. Novější verze se můžou rozhodnout vyloučit další metadata, pokud se určí tak, aby neovlivnilo veřejnou plochu rozhraní API.

> [!NOTE]
> Informace v této části platí pouze pro referenční sestavení generovaná kompilátory Roslyn počínaje C# verzí 7,1 nebo Visual Basic verze 15,3. Struktura referenčních sestavení pro .NET Framework a knihovny .NET Core se může v některých podrobnostech lišit, protože používají vlastní mechanismus generování referenčních sestavení. Například mohou mít zcela prázdné tělo metody místo těla `throw null`. Obecně platí ale obecná zásada: nemají použitelné implementace metod a obsahují metadata jenom pro členy, kteří mají pozorovatelný dopad z hlediska veřejné rozhraní API.

## <a name="see-also"></a>Viz také:

- [Sestavení v .NET](index.md)
- [Přehled cílení na rozhraní](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)
