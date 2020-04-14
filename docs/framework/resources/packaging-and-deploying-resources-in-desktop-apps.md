---
title: Balení a nasazování prostředků v aplikacích .NET
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
ms.openlocfilehash: d64e3b5201e34541fdafa5724b0c7e8c3f6c0c0d
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243047"
---
# <a name="packaging-and-deploying-resources-in-net-apps"></a>Balení a nasazování prostředků v aplikacích .NET

Aplikace spoléhají na správce prostředků rozhraní .NET Framework, reprezentované třídou, <xref:System.Resources.ResourceManager> k načtení lokalizovaných prostředků. Správce prostředků předpokládá, že model rozbočovače a paprsku se používá k balení a nasazení prostředků. Rozbočovač je hlavní sestavení, které obsahuje nelokalizovatelný spustitelný kód a prostředky pro jednu jazykovou verzi, nazývanou neutrální nebo výchozí jazyková verze. Výchozí jazyková verze je záložní jazyková verze pro aplikaci; je to jazyková verze, jejíž prostředky se používají, pokud nelze nalézt lokalizované prostředky. Každý paprsek se připojí k satelitnímu sestavení, které obsahuje prostředky pro jednu jazykovou verzi, ale neobsahuje žádný kód.

Tento model má několik výhod:

- Po nasazení aplikace můžete postupně přidávat prostředky pro nové jazykové verze. Vzhledem k tomu, že následný vývoj prostředků specifických pro jazykovou verzi může vyžadovat značné množství času, to umožňuje nejprve uvolnit hlavní aplikaci a později dodat prostředky specifické pro jazykovou verzi.
- Satelitní sestavení aplikace můžete aktualizovat a měnit bez nutnosti opětovné kompilace aplikace.
- Aplikace musí načíst pouze satelitní sestavení, které obsahují prostředky potřebné pro konkrétní jazykovou verzi. To může výrazně snížit využití systémových prostředků.

 Existují však také nevýhody tohoto modelu:

- Je nutné spravovat více sad prostředků.
- Počáteční náklady na testování aplikace se zvyšují, protože je nutné otestovat několik konfigurací. Všimněte si, že v dlouhodobém horizontu bude jednodušší a levnější testovat jednu základní aplikaci s několika satelity, než testovat a udržovat několik paralelních mezinárodních verzí.

## <a name="resource-naming-conventions"></a>Konvence pro pojmenování prostředků

