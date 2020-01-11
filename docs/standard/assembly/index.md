---
title: Sestavení v .NET
ms.date: 08/15/2019
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.openlocfilehash: 9fd0c55294815c191f1e116dd4e16a44693f3565
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900596"
---
# <a name="assemblies-in-net"></a>Sestavení v .NET

Sestavení tvoří základní jednotky nasazení, správy verzí, opětovného použití, oboru aktivace a oprávnění zabezpečení pro. Aplikace založené na síti. Sestavení je kolekce typů a prostředků, které jsou vytvořeny tak, aby vzájemně spolupracovaly a tvořily logickou jednotku funkčnosti. Sestavení mají formu spustitelného souboru ( *. exe*) nebo souborů dynamické knihovny ( *. dll*) a jsou stavebními bloky aplikací .NET. Poskytují modul CLR (Common Language Runtime) s informacemi, které musí být vědomy typu implementace.

V rozhraní .NET Core a .NET Framework můžete sestavit sestavení z jednoho nebo více souborů zdrojového kódu. V .NET Framework sestavení mohou obsahovat jeden nebo více modulů. To umožňuje, aby byly větší projekty plánovány, aby několik vývojářů fungovalo na samostatných souborech nebo modulech zdrojového kódu, které jsou kombinovány pro vytvoření jednoho sestavení. Další informace o modulech naleznete v tématu [How to: Build a vícesouborové sestavení](../../framework/app-domains/build-multifile-assembly.md).

Sestavení mají následující vlastnosti:

- Sestavení jsou implementována jako soubory *. exe* nebo *. dll* .

- Pro knihovny cílené na .NET Framework můžete sdílet sestavení mezi aplikacemi jejich vložením do [globální mezipaměti sestavení (GAC)](../../framework/app-domains/gac.md). Sestavení se silným názvem je nutné před tím, než je můžete zahrnout do globální mezipaměti sestavení (GAC). Další informace naleznete v tématu [sestavení se silným názvem](strong-named.md).

- Sestavení jsou načtena do paměti pouze v případě, že jsou požadována. Pokud se nepoužívají, nebudou načteny. To znamená, že sestavení mohou představovat efektivní způsob správy prostředků ve větších projektech.

