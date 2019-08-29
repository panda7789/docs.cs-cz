---
title: Balení a nasazení prostředků v aplikacích .NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- single resource assembly
- satellite assemblies
- default culture for applications
- names [.NET Framework], resources
- fallback process for resources
- grouping cultures
- application resources, deploying
- application resources, naming conventions
- culture, packaging and deploying resources
- resource files, naming conventions
- packaging application resources
- application resources, fallback processes
- resource files, fallback processes
- localizing resources
- neutral cultures
ms.assetid: b224d7c0-35f8-4e82-a705-dd76795e8d16
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4092d8694bdb896db1332bd73afae3f62bba36cf
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105915"
---
# <a name="packaging-and-deploying-resources-in-net-apps"></a>Balení a nasazení prostředků v aplikacích .NET

Aplikace spoléhají na .NET Framework správce prostředků reprezentované <xref:System.Resources.ResourceManager> třídou pro načtení lokalizovaných prostředků. Správce prostředků předpokládá, že se k zabalení a nasazení prostředků používá model hub a paprsek. Centrum je hlavní sestavení, které obsahuje nelokalizovatelný spustitelný kód a prostředky pro jednu jazykovou verzi, označovanou jako neutrální nebo výchozí jazyková verze. Výchozí jazyková verze je záložní jazyková verze pro aplikaci. Jedná se o jazykovou verzi, jejíž prostředky se používají, pokud nelze nalézt lokalizované prostředky. Každý paprsek se připojuje k satelitnímu sestavení, které obsahuje prostředky pro jednu jazykovou verzi, ale neobsahuje žádný kód.

Tento model má několik výhod:

- Po nasazení aplikace můžete postupně přidávat prostředky pro nové kultury. Vzhledem k tomu, že následné nasazení prostředků specifických pro jazykovou verzi může vyžadovat značnou dobu, to vám umožní nejprve uvolnit hlavní aplikaci a později doručovat prostředky specifické pro jazykovou verzi.

- Můžete aktualizovat a změnit satelitní sestavení aplikace bez nutnosti opětovné kompilace aplikace.

- Aplikace potřebuje načíst pouze ta satelitní sestavení, která obsahují prostředky potřebné pro konkrétní jazykovou verzi. To může významně snížit používání systémových prostředků.

 Nicméně existují i nevýhody tohoto modelu:

- Je nutné spravovat více sad prostředků.

- Počáteční náklady na testování aplikace se zvyšují, protože je nutné testovat několik konfigurací. Všimněte si, že v dlouhodobém období bude jednodušší a levnější testovat jednu základní aplikaci s několika satelity, než testovat a udržovat několik paralelních mezinárodních verzí.

## <a name="resource-naming-conventions"></a>Zásady vytváření názvů prostředků