Při balení prostředků aplikace, musíte je pojmenovat pomocí konvencí pojmenování prostředků, které očekává běžný jazyk runtime. Runtime identifikuje prostředek podle jeho názvu jazykové verze. Každá jazyková verze má jedinečný název, což je obvykle kombinace dvoupísmenného názvu jazykové verze s ložených písmenem a v případě potřeby dvoupísmenného názvu subkultury s velkými písmeny přidruženými k zemi nebo oblasti. Název subkultury následuje název jazykové verze, oddělený pomlčkou (-). Příklady zahrnují ja-JP pro japonštinu, jak se mluví v Japonsku, en-US pro angličtinu, jak se mluví ve Spojených státech, de-DE pro němčinu, jak se mluví v Německu, nebo de-AT pro němčinu, jak se mluví v Rakousku. Viz sloupec **Language tag** v seznamu názvů jazyků nebo [oblastí podporovaných systémem Windows](https://docs.microsoft.com/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c). Názvy kultur postupujte podle standardu definovaného [bcp 47](https://tools.ietf.org/html/bcp47).

> [!NOTE]
> Existují některé výjimky pro názvy jazykové verze `zh-Hans` se dvěma písmeny, například pro čínštinu (zjednodušená).

> [!NOTE]
> Informace o vytváření souborů prostředků naleznete v [tématu Vytváření souborů prostředků](creating-resource-files-for-desktop-apps.md) a [Vytváření satelitních sestavení](creating-satellite-assemblies-for-desktop-apps.md).

<a name="cpconpackagingdeployingresourcesanchor1"></a>

## <a name="the-resource-fallback-process"></a>Proces získávání náhradních prostředků

Model rozbočovače a paprsku pro balení a nasazování prostředků používá záložní proces k vyhledání vhodných prostředků. Pokud aplikace požaduje lokalizovaný prostředek, který není k dispozici, soubor RUNTIME společného jazyka vyhledá hierarchii jazykových verzí pro vhodný záložní prostředek, který nejvíce odpovídá požadavku aplikace uživatele a vyvolá výjimku pouze jako poslední možnost. Na každé úrovni hierarchie, pokud je nalezen příslušný prostředek, jej používá za běhu. Pokud zdroj není nalezen, hledání pokračuje na další úrovni.

Chcete-li zlepšit výkon <xref:System.Resources.NeutralResourcesLanguageAttribute> vyhledávání, použijte atribut pro hlavní sestavení a předejte mu název neutrálního jazyka, který bude pracovat s hlavním sestavením.

### <a name="net-framework-resource-fallback-process"></a>Záložní proces prostředků rozhraní .NET Framework

Záložní proces prostředků rozhraní .NET Framework zahrnuje následující kroky:

> [!TIP]
> Je možné použít [ \<relativníBindForResources>](../configure-apps/file-schema/runtime/relativebindforresources-element.md) konfigurační prvek pro optimalizaci procesu záložní prostředky a proces, kterým runtime sondy pro sestavení prostředků. Další informace naleznete v části [Optimalizace záložního procesu prostředků.](packaging-and-deploying-resources-in-desktop-apps.md#Optimizing)

1. Za běhu nejprve zkontroluje [globální mezipaměti sestavení](../app-domains/gac.md) pro sestavení, které odpovídá požadované jazykové verze pro vaši aplikaci.

     Globální mezipaměť sestavení může ukládat sestavení prostředků, která jsou sdílena mnoha aplikacemi. Tím osvobozujete nutnost zahrnout konkrétní sady prostředků do adresářové struktury každé aplikace, kterou vytvoříte. Pokud za běhu najde odkaz na sestavení, prohledá sestavení pro požadovaný prostředek. Pokud najde položku v sestavení, použije požadovaný prostředek. Pokud položku nenajde, pokračuje v hledání.

2. Modul runtime next zkontroluje adresář aktuálně spuštěného sestavení pro podadresář, který odpovídá požadované jazykové verzi. Pokud najde podadresář, vyhledá v tomto podadresáři platné satelitní sestavení pro požadovanou jazykovou verzi. Za běhu pak vyhledá satelitní sestavení pro požadovaný prostředek. Pokud najde prostředek v sestavení, použije jej. Pokud zdroj nenajde, bude pokračovat v hledání.

3. Další runtime se dotazuje Instalační služby systému Windows k určení, zda má být satelitní sestavení nainstalováno na vyžádání. Pokud ano, zpracovává instalaci, načte sestavu a prohledává ji nebo požadovaný prostředek. Pokud najde prostředek v sestavení, použije jej. Pokud zdroj nenajde, bude pokračovat v hledání.

4. Runtime vyvolá <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost označující, že není schopen najít satelitní sestavení. Pokud se rozhodnete zpracovat událost, obslužná rutina události může vrátit odkaz na satelitní sestavení, jehož prostředky budou použity pro vyhledávání. V opačném případě `null` se vrátí obslužná rutina události a hledání pokračuje.

5. Další čas běhu znovu prohledá globální mezipaměť sestavení, tentokrát pro nadřazené sestavení požadované jazykové verze. Pokud nadřazené sestavení existuje v globální mezipaměti sestavení, za běhu vyhledá sestavení pro požadovaný prostředek.

     Nadřazená jazyková verze je definována jako příslušná záložní jazyková verze. Zvažte rodiče jako záložní kandidáty, protože poskytnutí jakéhokoli prostředku je vhodnější pro vyvolání výjimky. Tento proces také umožňuje znovu použít prostředky. Konkrétní prostředek byste měli zahrnout na nadřazenou úroveň pouze v případě, že podřízená jazyková verze nepotřebuje lokalizovat požadovaný prostředek. Například pokud zadáte satelitní sestavení `en` `en-GB` pro (neutrální angličtina), (anglicky, `en-US` jak se mluví ve Spojeném `en` království) a (anglicky, `en-GB` `en-US` jak se mluví ve Spojených státech), satelit by obsahovat společnou terminologii a a satelity by mohly poskytnout přepsání pouze pro ty termíny, které se liší.

6. Další modul runtime zkontroluje adresář aktuálně spuštěného sestavení a zjistí, zda obsahuje nadřazený adresář. Pokud nadřazený adresář existuje, za běhu vyhledá v adresáři platné satelitní sestavení pro nadřazenou jazykovou verzi. Pokud najde sestavení, za běhu hledá sestavení pro požadovaný prostředek. Pokud najde prostředek, použije jej. Pokud zdroj nenajde, bude pokračovat v hledání.

7. Další runtime se dotazuje Instalační služby systému Windows k určení, zda má být nadřazené satelitní sestavení nainstalováno na vyžádání. Pokud ano, zpracovává instalaci, načte sestavu a prohledává ji nebo požadovaný prostředek. Pokud najde prostředek v sestavení, použije jej. Pokud zdroj nenajde, bude pokračovat v hledání.

8. Runtime vyvolá <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost označující, že není schopen najít vhodný záložní prostředek. Pokud se rozhodnete zpracovat událost, obslužná rutina události může vrátit odkaz na satelitní sestavení, jehož prostředky budou použity pro vyhledávání. V opačném případě `null` se vrátí obslužná rutina události a hledání pokračuje.

9. Další runtime hledá nadřazená sestavení, stejně jako v předchozích třech krocích, prostřednictvím mnoha potenciálních úrovní. Každá jazyková verze má pouze jeden <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> nadřazený, který je definován vlastností, ale nadřazený může mít svůj vlastní nadřazený. Hledání nadřazené jazykové verze <xref:System.Globalization.CultureInfo.Parent%2A> zastaví, <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>když vrátí vlastnost jazykové verze ; pro záložní prostředek invariantní jazyková verze není považována za nadřazenou jazykovou verzi nebo jazykovou verzi, která může mít prostředky.

10. Pokud jazyková verze, která byla původně zadána a všechny rodiče byly prohledány a prostředek stále nebyl nalezen, zdroj pro výchozí (záložní) jazyková verze se používá. Prostředky pro výchozí jazykovou verzi jsou obvykle zahrnuty v sestavení hlavní aplikace. Můžete však zadat hodnotu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> vlastnosti <xref:System.Resources.NeutralResourcesLanguageAttribute> atributu, která označuje, že konečné záložní umístění prostředků je satelitní sestavení, nikoli hlavní sestavení.

    > [!NOTE]
    > Výchozí prostředek je jediný prostředek, který lze zkompilovat s hlavním sestavením. Pokud nezadáte satelitní sestavení <xref:System.Resources.NeutralResourcesLanguageAttribute> pomocí atributu, je konečným záložní (poslední nadřazený). Proto doporučujeme vždy zahrnout výchozí sadu prostředků v hlavním sestavení. To pomáhá zabránit vyvolání výjimek. Zahrnutím výchozího prostředku soubor uvedete záložní pro všechny prostředky a zajistíte, že alespoň jeden prostředek je vždy k dispozici pro uživatele, i když není kulturně specifické.

11. Nakonec pokud runtime nenajde prostředek pro výchozí (záložní) jazykovou <xref:System.Resources.MissingManifestResourceException> verzi, nebo <xref:System.Resources.MissingSatelliteAssemblyException> je vyvolána výjimka označující, že prostředek nebyl nalezen.

Předpokládejme například, že aplikace požaduje prostředek lokalizovaný `es-MX` pro španělštinu (Mexiko) (jazykovou verzi). Za běhu nejprve vyhledá globální mezipaměti sestavení `es-MX`pro sestavení, které odpovídá , ale nenajde ji. Modul runtime pak prohledá adresář aktuálně spuštěného `es-MX` sestavení pro adresář. V opačném případě za běhu znovu vyhledá globální mezipaměti sestavení pro nadřazené sestavení, které odráží příslušnou záložní jazykovou verzi – v tomto případě `es` (španělština). Pokud nadřazené sestavení není nalezeno, za běhu vyhledá všechny `es-MX` potenciální úrovně nadřazených sestavení pro jazykovou verzi, dokud nenajde odpovídající prostředek. Pokud prostředek není nalezen, za běhu používá prostředek pro výchozí jazykovou verzi.

<a name="Optimizing"></a>

#### <a name="optimizing-the-net-framework-resource-fallback-process"></a>Optimalizace procesu záložního prostředku rozhraní .NET Framework

Za následujících podmínek můžete optimalizovat proces, kterým za běhu vyhledává prostředky v satelitních sestaveních.

- Satelitní sestavení jsou nasazeny ve stejném umístění jako sestavení kódu. Pokud je sestavení kódu nainstalováno v [globální mezipaměti sestavení](../app-domains/gac.md), satelitní sestavení jsou také nainstalována v globální mezipaměti sestavení. Pokud je sestavení kódu nainstalováno v adresáři, satelitní sestavení jsou nainstalována ve složkách tohoto adresáře specifických pro jazykovou verzi.

- Satelitní sestavení nejsou nainstalována na vyžádání.

- Kód aplikace nezpracovává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost.

Optimalizovat sondu pro satelitní sestavení zahrnutím [ \<relativeBindForResources>](../configure-apps/file-schema/runtime/relativebindforresources-element.md) `enabled` prvek `true` a nastavení jeho atribut v konfiguračním souboru aplikace, jak je znázorněno v následujícím příkladu.

```xml
<configuration>
   <runtime>
      <relativeBindForResources enabled="true" />
   </runtime>
</configuration>
```

Optimalizovaná sonda pro satelitní sestavení je funkce opt-in. To znamená, že runtime následuje kroky zdokumentované v [procesu záložní prostředek,](packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1) pokud [ \<relativníBindForResources>](../configure-apps/file-schema/runtime/relativebindforresources-element.md) `enabled` prvek je `true`přítomen v konfiguračním souboru aplikace a jeho atribut je nastaven na . Pokud se jedná o tento případ, proces sondování pro satelitní sestavení se změní takto:

- Runtime používá umístění sestavení nadřazeného kódu ke sondování pro satelitní sestavení. Pokud je nadřazené sestavení nainstalováno v globální mezipaměti sestavení, runtime sonduje v mezipaměti, ale ne v adresáři aplikace. Pokud je nadřazené sestavení nainstalováno v adresáři aplikace, runtime sonduje v adresáři aplikace, ale ne v globální mezipaměti sestavení.

- Za běhu není dotaz Instalační služby systému Windows pro instalaci satelitních sestavení na vyžádání.

- Pokud sonda pro sestavení určitého prostředku selže, za <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> běhu nevyvolá událost.

### <a name="net-core-resource-fallback-process"></a>Záložní proces prostředků jádra .NET

Záložní proces prostředku .NET Core zahrnuje následující kroky:

1. Za běhu se pokusí načíst satelitní sestavení pro požadovanou jazykovou verzi.
     - Zkontroluje adresář aktuálně spuštěného sestavení pro podadresář, který odpovídá požadované jazykové verzi. Pokud najde podadresář, vyhledá v tomto podadresáři platné satelitní sestavení pro požadovanou jazykovou verzi a načte ji.

       > [!NOTE]
       > V operačních systémech se systémy souborů rozlišujícími malá a velká písmena (tj. Linux a macOS) je hledání názvu jazykové verze rozlišováno. Název podadresáře se musí přesně <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> shodovat s případem (například `es` nebo). `es-MX`

       > [!NOTE]
       > Pokud programátor odvodil vlastní kontext <xref:System.Runtime.Loader.AssemblyLoadContext>zatížení sestavení z , situace je komplikovaná. Pokud spuštění sestavení byla načtena do vlastního kontextu, modul runtime načte satelitní sestavení do vlastního kontextu. Podrobnosti jsou mimo rozsah pro tento dokument. Viz <xref:System.Runtime.Loader.AssemblyLoadContext>.

     - Pokud nebyla nalezena satelitní <xref:System.Runtime.Loader.AssemblyLoadContext> sestava, <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> vyvolá událost, která označuje, že není schopna najít satelitní sestavení. Pokud se rozhodnete zpracovat událost, obslužná rutina události můžete načíst a vrátit odkaz na satelitní sestavení.
     - Pokud satelitní sestavení stále nebyl nalezen, AssemblyLoadContext způsobí AppDomain <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> aktivovat událost označující, že není schopen najít satelitní sestavení. Pokud se rozhodnete zpracovat událost, obslužná rutina události můžete načíst a vrátit odkaz na satelitní sestavení.

2. Pokud je nalezeno satelitní sestavení, za běhu vyhledá požadovaný prostředek. Pokud najde prostředek v sestavení, použije jej. Pokud zdroj nenajde, bude pokračovat v hledání.

     > [!NOTE]
     > Chcete-li najít prostředek v satelitním sestavení, hledá za běhu <xref:System.Resources.ResourceManager> soubor <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>prostředků požadovaný pro aktuální . V souboru prostředků vyhledá požadovaný název prostředku. Pokud buď nebyl nalezen, prostředek je považován za nebyl nalezen.

3. Další runtime prohledává nadřazená sestavení jazykové verze prostřednictvím mnoha potenciálních úrovní, pokaždé, když opakuje kroky 1 & 2.

     Nadřazená jazyková verze je definována jako odpovídající záložní jazyková verze. Zvažte rodiče jako záložní kandidáty, protože poskytnutí jakéhokoli prostředku je vhodnější pro vyvolání výjimky. Tento proces také umožňuje znovu použít prostředky. Konkrétní prostředek byste měli zahrnout na nadřazenou úroveň pouze v případě, že podřízená jazyková verze nepotřebuje lokalizovat požadovaný prostředek. Například pokud zadáte satelitní sestavení `en` `en-GB` pro (neutrální angličtina), (anglicky, `en-US` jak se mluví ve Spojeném `en` království) a (anglicky, jak se mluví ve Spojených státech), satelit obsahuje společnou terminologii a `en-GB` `en-US` a satelity poskytuje přepsání pouze pro ty termíny, které se liší.

     Každá jazyková verze má pouze jeden <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> nadřazený, který je definován vlastností, ale nadřazený může mít svůj vlastní nadřazený. Hledání nadřazené jazykové verze <xref:System.Globalization.CultureInfo.Parent%2A> se <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>zastaví, když vrátí vlastnost jazykové verze . Pro záložní prostředek invariantní jazyková verze není považována za nadřazenou jazykovou verzi nebo jazykovou verzi, která může mít prostředky.

4. Pokud jazyková verze, která byla původně zadána a všechny rodiče byly prohledány a prostředek stále nebyl nalezen, zdroj pro výchozí (záložní) jazyková verze se používá. Prostředky pro výchozí jazykovou verzi jsou obvykle zahrnuty v sestavení hlavní aplikace. Můžete však zadat hodnotu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty.nameWithType> <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> vlastnosti, která označuje, že konečné záložní umístění prostředků je satelitní sestavení spíše než hlavní sestavení.

    > [!NOTE]
    > Výchozí prostředek je jediný prostředek, který lze zkompilovat s hlavním sestavením. Pokud nezadáte satelitní sestavení <xref:System.Resources.NeutralResourcesLanguageAttribute> pomocí atributu, je konečným záložní (poslední nadřazený). Proto doporučujeme vždy zahrnout výchozí sadu prostředků v hlavním sestavení. To pomáhá zabránit vyvolání výjimek. Zahrnutím výchozího souboru prostředků poskytnete záložní informace pro všechny prostředky a zajistíte, že alespoň jeden prostředek je pro uživatele vždy k dispozici, i když není kulturně specifický.

5. Nakonec pokud runtime nenajde soubor prostředků pro výchozí (záložní) jazykovou <xref:System.Resources.MissingManifestResourceException> <xref:System.Resources.MissingSatelliteAssemblyException> verzi, nebo je vyvolána výjimka označující, že prostředek nebyl nalezen. Pokud je soubor prostředků nalezen, ale požadovaný prostředek `null`není přítomen požadavek vrátí .

### <a name="ultimate-fallback-to-satellite-assembly"></a>Ultimate Fallback na satelitní montáž

Volitelně můžete odebrat prostředky z hlavního sestavení a určit, že runtime by měl načíst konečné záložní prostředky ze satelitního sestavení, které odpovídá určité jazykové verzi. Chcete-li řídit záložní proces, <xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29> použijte konstruktor a <xref:System.Resources.UltimateResourceFallbackLocation> zajistěte hodnotu parametru, který určuje, zda má Správce prostředků extrahovat záložní prostředky z hlavního sestavení nebo ze satelitního sestavení.

Následující příklad rozhraní .NET <xref:System.Resources.NeutralResourcesLanguageAttribute> Framework používá atribut k uložení záložních prostředků aplikace`fr`v satelitním sestavení pro francouzský jazyk ( ). Příklad má dva soubory prostředků založené na textu, `Greeting`které definují jeden řetězec prostředku s názvem . První, resources.fr.txt, obsahuje prostředek francouzského jazyka.

```text
Greeting=Bon jour!
```

Druhý, resources,ru.txt, obsahuje prostředek ruského jazyka.

```text
Greeting=Добрый день
```

Tyto dva soubory jsou kompilovány do souborů .resources spuštěním [generátoru souborů prostředků (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) z příkazového řádku. Pro prostředek francouzského jazyka je příkaz:

**resgen.exe resources.fr.txt**

Pro prostředek ruského jazyka je příkaz:

**resgen.exe resources.ru.txt**

Soubory .resources jsou vloženy do knihoven dynamických odkazů spuštěním [propojovacího systému sestavení (Al.exe)](../tools/al-exe-assembly-linker.md) z příkazového řádku pro prostředek francouzského jazyka následujícím způsobem:

**al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**

a pro ruský jazyk zdroj takto:

**al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**

Zdrojový kód aplikace se nachází v souboru s názvem Example1.cs nebo Example1.vb. Obsahuje <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut označující, že výchozí prostředek aplikace je v podadresáři fr. Konkretně instancí Správce prostředků, `Greeting` načte hodnotu prostředku a zobrazí jej do konzoly.

[!code-csharp[Conceptual.Resources.Packaging#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)]
[!code-vb[Conceptual.Resources.Packaging#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]

Potom můžete zkompilovat zdrojový kód jazyka C# z příkazového řádku následujícím způsobem:

```console
csc Example1.cs
```

Příkaz pro kompilátor jazyka je velmi podobný:

```console
vbc Example1.vb
```

Vzhledem k tomu, že v hlavním sestavení nejsou vloženy `/resource` žádné prostředky, není třeba zkompilovat pomocí přepínače.

Při spuštění příkladu ze systému, jehož jazyk je něco jiného než ruština, zobrazí následující výstup:

```output
Bon jour!
```

## <a name="suggested-packaging-alternative"></a>Doporučená alternativa balení

Časová nebo rozpočtová omezení vám mohou bránit ve vytváření sady prostředků pro každou subkulturu, kterou vaše aplikace podporuje. Místo toho můžete vytvořit jedno satelitní sestavení pro nadřazenou jazykovou verzi, kterou mohou používat všechny související subkultury. Můžete například zadat jedno anglické satelitní sestavení (en), které je načteno uživateli, kteří požadují anglické prostředky specifické pro oblast, a jedno německé satelitní sestavení (de) pro uživatele, kteří požadují německé prostředky specifické pro oblast. Například požadavky na němčinu, jak se mluví v Německu (de-DE), Rakousku (de-AT) a Švýcarsku (de-CH), by se vrátily do německého satelitního sestavení (de). Výchozí prostředky jsou konečné záložní a proto by měly být prostředky, které budou požadovány většinou uživatelů aplikace, takže pečlivě zvolte tyto prostředky. Tento přístup nasazuje prostředky, které jsou méně kulturně specifické, ale může výrazně snížit náklady na lokalizaci vaší aplikace.

## <a name="see-also"></a>Viz také

- [Prostředky v aplikacích klasické pracovní plochy](index.md)
- [Globální mezipaměť sestavení](../app-domains/gac.md)
- [Vytváření zdrojových souborů](creating-resource-files-for-desktop-apps.md)
- [Vytváření satelitních sestavení](creating-satellite-assemblies-for-desktop-apps.md)