- Můžete programově získat informace o sestavení pomocí reflexe. Další informace naleznete v tématu [Reflection (C#)](../../csharp/programming-guide/concepts/reflection.md) nebo [Reflection (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Sestavení lze načíst pouze pro kontrolu pomocí třídy <xref:System.Reflection.MetadataLoadContext> v rozhraní .NET Core a metody <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> v rozhraní .NET Core a .NET Framework.

## <a name="assemblies-in-the-common-language-runtime"></a>Sestavení v modulu CLR (Common Language Runtime)

Sestavení poskytují modul CLR (Common Language Runtime) s informacemi, které musí být vědomy typu implementace. V modulu runtime neexistuje typ mimo kontext sestavení.

Sestavení definuje následující informace:

- Kód, který modul common language runtime spouští. Všimněte si, že každé sestavení může mít pouze jeden vstupní bod: `DllMain`, `WinMain`nebo `Main`.

- Hranice zabezpečení. Sestavení je jednotka, ve které jsou požadována a udělována oprávnění. Další informace o hranicích zabezpečení v sestaveních naleznete v tématu [požadavky na zabezpečení sestavení](security-considerations.md).

- Hranice typu Jednotlivé identity typu zahrnují název sestavení, ve kterém se nachází. Typ s názvem `MyType`, který je načten v oboru jednoho sestavení, není stejný jako typ s názvem `MyType`, který je načten v oboru jiného sestavení.

- Hranice oboru odkazů [Manifest sestavení](#assembly-manifest) má metadata, která se používají pro překlad typů a uspokojení požadavků na prostředky. Manifest určuje typy a prostředky, které mají být vystaveny mimo sestavení, a vytvoří výčet jiných sestavení, na kterých závisí. Kód jazyka MSIL (Microsoft Intermediate Language) v přenositelném spustitelném souboru (PE) nebude proveden pouze v případě, že má přidružený [manifest sestavení](#assembly-manifest).

- Hranice verze Sestavení je nejmenší jednotka s možnou verzí v modulu CLR (Common Language Runtime). Všechny typy a prostředky ve stejném sestavení jsou ve verzi jako jednotka. [Manifest sestavení](#assembly-manifest) popisuje závislosti verze, které zadáte pro všechna závislá sestavení. Další informace o tom, jak se správou verzí, najdete v tématu [Správa verzí sestavení](versioning.md).

- Jednotka nasazení. Při spuštění aplikace je nutné, aby byla k dispozici pouze ta sestavení, která aplikace zpočátku volá. Jiná sestavení, jako například sestavení obsahující prostředky lokalizace nebo obslužné třídy, lze načíst na vyžádání. To umožňuje, aby při prvním stažení aplikace byly jednoduché a tenké. Další informace o nasazení sestavení naleznete v tématu [Deploy Applications](../../framework/deployment/index.md).

- Souběžná jednotka spuštění. Další informace o spuštění více verzí sestavení naleznete v tématu [sestavení a souběžné spouštění](side-by-side-execution.md).

## <a name="create-an-assembly"></a>Vytvoření sestavení

Sestavení mohou být statická nebo dynamická. Statická sestavení jsou uložena na disku v přenosných spustitelných souborech (PE). Statická sestavení mohou zahrnovat rozhraní, třídy a prostředky, jako jsou bitmapy, soubory JPEG a jiné soubory prostředků. Můžete také vytvořit dynamická sestavení, která se spouštějí přímo z paměti a nejsou uložena na disk před provedením. Na disk můžete dynamická sestavení uložit až poté, co jsou spuštěna.

Existuje několik způsobů vytváření sestavení. Můžete použít vývojové nástroje, jako je například Visual Studio, které mohou vytvářet soubory *. dll* nebo *. exe* . Pomocí nástrojů v Windows SDK můžete vytvářet sestavení s moduly z jiných vývojových prostředí. Pro vytváření dynamických sestavení můžete také použít rozhraní API modulu CLR (Common Language Runtime), jako je například <xref:System.Reflection.Emit?displayProperty=nameWithType>.

Zkompilujte sestavení jejich sestavením v aplikaci Visual Studio, Sestavujte je pomocí nástrojů rozhraní příkazového řádku .NET Core nebo Sestavujte .NET Framework sestavení pomocí kompilátoru příkazového řádku. Další informace o vytváření sestavení pomocí nástrojů rozhraní příkazového řádku .NET Core naleznete v tématu [.NET Core Command-line interface Tools](../../core/tools/index.md). Pro vytváření sestavení pomocí kompilátorů příkazového řádku, přečtěte si [sestavení příkazového řádku s CSc. exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) pro C#nebo [Sestavte z příkazového řádku](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) pro Visual Basic.

> [!NOTE]
> Chcete-li sestavit sestavení v aplikaci Visual Studio, vyberte v nabídce **sestavení** položku **sestavit**.

## <a name="assembly-manifest"></a>Manifest sestavení

Každé sestavení má soubor *manifestu sestavení* . Podobně jako obsah, manifest sestavení obsahuje:

- Identita sestavení (jeho název a verze)

- Tabulka souborů popisující všechny ostatní soubory, které tvoří sestavení, jako například jiná sestavení, která jste vytvořili, že soubor *. exe* nebo *. dll* spoléhá na soubory rastrového obrázku nebo soubory Readme.

- *Seznam odkazů na sestavení*, což je seznam všech vnějších závislostí, například *. dll*s nebo jiné soubory. Odkazy na sestavení obsahují odkazy na globální i privátní objekty. Globální objekty jsou k dispozici pro všechny ostatní aplikace. V rozhraní .NET Core jsou globální objekty spojeny s konkrétním modulem runtime .NET Core. V .NET Framework se globální objekty nacházejí v globální mezipaměti sestavení (GAC). *System. IO. dll* je příkladem sestavení v globální mezipaměti sestavení (GAC). Privátní objekty musí být v adresáři, ve kterém je vaše aplikace nainstalovaná, na úrovni adresáře nebo pod ním.

Vzhledem k tomu, že sestavení obsahují informace o obsahu, správy verzí a závislostech, aplikace, které je používají, se nemusí podepisovat spoléhají na externí zdroje, jako je registr v systémech Windows, aby fungovaly správně. Sestavení snižují konflikty *knihoven DLL* a umožňují spolehlivější a snazší nasazení aplikací. V mnoha případech můžete nainstalovat. Pomocí čisté aplikace můžete jednoduše zkopírovat své soubory do cílového počítače. Další informace naleznete v tématu [manifest sestavení](manifest.md).

## <a name="add-a-reference-to-an-assembly"></a>Přidat odkaz na sestavení

Chcete-li použít sestavení v aplikaci, je nutné přidat odkaz na něj. Jakmile je odkazováno na sestavení, všechny dostupné typy, vlastnosti, metody a další členy svých oborů názvů jsou k dispozici pro vaši aplikaci, jako by jejich kód byl součástí zdrojového souboru.

> [!NOTE]
> Většina sestavení z knihovny tříd .NET je odkazována automaticky. Pokud se na systémové sestavení neodkazuje automaticky, můžete pro .NET Core přidat odkaz na balíček NuGet, který obsahuje sestavení. Buď použijte Správce balíčků NuGet v aplikaci Visual Studio, nebo přidejte [\<prvek > PackageReference](../../core/tools/dependencies.md#the-new-packagereference-element) pro sestavení do projektu *. csproj* nebo *. vbproj* . V .NET Framework můžete přidat odkaz na sestavení pomocí dialogového okna **Přidat odkaz** v aplikaci Visual Studio nebo pomocí možnosti příkazového řádku `-reference` pro kompilátory [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) nebo [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) .

V C#nástroji můžete použít dvě verze stejného sestavení v jediné aplikaci. Další informace najdete v tématu [extern alias](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="related-content"></a>Související obsah

|Název|Popis|
|-----------|-----------------|
|[Obsah sestavení](contents.md)|Prvky, které tvoří sestavení.|
|[Manifest sestavení](manifest.md)|Data v manifestu sestavení a jejich uložení v sestaveních.|
|[Globální mezipaměť sestavení](../../framework/app-domains/gac.md)|Jak globální mezipaměť sestavení (GAC) ukládá a používá sestavení.|
|[Sestavení se silným názvem](strong-named.md)|Charakteristiky sestavení se silným názvem.|
|[Požadavky na zabezpečení sestavení](security-considerations.md)|Jak funguje zabezpečení se sestaveními.|
|[Správa verzí sestavení](versioning.md)|Přehled zásad správy verzí .NET Framework.|
|[Umístění sestavení](../../framework/app-domains/assembly-placement.md)|Kam umístit sestavení.|
|[Sestavení a souběžné spouštění](side-by-side-execution.md)|Použijte současně více verzí modulu runtime nebo sestavení.|
|[Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Vytváření dynamických sestavení.|
|[Způsob, jakým modul runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Způsob, jakým .NET Framework řeší odkazy na sestavení v době běhu.|

## <a name="reference"></a>Odkaz

<xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>Viz také:

- [Formát souboru sestavení .NET](file-format.md)
- [Friend – sestavení](friend.md)
- [Referenční sestavení](reference-assemblies.md)
- [Postupy: načítání a uvolňování sestavení](load-unload.md)
- [Postupy: použití a ladění nevytížení sestavení v .NET Core](unloadability.md)
- [Postupy: určení, zda je soubor sestavením](identify.md)