Když zabalíte prostředky vaší aplikace, je nutné je pojmenovat pomocí konvencí pojmenování prostředků, které modul CLR (Common Language Runtime) očekává. Modul runtime identifikuje prostředek podle názvu jeho jazykové verze. Každé jazykové verzi má jedinečný název, což je obvykle kombinace názvu jazykové verze s malým písmenem, která je přidružená k jazyku, a v případě potřeby se jedná o název subjazykové verze se dvěma písmeny, které jsou přidružené k zemi nebo oblasti. Název subjazykové verze následuje název jazykové verze oddělený spojovníkem (-). Mezi příklady patří ja-JP pro japonštinu, jak je popsáno v Japonsku, en-US pro angličtinu jako mluvené slovo v USA, de-DE pro němčinu, jak je popsáno v Německu, nebo de-AT pro němčinu jako mluvené slovo v Rakousku. Podívejte se na sloupec **značky jazyka** v [seznamu názvů jazyků nebo oblastí podporovaných systémem Windows](https://docs.microsoft.com/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c). Názvy jazykové verze se řídí standardem definovaným v [BCP 47](https://tools.ietf.org/html/bcp47).

> [!NOTE]
> Informace o vytváření souborů prostředků naleznete v tématu [vytváření souborů prostředků](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md) a [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md).

<a name="cpconpackagingdeployingresourcesanchor1"></a>

## <a name="the-resource-fallback-process"></a>Proces získávání náhradních prostředků

Model hub a paprsk pro balení a nasazování prostředků používá záložní proces k vyhledání odpovídajících prostředků. Pokud aplikace požaduje lokalizovaný prostředek, který není k dispozici, modul CLR (Common Language Runtime) prohledá hierarchii kultur pro příslušný záložní prostředek, který nejlépe odpovídá žádosti application's uživatele, a vyvolá výjimku pouze jako poslední možnost. Pokud je v každé úrovni hierarchie nalezen odpovídající prostředek, modul runtime ho použije. Pokud se prostředek nenajde, hledání pokračuje na další úrovni.

Chcete-li zlepšit výkon vyhledávání, <xref:System.Resources.NeutralResourcesLanguageAttribute> použijte atribut pro hlavní sestavení a předejte mu název neutrálního jazyka, který bude fungovat s vaším hlavním sestavením.

### <a name="net-framework-resource-fallback-process"></a>Proces záložního prostředku .NET Framework

Záložní proces .NET Framework prostředků zahrnuje následující kroky:

> [!TIP]
> Můžete použít [ \<relativeBindForResources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) konfiguračního prvku pro optimalizaci procesu záložního prostředku a procesu, pomocí kterého sondy modulu runtime pro sestavení prostředků. Další informace najdete v části [Optimalizace procesu pro použití náhradních prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing) .

1. Modul runtime nejprve zkontroluje [globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md) (GAC) pro sestavení, které odpovídá požadované jazykové verzi vaší aplikace.

     Globální mezipaměť sestavení (GAC) může ukládat sestavení prostředků, která jsou sdílena mnoha aplikacemi. Tím se zadarmo nebudete muset zahrnout konkrétní sady prostředků do adresářové struktury každé aplikace, kterou vytvoříte. Pokud modul runtime najde odkaz na sestavení, vyhledá v sestavení požadovaný prostředek. Pokud nalezne položku v sestavení, použije požadovaný prostředek. Pokud záznam nenajde, pokračuje v hledání.

2. Modul runtime Next zkontroluje adresář aktuálně spuštěného sestavení pro podadresář, který odpovídá požadované jazykové verzi. Pokud nalezne podadresář, vyhledá v podadresáři platné satelitní sestavení pro požadovanou jazykovou verzi. Modul runtime pak vyhledá satelitní sestavení pro požadovaný prostředek. Pokud nalezne prostředek v sestavení, použije ho. Pokud prostředek nenajde, pokračuje v hledání.

3. Modul runtime Next provede dotaz na Instalační služba systému Windows a určí, zda satelitní sestavení má být nainstalováno na vyžádání. Pokud ano, zpracuje instalaci, načte sestavení a vyhledá nebo dožádaný prostředek. Pokud nalezne prostředek v sestavení, použije ho. Pokud prostředek nenajde, pokračuje v hledání.

4. Modul runtime vyvolává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost, aby označovala, že není možné najít satelitní sestavení. Pokud se rozhodnete událost zpracovat, obslužná rutina události může vrátit odkaz na satelitní sestavení, jehož prostředky budou použity pro vyhledávání. V opačném případě se obslužná `null` rutina události vrátí a hledání pokračuje.

5. Modul runtime Next znovu vyhledá globální mezipaměť sestavení (GAC), tentokrát pro nadřazené sestavení požadované jazykové verze. Pokud nadřazené sestavení existuje v globální mezipaměti sestavení (GAC), modul runtime vyhledá požadované prostředky v sestavení.

     Nadřazená jazyková verze je definována jako vhodná záložní jazyková verze. Představte si rodiče jako náhradní kandidáty, protože poskytování jakýchkoli prostředků je vhodnější k vyvolání výjimky. Tento proces také umožňuje znovu použít prostředky. Konkrétní prostředek na nadřazené úrovni byste měli zahrnout pouze v případě, že podřízená jazyková verze nemusí lokalizovat požadovaný prostředek. Například `en` Pokud zadáte satelitní sestavení pro (neutrální angličtinu), `en-GB` (anglicky jako mluvené slovo ve Spojeném království) a `en-US` (anglicky `en` jako mluvené USA), by satelit obsahovala společný terminologie a satelity můžou poskytnout přepsání jenom pro ty, které se liší. `en-US` `en-GB`

6. Modul runtime dále kontroluje adresář aktuálně spuštěného sestavení, aby bylo možné zjistit, zda obsahuje nadřazený adresář. Pokud existuje nadřazený adresář, modul runtime v adresáři vyhledá platné satelitní sestavení pro nadřazenou jazykovou verzi. Pokud nalezne sestavení, modul runtime vyhledá požadované prostředky v sestavení. Pokud prostředek najde, použije ho. Pokud prostředek nenajde, pokračuje v hledání.

7. Modul runtime Next provede dotaz na Instalační služba systému Windows a určí, jestli se má na vyžádání nainstalovat nadřazené satelitní sestavení. Pokud ano, zpracuje instalaci, načte sestavení a vyhledá nebo dožádaný prostředek. Pokud nalezne prostředek v sestavení, použije ho. Pokud prostředek nenajde, pokračuje v hledání.

8. Modul runtime vyvolá <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost, která indikuje, že není schopen najít vhodný záložní prostředek. Pokud se rozhodnete událost zpracovat, obslužná rutina události může vrátit odkaz na satelitní sestavení, jehož prostředky budou použity pro vyhledávání. V opačném případě se obslužná `null` rutina události vrátí a hledání pokračuje.

9. Modul runtime dále hledá nadřazená sestavení, jako v předchozích třech krocích, a to prostřednictvím mnoha potenciálních úrovní. Každá jazyková verze má pouze jeden nadřazený prvek, který je definován <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> vlastností, ale nadřazený objekt může mít svůj vlastní nadřazený objekt. Hledání nadřazených kultur se zastaví, když se vrátí <xref:System.Globalization.CultureInfo.Parent%2A> <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>vlastnost jazykové verze; u záložního prostředku není neutrální jazyková verze považována za nadřazenou jazykovou verzi nebo jazykovou verzi, která může mít prostředky.

10. Pokud byla prohledána původně zadaná jazyková verze a všichni rodiče a prostředek stále nebyl nalezen, bude použit prostředek pro výchozí (záložní) jazykovou verzi. Prostředky pro výchozí jazykovou verzi jsou obvykle zahrnuty v sestavení Main aplikace. Můžete však zadat hodnotu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> pro vlastnost <xref:System.Resources.NeutralResourcesLanguageAttribute> atributu k označení, že konečné záložní umístění pro prostředky je satelitní sestavení, nikoli hlavní sestavení.

    > [!NOTE]
    > Výchozí prostředek je jediný prostředek, který může být zkompilován s hlavním sestavením. Pokud nezadáte satelitní sestavení pomocí <xref:System.Resources.NeutralResourcesLanguageAttribute> atributu, jedná se o konečnou zálohu (konečnou nadřazenou položku). Proto doporučujeme, abyste vždy zahrnuli výchozí sadu prostředků do hlavního sestavení. To pomáhá zabránit vyvolání výjimek. Zahrnutím výchozího prostředku se souborem zadáte zálohu pro všechny prostředky a zajistěte, aby měl uživatel vždy k dispozici alespoň jeden prostředek, a to i v případě, že není konkrétní kultura.

11. Nakonec, pokud modul runtime nenajde prostředek pro výchozí (záložní) jazykovou verzi, <xref:System.Resources.MissingManifestResourceException> je vyvolána výjimka nebo <xref:System.Resources.MissingSatelliteAssemblyException> , která označuje, že prostředek nebyl nalezen.

Předpokládejme například, že aplikace požaduje prostředek lokalizovaný pro španělštinu (Mexiko) ( `es-MX` jazyková verze). Modul runtime nejprve vyhledá globální mezipaměť sestavení (GAC) pro sestavení `es-MX`, které odpovídá, ale nenajde. Modul runtime pak vyhledá adresář aktuálně spuštěného sestavení pro `es-MX` adresář. V takovém případě modul runtime znovu vyhledá globální mezipaměť sestavení `es` (GAC) pro nadřazené sestavení, které odráží příslušnou záložní jazykovou verzi – v tomto případě (španělština). Pokud není nadřazené sestavení nalezeno, modul runtime vyhledá všechny potenciální úrovně nadřazených sestavení pro `es-MX` jazykovou verzi, dokud nenajde odpovídající prostředek. Pokud se prostředek nenajde, modul runtime použije prostředek pro výchozí jazykovou verzi.

<a name="Optimizing"></a>

#### <a name="optimizing-the-net-framework-resource-fallback-process"></a>Optimalizace procesu .NET Framework záložního prostředku

V následujících podmínkách můžete optimalizovat proces, podle kterého modul runtime vyhledává prostředky v satelitních sestaveních.

- Satelitní sestavení jsou nasazena ve stejném umístění jako sestavení kódu. Pokud je sestavení kódu nainstalováno v [globální mezipaměti sestavení (GAC](../../../docs/framework/app-domains/gac.md)), jsou satelitní sestavení nainstalována také v globální mezipaměti sestavení (GAC). Pokud je sestavení kódu nainstalováno v adresáři, jsou satelitní sestavení nainstalována ve složkách specifických pro jazykovou verzi tohoto adresáře.

- Satelitní sestavení nejsou na vyžádání nainstalována.

- Kód aplikace nezpracovává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost.

Optimalizujete sondu pro satelitní sestavení zahrnutím `enabled` `true` [ \<prvku relativeBindForResources >](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) a nastavením jeho atributu do konfiguračního souboru aplikace, jak je znázorněno v následujícím příkladu. případě.

```xml
<configuration>
   <runtime>
      <relativeBindForResources enabled="true" />
   </runtime>
</configuration>
```

Optimalizovaná sonda pro satelitní sestavení je funkce výslovného souhlasu. To znamená, že modul runtime postupuje podle kroků popsaných v [procesu záložního prostředku](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) , pokud `enabled` [ \<](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) se v konfiguračním souboru aplikace nenachází prvek relativeBindForResources > a jeho atribut je nastaven. na `true`. Pokud se jedná o tento případ, proces zjišťování pro satelitní sestavení se upraví takto:

- Modul runtime používá umístění nadřazeného sestavení kódu pro test satelitního sestavení. Pokud je nadřazené sestavení nainstalováno v globální mezipaměti sestavení (GAC), běhové testy v mezipaměti, ale ne v adresáři aplikace. Pokud je nadřazené sestavení nainstalováno v adresáři aplikace, sondy modulu runtime v adresáři aplikace, ale ne v globální mezipaměti sestavení (GAC).

- Modul runtime nedotazuje Instalační služba systému Windows pro instalaci satelitních sestavení na vyžádání.

- Pokud se sonda pro konkrétní sestavení prostředku nezdařila, modul runtime <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost nevyvolává.

### <a name="net-core-resource-fallback-process"></a>Záložní proces prostředků .NET Core

Záložní proces prostředku .NET Core zahrnuje následující kroky:

1. Modul runtime se pokusí načíst satelitní sestavení pro požadovanou jazykovou verzi.
     - Kontroluje adresář aktuálně spuštěného sestavení pro podadresář, který odpovídá požadované jazykové verzi. Pokud nalezne podadresář, vyhledá v podadresáři platné satelitní sestavení pro požadovanou jazykovou verzi a načte ji.

       > [!NOTE]
       > V operačních systémech se systémy souborů s rozlišováním velkých a malých písmen (tj. Linux a macOS) má hledání v podadresářích s názvem jazykové verze rozlišovat velká a malá písmena. Název podadresáře musí přesně odpovídat velikosti písmen <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> ( `es` například nebo `es-MX`).

       > [!NOTE]
       > Pokud programátor odvozuje vlastní kontext načtení sestavení z <xref:System.Runtime.Loader.AssemblyLoadContext>, je tato situace složitá. Pokud je spuštěné sestavení načteno do vlastního kontextu, modul runtime načte satelitní sestavení do vlastního kontextu. Podrobnosti jsou pro tento dokument mimo rozsah. Viz <xref:System.Runtime.Loader.AssemblyLoadContext>.

     - Pokud nebyla nalezena satelitní sestavení, <xref:System.Runtime.Loader.AssemblyLoadContext> <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> vyvolá událost, aby označovala, že není možné najít satelitní sestavení. Pokud se rozhodnete událost zpracovat, vaše obslužná rutina události může načíst a vrátit odkaz na satelitní sestavení.
     - Pokud satelitní sestavení ještě není nalezeno, AssemblyLoadContext způsobí, že doména AppDomain spustí <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost, aby označovala, že není možné najít satelitní sestavení. Pokud se rozhodnete událost zpracovat, vaše obslužná rutina události může načíst a vrátit odkaz na satelitní sestavení.

2. Pokud je nalezeno satelitní sestavení, modul runtime ho vyhledá u požadovaného prostředku. Pokud nalezne prostředek v sestavení, použije ho. Pokud prostředek nenajde, pokračuje v hledání.

     > [!NOTE]
     > Chcete-li najít prostředek v rámci satelitního sestavení, modul runtime vyhledá soubor prostředků požadovaný <xref:System.Resources.ResourceManager> pro aktuální. <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> V souboru prostředků vyhledá požadovaný název prostředku. Pokud buď není nalezen, bude prostředek považován za nenalezený.

3. Modul runtime Next prohledává sestavení nadřazené jazykové verze prostřednictvím mnoha potenciálních úrovní, pokaždé při opakování kroků 1 & 2.

     Nadřazená jazyková verze je definována jako vhodná záložní jazyková verze. Představte si rodiče jako náhradní kandidáty, protože poskytování jakýchkoli prostředků je vhodnější k vyvolání výjimky. Tento proces také umožňuje znovu použít prostředky. Konkrétní prostředek na nadřazené úrovni byste měli zahrnout pouze v případě, že podřízená jazyková verze nemusí lokalizovat požadovaný prostředek. Například `en` Pokud zadáte satelitní sestavení pro (neutrální angličtinu), `en-GB` (anglicky jako mluvené slovo ve Spojeném království) a `en-US` (anglicky `en` jako mluvené USA), satelit obsahuje společný terminologie a `en-GB` `en-US` satelity a jsou popsány pouze pro takové výrazy, které se liší.

     Každá jazyková verze má pouze jeden nadřazený prvek, který je definován <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> vlastností, ale nadřazený objekt může mít svůj vlastní nadřazený objekt. Hledání nadřazených jazykových verzí se zastaví, když se <xref:System.Globalization.CultureInfo.Parent%2A> vrátí <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>vlastnost jazykové verze. V případě záložního prostředku není neutrální jazyková verze považována za nadřazenou jazykovou verzi nebo jazykovou verzi, která může mít prostředky.

4. Pokud byla prohledána původně zadaná jazyková verze a všichni rodiče a prostředek stále nebyl nalezen, bude použit prostředek pro výchozí (záložní) jazykovou verzi. Prostředky pro výchozí jazykovou verzi jsou obvykle zahrnuty v sestavení Main aplikace. Můžete však zadat hodnotu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty.nameWithType> <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> vlastnosti, která označuje, že konečné záložní umístění pro prostředky je satelitní sestavení namísto hlavního sestavení.

    > [!NOTE]
    > Výchozí prostředek je jediný prostředek, který může být zkompilován s hlavním sestavením. Pokud nezadáte satelitní sestavení pomocí <xref:System.Resources.NeutralResourcesLanguageAttribute> atributu, jedná se o konečnou zálohu (konečnou nadřazenou položku). Proto doporučujeme, abyste vždy zahrnuli výchozí sadu prostředků do hlavního sestavení. To pomáhá zabránit vyvolání výjimek. Zahrnutím výchozího souboru prostředků zadáte zálohu pro všechny prostředky a zajistěte, aby byl uživatel vždy přítomen alespoň jeden prostředek, i když není konkrétní kultura.

5. Nakonec, pokud modul runtime nenajde soubor prostředků pro výchozí (záložní) jazykovou verzi, <xref:System.Resources.MissingManifestResourceException> je vyvolána výjimka nebo <xref:System.Resources.MissingSatelliteAssemblyException> , která označuje, že prostředek nebyl nalezen. Pokud se soubor prostředků najde, ale požadovaný prostředek není přítomen, požadavek se vrátí `null`.

### <a name="ultimate-fallback-to-satellite-assembly"></a>Ultimate Fallback do satelitního sestavení

Volitelně můžete odebrat prostředky z hlavního sestavení a určit, že modul runtime má načíst konečné záložní prostředky ze satelitního sestavení, které odpovídá konkrétní jazykové verzi. Chcete-li řídit záložní proces, použijte <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=nameWithType> konstruktor a zadejte hodnotu <xref:System.Resources.UltimateResourceFallbackLocation> parametru, který určuje, zda má správce prostředků extrahovat záložní prostředky z hlavního sestavení nebo satelitního sestavení.

Následující příklad .NET Framework používá <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut k uložení záložních prostředků aplikace do satelitního sestavení pro jazyk francouzštiny (`fr`). V příkladu jsou dva textové soubory prostředků, které definují jeden řetězec řetězce s názvem `Greeting`. První, Resources. fr. txt obsahuje prostředek francouzského jazyka.

```
Greeting=Bon jour!
```

Druhý, Resources, ru. txt, obsahuje prostředek ruského jazyka.

```
Greeting=Добрый день
```

Tyto dva soubory jsou zkompilovány do souborů. Resources spuštěním [generátoru souboru prostředků (Resgen. exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) z příkazového řádku. Pro zdroj francouzského jazyka je tento příkaz:

**resgen.exe resources.fr.txt**

Pro prostředek ruského jazyka je tento příkaz:

**Resgen. exe Resources. ru. txt**

Soubory. Resources jsou vloženy do knihoven DLL spuštěním [linkeru sestavení (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) z příkazového řádku pro zdroj francouzského jazyka následujícím způsobem:

**al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**

a pro prostředek ruského jazyka následujícím způsobem:

**Al/t: lib/embed: Resources. ru. Resources/Culture: ru/out: ru\Example1.resources.dll**

Zdrojový kód aplikace se nachází v souboru s názvem Example1.cs nebo priklad1. vb. Obsahuje <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut, který označuje, že výchozí prostředek aplikace je v podadresáři fr. Vytvoří instanci správce prostředků, načte hodnotu `Greeting` prostředku a zobrazí ho do konzoly.

[!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
[!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]

Zdrojový kód pak můžete C# zkompilovat z příkazového řádku následujícím způsobem:

```console
csc Example1.cs
```

Příkaz pro Visual Basic kompilátor je velmi podobný:

```console
vbc Example1.vb
```

Vzhledem k tomu, že v hlavním sestavení nejsou vloženy žádné prostředky, není nutné kompilovat pomocí `/resource` přepínače.

Pokud spustíte příklad ze systému, jehož jazyk je jiný než ruština, zobrazí se následující výstup:

```
Bon jour!
```

## <a name="suggested-packaging-alternative"></a>Navrhovaná alternativa k balení

Omezení času nebo rozpočtu vám mohou zabránit v vytváření sady prostředků pro každou podjazykovou verzi, kterou vaše aplikace podporuje. Místo toho můžete vytvořit jedno satelitní sestavení pro nadřazenou jazykovou verzi, kterou mohou používat všechny související subjazykové verze. Můžete například poskytnout jedno anglické satelitní sestavení (EN), které je načteno uživateli, kteří požadují České prostředky specifické pro oblast, a jedno německé satelitní sestavení (de) pro uživatele, kteří požadují německé prostředky specifické pro oblast. Například žádosti pro němčinu jako mluvené slovo v Německu (de-DE), Rakousko (de-AT) a Švýcarsko (de-CH) by se vrátily do německého satelitního sestavení (de). Výchozími prostředky jsou poslední záloha, proto by měly být prostředky, které bude požadovat většina uživatelů vaší aplikace, takže tyto prostředky pečlivě vybírejte. Tento přístup nasadí prostředky, které jsou méně kulturní, ale můžou významně snížit náklady na lokalizaci aplikace.

## <a name="see-also"></a>Viz také:

- [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
- [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)
- [Vytváření zdrojových souborů](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
