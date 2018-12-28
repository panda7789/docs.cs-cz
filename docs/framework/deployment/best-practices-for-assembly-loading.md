---
title: Doporučené postupy pro načtení sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies,binding
- LoadFrom method
- default load context
- TypeLoadException class,causes
- assembly loading errors
- load contexts
- assemblies,loading
- LoadWithPartialName method
- load-from context
ms.assetid: 68d1c539-6a47-4614-ab59-4b071c9d4b4c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f7aa8a57fce9382cb67327e69048c2b05bb99da
ms.sourcegitcommit: 49af435bfdd41faf26d38c20c5b0cc07e87bea60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2018
ms.locfileid: "53397043"
---
# <a name="best-practices-for-assembly-loading"></a>Doporučené postupy pro načtení sestavení
Tento článek popisuje způsoby, jak se vyhnout problémům identity typu, který může mít za následek <xref:System.InvalidCastException>, <xref:System.MissingMethodException>a další chyby. Tento článek popisuje následující doporučení:  
  
-   [Porozumět výhodám a nevýhodám načtení kontextů](#load_contexts)  
  
-   [Vyhněte se vazby pro sestavení částečné názvy](#avoid_partial_names)  
  
-   [Vyhněte se načítání sestavení do více kontextů](#avoid_loading_into_multiple_contexts)  
  
-   [Vyhněte se načítání více verzí sestavení do stejného kontextu](#avoid_loading_multiple_versions)  
  
-   [Zvažte možnost Výchozí kontext načtení](#switch_to_default)  
  
 První doporučení [porozumět výhodám a nevýhodám zatížení kontexty](#load_contexts), poskytuje základní informace pro další doporučení, protože jsou všechny závislé na znalost kontextu zatížení.  
  
<a name="load_contexts"></a>   
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Porozumět výhodám a nevýhodám načtení kontextů  
 V rámci domény aplikace sestavení lze načíst do jedné ze tří kontexty nebo mohou být načteny bez kontextu:  
  
-   Výchozím kontextu načtení obsahuje sestavení zjištěných aplikací globální mezipaměti sestavení, úložiště sestavení hostitele, pokud je hostitelem modulu runtime (například v systému SQL Server), zjišťování a <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A> domény aplikace. Většina přetížení <xref:System.Reflection.Assembly.Load%2A> metoda zatížení sestavení v tomto kontextu.  
  
-   Načtení z kontextu obsahuje sestavení, která jsou načtena z umístění, které se neprohledávají zavaděčem. Doplňky například může být nainstalováno v adresáři, který není v cestě aplikace. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>, a <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> jsou příklady metod, které načítají podle cesty.  
  
-   Kontextu pouze pro reflexi obsahuje sestavení načtená <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> a <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody. Kód v tomto kontextu nelze provést, takže tady není probíraná. Další informace najdete v tématu [jak: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
-   Pokud jste vygenerovali přechodné dynamické sestavení pomocí reflexe generování, sestavení není v libovolném kontextu. Kromě toho většina sestavení, která jsou načtena pomocí <xref:System.Reflection.Assembly.LoadFile%2A> metody jsou načteny bez kontextu a sestavení, která jsou načtena z bajtových polí jsou načteny bez kontextu, pokud svoji identitu (po zásada) zjistí, že jsou v globální mezipaměti sestavení.  
  
 Kontexty spuštění mají své výhody a nevýhody, jak je popsáno v následujících částech.  
  
### <a name="default-load-context"></a>Výchozí kontext načtení  
 Jsou-li sestavení načteno do výchozím kontextu načtení, se automaticky načtou jejich závislosti. Závislosti, které se načtou do výchozí kontext načtení pro sestavení ve výchozím kontextu načtení nebo načtení z kontextu nebyly nalezeny automaticky. Načítání podle identity sestavení zvyšuje stability aplikacím tím, že zajišťuje, že nejsou použity Neznámá verze sestavení (najdete v článku [vyhnout vazby na částečné názvy sestavení](#avoid_partial_names) části).  
  
 Použití výchozího kontextu zatížení má následující nevýhody:  
  
-   Závislosti, které jsou načteny v jiných kontextech nejsou k dispozici.  
  
-   Nelze načíst sestavení z umístění mimo cesta zjišťování do výchozím kontextu načtení.  
  
### <a name="load-from-context"></a>Načtení z kontextu  
 Načtení z kontextu umožňuje načíst sestavení z cesty, které nejsou v rámci cesty aplikace a proto není zahrnut v zjišťování. Umožňuje závislosti umístěné a načíst z této cesty, protože kontext udržuje informace o cestě. Kromě toho sestavení v tomto kontextu můžete použít závislosti, které jsou načteny v kontextu načtení výchozí.  
  
 Načítání sestavení s použitím <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metoda nebo jednu z metod, které načítají podle cesty, má následující nevýhody:  
  
-   Pokud sestavení se stejnou identitou je již načten, <xref:System.Reflection.Assembly.LoadFrom%2A> vrátí načtené sestavení, i v případě, že byl zadán jinou cestu.  
  
-   Pokud je sestavení načteno s <xref:System.Reflection.Assembly.LoadFrom%2A>a později pokusí načíst stejné sestavení podle zobrazovaného názvu sestavení ve výchozím kontextu načtení, neúspěšného pokusu o načtení. Tato situace může nastat, když je deserializovat sestavení.  
  
-   Pokud je sestavení načteno s <xref:System.Reflection.Assembly.LoadFrom%2A>, a cesta zjišťování zahrnuje sestavení se stejnou identitou, ale v jiném umístění, <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, nebo jiné neočekávané chování může dojít.  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A> požadavky na <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> a <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>, nebo <xref:System.Net.WebPermission>, na zadané cestě.  
  
-   Pokud nativní bitovou kopii pro sestavení existuje, se nepoužívá.  
  
-   Sestavení nelze načteno jako doménově neutrální.  
  
-   V rozhraní .NET Framework verze 1.0 a 1.1 zásady se neuplatní.  
  
### <a name="no-context"></a>Žádný kontext.  
 Načítají se bez kontextu je jedinou možností pro přechodný sestavení, které jsou generovány pomocí reflexe vysílat. Načítání bez kontextu je jediný způsob, jak načítat více sestavení, které mají stejnou identitu do jeden aplikační domény. Náklady na zjišťování je vyloučeno.  
  
 Sestavení, která jsou načtena z bajtových polí jsou načteny bez kontextu, pokud identitu sestavení, který se stanoví při použití zásad, odpovídá identitě sestavení v globální mezipaměti sestavení; v takovém případě je načteno sestavení z globální mezipaměti sestavení.  
  
 Načítání sestavení bez kontextu má následující nevýhody:  
  
-   Jiná sestavení nelze vytvořit vazbu sestavení, která jsou načtena bez kontextu, pokud zpracováváte <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.  
  
-   Závislosti nejsou načteny automaticky. Přednačtení bez kontextu, přednačtení do výchozím kontextu načtení nebo načíst pomocí manipulace <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.  
  
-   Načítání více sestavení se stejnou identitou bez kontextu může způsobit problémy identity typu podobné těm, které jsou způsobené načítání sestavení se stejnou identitou do více kontextů. Zobrazit [předejít sestavení do více kontextů](#avoid_loading_into_multiple_contexts).  
  
-   Pokud nativní bitovou kopii pro sestavení existuje, se nepoužívá.  
  
-   Sestavení nelze načteno jako doménově neutrální.  
  
-   V rozhraní .NET Framework verze 1.0 a 1.1 zásady se neuplatní.  
  
<a name="avoid_partial_names"></a>   
## <a name="avoid-binding-on-partial-assembly-names"></a>Vyhněte se vazby pro sestavení částečné názvy  
 Částečný název vazby nastane, pokud zadáte pouze část zobrazovaného názvu sestavení (<xref:System.Reflection.Assembly.FullName%2A>) při načtení sestavení. Například můžete volat <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodu s jednoduchý název sestavení, vynechání verze, jazykovou verzi a token veřejného klíče. Nebo může volat <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metody, které první volání <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda a pokud selže k nalezení sestavení, hledá globální mezipaměti sestavení a načte nejnovější verzi sestavení, která je k dispozici.  
  
 Částečný název vazby může způsobit, že mnoho problémů, včetně následujících:  
  
-   <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> Metoda může načíst odlišné sestavení se stejným jednoduchým názvem. Dvě aplikace může například nainstalovat dvě zcela odlišné sestavení, obě mají jednoduchý název `GraphicsLibrary` do globální mezipaměti sestavení.  
  
-   Sestavení, které je ve skutečnosti načteno nemusí být zpětně kompatibilní. Například bez zadání verze může způsobit načítání mnohem novější než verze, že váš program byl původně zapsán používat. Změny v novější verzi může způsobit chyby v aplikaci.  
  
-   Sestavení, které je ve skutečnosti načteno nemusí být dopřednou. Například je může mít sestaví a otestují vaši aplikaci s nejnovější verzí sestavení, ale částečné vazbě může načíst mnohem starší verzi, která nemá funkce, které vaše aplikace používá.  
  
-   Instalace nové aplikace může dojít k narušení stávající aplikace. Aplikace, která se používá <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metoda může být porušena nainstalovat novější, nekompatibilní verzi sdílené sestavení.  
  
-   Může dojít k načítání neočekávané závislostí. Ho načtete dvě sestavení tuto sdílenou složku, závislostí, načtení se částečné vazbě může mít za následek jedno sestavení pomocí komponenty, která nebyla sestavené nebo otestované s.  
  
 Z důvodu problémů, může to způsobit <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metoda má byla označena jako zastaralá. Doporučujeme použít <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda místo a zadejte úplný sestavení zobrazované názvy. Zobrazit [porozumět výhodám a nevýhodám kontexty zatížení](#load_contexts) a [zvažte možnost výchozím kontextu načtení](#switch_to_default).  
  
 Pokud chcete použít <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metoda totiž sestavení načítání snadné, vezměte v úvahu, že vaše aplikace selhat s chybovou zprávou, která identifikuje chybějící sestavení by mohla poskytovat lepší výkon než automaticky pomocí Neznámá verze sestavení, což by mohlo způsobit nepředvídatelné chování a bezpečnostní díry.  
  
<a name="avoid_loading_into_multiple_contexts"></a>   
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Vyhněte se načítání sestavení do více kontextů  
 Načtení sestavení do více kontextů může způsobovat problémy identity typu. Pokud stejný typ načten ze stejného sestavení do dvou různých kontextů, je to, jako kdyby měla byly načteny dva různé typy se stejným názvem. <xref:System.InvalidCastException> Je vyvolána, pokud se pokusíte převést jednoho typu na druhý matoucí zprávou, která zadejte `MyType` nejde přetypovat na typ `MyType`.  
  
 Předpokládejme například, že `ICommunicate` rozhraní je deklarován v sestavení s názvem `Utility`, který se odkazuje váš program a také další sestavení, která načte aplikaci. Tato sestavení obsahují typy, které implementují `ICommunicate` rozhraní, umožňuje váš program k jejich použití.  
  
 Teď se podíváme co se stane při spuštění programu. Sestavení, na které odkazuje váš program jsou načtena do výchozím kontextu načtení. Pokud načítáte cílové sestavení jeho identita, pomocí <xref:System.Reflection.Assembly.Load%2A> metody, bude ve výchozím kontextu načtení, a stejně tomu bude u jeho závislosti. Program a cílové sestavení bude používat stejný `Utility` sestavení.  
  
 Nicméně, Předpokládejme, že načtení cílové sestavení podle cesty k souboru pomocí <xref:System.Reflection.Assembly.LoadFile%2A> metody. Sestavení je načteno bez kontextu, takže jeho závislosti nejsou automaticky nahrány. Můžete mít obslužnou rutinu pro <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> může načíst události slouží k poskytování závislost a `Utility` sestavení se žádný kontext pomocí <xref:System.Reflection.Assembly.LoadFile%2A> metoda. Teď při vytváření instance typu, který je obsažen v cílové sestavení a zkuste ji přiřadit do proměnné typu `ICommunicate`, <xref:System.InvalidCastException> je vyvolána, protože modul runtime bere v úvahu `ICommunicate` rozhraní v dvě kopie `Utility` sestavení pro různé typy.  
  
 Existuje mnoho dalších scénářů, ve kterých může být sestavení načteno do více kontextů. Nejlepším řešením je, aby nedocházelo ke konfliktům přemístění cílové sestavení ve své cestě aplikace a použitím <xref:System.Reflection.Assembly.Load%2A> metodu se úplný zobrazovaný název. Sestavení se pak načtou do výchozím kontextu načtení, a obě sestavení použít stejné `Utility` sestavení.  
  
 Pokud cílové sestavení musí zůstat mimo cestu vaší aplikace, můžete použít <xref:System.Reflection.Assembly.LoadFrom%2A> metodu pro načtení do načtení z kontextu. Pokud cílové sestavení bylo zkompilováno pomocí odkazu na vaši aplikaci `Utility` sestavení, se bude používat `Utility` sestavení, které vaše aplikace se načítají do kontextu zatížení výchozí. Všimněte si, že může dojít k problémům pokud cílové sestavení má závislost na kopii `Utility` sestavení nacházejících se mimo vaši cestu aplikace. Pokud toto sestavení je načteno do načtení z kontextu před zatížení vašich aplikací `Utility` sestavení, načtení aplikace se nezdaří.  
  
 [Zvažte přepnutí do kontextu načtení výchozí](#switch_to_default) část popisuje alternativy k pomocí načte cestu souboru, například <xref:System.Reflection.Assembly.LoadFile%2A> a <xref:System.Reflection.Assembly.LoadFrom%2A>.  
  
<a name="avoid_loading_multiple_versions"></a>   
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Vyhněte se načítání více verzí sestavení do stejného kontextu  
 Načítání více verzí sestavení do jednoho kontextu zatížení může způsobovat problémy identity typu. Pokud stejný typ je načtena z dvou verzí stejného sestavení, je to, jako kdyby měla byly načteny dva různé typy se stejným názvem. <xref:System.InvalidCastException> Je vyvolána, pokud se pokusíte převést jednoho typu na druhý matoucí zprávou, která zadejte `MyType` nejde přetypovat na typ `MyType`.  
  
 Například váš program může načíst jednu verzi `Utility` sestavení přímo a později ji může načíst jiná sestavení, která načte jinou verzi `Utility` sestavení. Nebo chybě kódu může způsobit, že dvě cesty odlišný kód ve vaší aplikaci načíst různé verze sestavení.  
  
 Ve výchozím kontextu načtení, tento problém může vzniknout při použití <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodu a zadejte úplný sestavení zobrazované názvy, které obsahují různá čísla verze. Pro sestavení, které jsou načteny bez kontextu, může být způsobeno problém pomocí <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> metody k načtení stejné sestavení z různých cest. Modul runtime bere v úvahu dvě sestavení, která jsou načtena z různých cest na jiné sestavení, i v případě jejich identit.  
  
 Kromě typu identity problémy, může způsobit více verzí sestavení <xref:System.MissingMethodException> kód, který očekává, že tento typ z jiné verze je předán typ, který je načten z jedné verze sestavení. Například kód může očekávat metodu, která byla přidána na novější verzi.  
  
 Více drobným chybám může dojít, pokud mezi verzemi změnit chování typu. Například metoda může být vyvolání neočekávané výjimky, nebo vrátit neočekávanou hodnotu.  
  
 Pečlivě zkontrolujte kód a ujistěte se, že pouze jedna verze sestavení je načtena. Můžete použít <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> metodou ke zjištění, která sestavení jsou načteny v daném okamžiku.  
  
<a name="switch_to_default"></a>   
## <a name="consider-switching-to-the-default-load-context"></a>Zvažte možnost Výchozí kontext načtení  
 Prozkoumejte vzory pro načítání a nasazování sestavení vaší aplikace. Můžete vyloučit sestavení, která jsou načtena z bajtových polí? Můžete přesunout do cesta zjišťování sestavení? Pokud sestavení se nachází v globální mezipaměti sestavení nebo v doméně aplikace na zjišťování cesty (to znamená, že jeho <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A>), můžete načíst sestavení svoji identitu.  
  
 Pokud není možné vložit vaše sestavení cesta zjišťování, vezměte v úvahu alternativy, třeba pomocí modelu doplňku rozhraní .NET Framework, umístění sestavení do globální mezipaměti sestavení nebo vytváření domény aplikace.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>Zvažte použití modelu doplňku rozhraní .NET Framework  
 Pokud používáte načtení z kontextu pro implementaci doplňků, které nejsou obvykle nainstalovány v základ cesty aplikace, použijte modelu doplňku rozhraní .NET Framework. Tento model zajišťuje izolaci na úrovni domény nebo proces aplikací bez nutnosti spravovat domény aplikace sami. Informace o tomto modelu najdete v tématu [doplňků a rozšíření](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Zvažte možnost použít globální mezipaměti sestavení  
 Získejte výhodu, že cesta sdíleného sestavení místo sestavení v globální mezipaměti sestavení, která je mimo základ cesty, aplikace bez ztráty výhody výchozím kontextu načtení nebo s ohledem na nevýhody jiném kontextu.  
  
### <a name="consider-using-application-domains"></a>Zvažte používání domén aplikací  
 Pokud zjistíte, že některé z vašich sestavení se nedá nasadit aplikace cesta zjišťování, zvažte možnost vytvořit novou doménu aplikace pro tato sestavení. Použití <xref:System.AppDomainSetup> vytvořit novou doménu aplikace a použít <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> vlastnosti a určit cestu, která obsahuje sestavení, který chcete načíst. Pokud máte více adresářů, testovat, můžete nastavit <xref:System.AppDomainSetup.ApplicationBase%2A> do kořenového adresáře a použijte <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> vlastnost k identifikaci podadresáře testovat. Alternativně můžete vytvořit více domén aplikace a nastavení <xref:System.AppDomainSetup.ApplicationBase%2A> z každé aplikační domény na příslušné cesty pro jeho sestavení.  
  
 Všimněte si, že můžete použít <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu pro načtení těchto sestavení. Protože teď jsou cesta zjišťování, budou načtena do výchozím kontextu načtení místo načtení z kontextu. Doporučujeme však, že přejdete <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda a dodávky, celé zobrazované názvy sestavení k zajištění, že se vždy používají správné verze.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>
