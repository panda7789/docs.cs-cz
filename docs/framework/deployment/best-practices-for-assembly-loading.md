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
ms.openlocfilehash: 7575c40edf47e977335bcc34fcd9e49debab0980
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181705"
---
# <a name="best-practices-for-assembly-loading"></a>Doporučené postupy pro načtení sestavení
Tento článek popisuje způsoby, jak se vyhnout <xref:System.InvalidCastException>problémům <xref:System.MissingMethodException>s identitou typu, které mohou vést k , a další chyby. Článek popisuje následující doporučení:  
  
- [Pochopte výhody a nevýhody kontextů zatížení](#load_contexts)  
  
- [Vyhněte se vazbě na názvy částečných sestavení](#avoid_partial_names)  
  
- [Vyhněte se načítání sestavy do více kontextů](#avoid_loading_into_multiple_contexts)  
  
- [Vyhněte se načítání více verzí sestavení do stejného kontextu](#avoid_loading_multiple_versions)  
  
- [Zvažte přepnutí na výchozí kontext zatížení](#switch_to_default)  
  
 První doporučení, [pochopit výhody a nevýhody zatížení kontexty](#load_contexts), poskytuje základní informace pro další doporučení, protože všechny závisí na znalosti zatížení kontexty.  
  
<a name="load_contexts"></a>
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Seznamte se s výhodami a nevýhodami kontextů zatížení  
 V rámci domény aplikace lze sestavení načíst do jednoho ze tří kontextů nebo je lze načíst bez kontextu:  
  
- Výchozí kontext zatížení obsahuje sestavení nalezená zjišťováním globální mezipaměti sestavení, úložiště sestavení hostitele, pokud je modul <xref:System.AppDomainSetup.ApplicationBase%2A> runtime hostován (například na serveru SQL Server), a doménu aplikace a a. <xref:System.AppDomainSetup.PrivateBinPath%2A> Většina přetížení <xref:System.Reflection.Assembly.Load%2A> sestavení zatížení metody do tohoto kontextu.  
  
- Kontext load-from obsahuje sestavení, která jsou načtena z umístění, která nejsou prohledána zavaděčem. Doplňky mohou být například nainstalovány v adresáři, který není v cestě aplikace. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>a <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> jsou příklady metod, které se načítají podle cesty.  
  
- Pouze reflexe kontextu obsahuje sestavení <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> naloženo s a <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody. Kód v tomto kontextu nelze spustit, takže není popsánzde. Další informace naleznete v [tématu How to: Load Assemblies into the Reflection-Only Context](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
- Pokud jste vygenerovali přechodné dynamické sestavení pomocí odrazu vyzařovat, sestavení není v žádném kontextu. Kromě toho většina sestavení, které <xref:System.Reflection.Assembly.LoadFile%2A> jsou načteny pomocí metody jsou načteny bez kontextu a sestavení, které jsou načteny z bajtových polí jsou načteny bez kontextu, pokud jejich identita (po použití zásady) zjistí, že jsou v globální mezipaměti sestavení.  
  
 Spuštění kontexty mají výhody a nevýhody, jak je popsáno v následujících částech.  
  
### <a name="default-load-context"></a>Výchozí kontext načítání  
 Při načtení sestavení do výchozího kontextu zatížení jsou jejich závislosti načteny automaticky. Závislosti, které jsou načteny do výchozího kontextu načítání, jsou nalezeny automaticky pro sestavení ve výchozím kontextu zatížení nebo kontextu zatížení z. Načítání identitou sestavení zvyšuje stabilitu aplikací tím, že zajišťuje, že se nepoužívají neznámé verze sestavení (viz část [Vyhněte se vazbě na částečné názvy sestavení).](#avoid_partial_names)  
  
 Použití výchozího kontextu zatížení má následující nevýhody:  
  
- Závislosti, které jsou načteny do jiných kontextů, nejsou k dispozici.  
  
- Sestavení z umístění mimo cestu zjišťování nelze načíst do výchozího kontextu načítání.  
  
### <a name="load-from-context"></a>Načíst z kontextu  
 Kontext load-from umožňuje načíst sestavení z cesty, která není pod cestou aplikace, a proto není zahrnuta v zjišťování. Umožňuje závislosti, které mají být umístěny a načteny z této cesty, protože informace o cestě je udržována kontextu. Kromě toho sestavení v tomto kontextu můžete použít závislosti, které jsou načteny do výchozího kontextu zatížení.  
  
 Načítání sestavení pomocí <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody nebo jedné z dalších metod, které se načítají cestou, má následující nevýhody:  
  
- Pokud je již načteno sestavení se <xref:System.Reflection.Assembly.LoadFrom%2A> stejnou identitou, vrátí načtené sestavení i v případě, že byla zadána jiná cesta.  
  
- Pokud je sestavení <xref:System.Reflection.Assembly.LoadFrom%2A>načteno s a později se sestavení ve výchozím kontextu zatížení pokusí načíst stejné sestavení podle zobrazovaného názvu, pokus o načtení se nezdaří. Tato situace může nastat při rekonstruované sestavení.  
  
- Pokud je sestavení <xref:System.Reflection.Assembly.LoadFrom%2A>načteno s , a cesta zjišťování obsahuje sestavení se stejnou <xref:System.InvalidCastException>identitou, ale v jiném umístění, může dojít k , <xref:System.MissingMethodException>nebo jinému neočekávanému chování.  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A>požadavky <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>a <xref:System.Net.WebPermission>, nebo na zadanou cestu.  
  
- Pokud pro sestavení existuje nativní bitová kopie, nebude použita.  
  
- Sestavení nelze načíst jako neutrální doménu.  
  
- V rozhraní .NET Framework verze 1.0 a 1.1 zásady není použita.  
  
### <a name="no-context"></a>Žádný kontext  
 Načítání bez kontextu je jedinou možností pro přechodná sestavení, která jsou generována s odrazem emit. Načítání bez kontextu je jediný způsob, jak načíst více sestavení, které mají stejnou identitu do jedné domény aplikace. Náklady na sondování je zabráněno.  
  
 Sestavení, která jsou načtena z bajtových polí, jsou načtena bez kontextu, pokud identita sestavení, která je vytvořena při použití zásady, neodpovídá identitě sestavení v globální mezipaměti sestavení; v takovém případě je sestavení načteno z globální mezipaměti sestavení.  
  
 Načítání sestavení bez kontextu má následující nevýhody:  
  
- Jiná sestavení nelze vytvořit vazbu na sestavení, která <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> jsou načtena bez kontextu, pokud událost nezpracovat.  
  
- Závislosti nejsou načteny automaticky. Můžete je předem načíst bez kontextu, předem je načíst do <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> výchozího kontextu zatížení nebo je načíst zpracováním události.  
  
- Načítání více sestavení se stejnou identitou bez kontextu může způsobit problémy s identitou typu podobné těm, které jsou způsobeny načítáním sestavení se stejnou identitou do více kontextů. Viz [Vyhněte se načítání sestavení do více kontextů](#avoid_loading_into_multiple_contexts).  
  
- Pokud pro sestavení existuje nativní bitová kopie, nebude použita.  
  
- Sestavení nelze načíst jako neutrální doménu.  
  
- V rozhraní .NET Framework verze 1.0 a 1.1 zásady není použita.  
  
<a name="avoid_partial_names"></a>
## <a name="avoid-binding-on-partial-assembly-names"></a>Vyhněte se vazbě na částečné názvy sestavení  
 Částečná vazba názvu nastane, když zadáte<xref:System.Reflection.Assembly.FullName%2A>pouze část zobrazovaného názvu sestavení ( ) při načtení sestavy. Například můžete volat <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodu pouze s jednoduchým názvem sestavení, vynechání verze, jazykové verze a token veřejného klíče. Nebo můžete volat <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metodu, která <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nejprve volá metodu a pokud se nepodaří najít sestavení, prohledá globální mezipaměť sestavení a načte nejnovější dostupnou verzi sestavení.  
  
 Částečná vazba názvu může způsobit mnoho problémů, včetně následujících:  
  
- Metoda <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> může načíst jiné sestavení se stejným jednoduchým názvem. Například dvě aplikace mohou nainstalovat dvě zcela odlišná `GraphicsLibrary` sestavení, která mají jednoduchý název do globální mezipaměti sestavení.  
  
- Sestavení, které je skutečně načtennemusí být zpětně kompatibilní. Například nezadání verze může mít za následek načítání mnohem novější verze, než byla původně napsána verze, kterou byl program původně napsán k použití. Změny v novější verzi může způsobit chyby v aplikaci.  
  
- Sestavení, které je skutečně načteno, nemusí být kompatibilní s forwardem. Například jste vytvořili a otestovali aplikaci s nejnovější verzí sestavení, ale částečná vazba může načíst mnohem starší verzi, která postrádá funkce, které vaše aplikace používá.  
  
- Instalace nových aplikací může přerušit stávající aplikace. Aplikace, která <xref:System.Reflection.Assembly.LoadWithPartialName%2A> používá metodu lze porušit instalací novější, nekompatibilní verze sdíleného sestavení.  
  
- Může dojít k neočekávanému načítání závislostí. Načtete dvě sestavení, která sdílejí závislost, načítání je s částečnou vazbou může mít za následek jednu sestavu pomocí součásti, která nebyla vytvořena nebo testována s.  
  
 Z důvodu problémů, které <xref:System.Reflection.Assembly.LoadWithPartialName%2A> může způsobit, byla metoda označena jako zastaralá. Doporučujeme použít metodu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> místo a zadejte úplné sestavení zobrazované názvy. Viz [Principy výhod a nevýhod kontextů zatížení](#load_contexts) a [zvažte přepnutí na výchozí kontext načítání](#switch_to_default).  
  
 Pokud chcete použít <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metodu, protože usnadňuje načítání sestavení, zvažte, že s vaší aplikace nezdaří s chybovou zprávou, která identifikuje chybějící sestavení je pravděpodobné, že poskytne lepší uživatelské prostředí než automaticky pomocí neznámé verze sestavení, což může způsobit nepředvídatelné chování a bezpečnostní díry.  
  
<a name="avoid_loading_into_multiple_contexts"></a>
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Vyhněte se načítání sestavení do více kontextů  
 Načítání sestavení do více kontextů může způsobit problémy s identitou typu. Pokud je stejný typ načten ze stejného sestavení do dvou různých kontextů, je to, jako kdyby byly načteny dva různé typy se stejným názvem. Je <xref:System.InvalidCastException> vyvolána, pokud se pokusíte přetypovat jeden typ `MyType` na druhý, `MyType`s matoucí zprávu, že typ nelze přetypovat na typ .  
  
 Předpokládejme například, `ICommunicate` že rozhraní je `Utility`deklarováno v sestavení s názvem , na které odkazuje program a také další sestavení, která program načte. Tato další sestavení obsahují typy, které implementují `ICommunicate` rozhraní, což umožňuje programu je používat.  
  
 Nyní zvažte, co se stane, když je váš program spuštěn. Sestavení, na která program odkazuje, jsou načtena do výchozího kontextu načítání. Pokud načtete cílové sestavení podle jeho <xref:System.Reflection.Assembly.Load%2A> identity pomocí metody, bude ve výchozím kontextu zatížení a tak bude jeho závislosti. Váš program i cílové sestavení budou `Utility` používat stejné sestavení.  
  
 Předpokládejme však, že načtete cílové <xref:System.Reflection.Assembly.LoadFile%2A> sestavení podle cesty k souboru pomocí metody. Sestavení je načteno bez kontextu, takže jeho závislosti nejsou automaticky načteny. Můžete mít obslužnou rutinu <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pro událost k `Utility` zadání závislosti a může <xref:System.Reflection.Assembly.LoadFile%2A> načíst sestavení bez kontextu pomocí metody. Nyní při vytváření instance typu, který je obsažen v cílovém sestavení a pokuste `ICommunicate` <xref:System.InvalidCastException> se ji přiřadit proměnné typu `ICommunicate` , je vyvolána, `Utility` protože modul runtime považuje rozhraní ve dvou kopiích sestavení za různé typy.  
  
 Existuje mnoho dalších scénářů, ve kterých lze načíst sestavení do více kontextů. Nejlepším přístupem je vyhnout se konfliktům přemístěním cílového sestavení v <xref:System.Reflection.Assembly.Load%2A> cestě aplikace a použitím metody s úplným zobrazovaným názvem. Sestava je pak načtena do výchozího kontextu zatížení `Utility` a obě sestavení používají stejné sestavení.  
  
 Pokud cílové sestavení musí zůstat mimo cestu aplikace, můžete použít metodu <xref:System.Reflection.Assembly.LoadFrom%2A> k načtení do kontextu load-from. Pokud cílové sestavení bylo zkompilován s `Utility` odkazem na sestavení `Utility` vaší aplikace, bude používat sestavení, které vaše aplikace načetla do výchozího kontextu zatížení. Všimněte si, že problémy mohou nastat, pokud `Utility` cílové sestavení má závislost na kopii sestavení umístěné mimo cestu aplikace. Pokud je toto sestavení načteno do kontextu `Utility` zatížení z před načtením sestavení, zatížení aplikace se nezdaří.  
  
 V [části Zvažte přepnutí na výchozí kontext načítání](#switch_to_default) popisuje <xref:System.Reflection.Assembly.LoadFile%2A> alternativy k použití načtení cesty k souboru, například a <xref:System.Reflection.Assembly.LoadFrom%2A>.  
  
<a name="avoid_loading_multiple_versions"></a>
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Vyhněte se načítání více verzí sestavení do stejného kontextu  
 Načítání více verzí sestavení do jednoho kontextu zatížení může způsobit problémy s identitou typu. Pokud je stejný typ načten ze dvou verzí stejného sestavení, je to, jako kdyby byly načteny dva různé typy se stejným názvem. Je <xref:System.InvalidCastException> vyvolána, pokud se pokusíte přetypovat jeden typ `MyType` na druhý, `MyType`s matoucí zprávu, že typ nelze přetypovat na typ .  
  
 Program může například načíst jednu verzi `Utility` sestavení přímo a později může načíst `Utility` jiné sestavení, které načte jinou verzi sestavení. Nebo chyba kódování může způsobit dvě různé cesty kódu v aplikaci načíst různé verze sestavení.  
  
 Ve výchozím kontextu zatížení k tomuto problému <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> může dojít při použití metody a zadat úplné sestavení zobrazované názvy, které obsahují různá čísla verzí. U sestavení, která jsou načtena bez kontextu, <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> může být problém způsoben použitím metody k načtení stejnésestavy z různých cest. Za běhu považuje dvě sestavení, které jsou načteny z různých cest, za různá sestavení, i když jsou jejich identity stejné.  
  
 Kromě problémů s identitou typu může více verzí <xref:System.MissingMethodException> sestavení způsobit, pokud je typ načtený z jedné verze sestavení předán kódu, který očekává tento typ z jiné verze. Kód může například očekávat metodu, která byla přidána do novější verze.  
  
 Jemnější chyby může dojít, pokud chování typu změnil mezi verzemi. Metoda může například vyvolat neočekávanou výjimku nebo vrátit neočekávanou hodnotu.  
  
 Pečlivě zkontrolujte kód a ujistěte se, že je načtena pouze jedna verze sestavení. Tuto metodu <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> můžete použít k určení sestavení, která jsou v daném okamžiku načtena.  
  
<a name="switch_to_default"></a>
## <a name="consider-switching-to-the-default-load-context"></a>Zvažte přepnutí na výchozí kontext načítání  
 Zkontrolujte vzory načítání a nasazování sestavení aplikace. Můžete eliminovat sestavení, která jsou načtena z bajtových polí? Můžete přesunout sestavení do cesty sondování? Pokud jsou sestavení umístěna v globální mezipaměti sestavení nebo v cestě zjišťování <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A>domény aplikace (tj. jeho a ), můžete načíst sestavení podle jeho identity.  
  
 Pokud není možné umístit všechna sestavení do cesty zjišťování, zvažte alternativy, jako je například použití modelu doplňku rozhraní .NET Framework, umístění sestavení do globální mezipaměti sestavení nebo vytvoření aplikačních domén.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>Zvažte použití modelu doplňku rozhraní .NET Framework  
 Pokud používáte kontext load-from k implementaci doplňků, které obvykle nejsou nainstalovány v základu aplikace, použijte model doplňku rozhraní .NET Framework. Tento model poskytuje izolaci na úrovni domény aplikace nebo procesu, aniž byste museli spravovat aplikační domény sami. Informace o modelu doplňku naleznete [v tématu Doplňky a rozšiřitelnost](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Zvažte použití globální mezipaměti sestavení  
 Umístěte sestavení do globální mezipaměti sestavení, abyste získali výhodu sdílené cesty sestavení, která je mimo základnu aplikace, aniž byste ztratili výhody výchozího kontextu zatížení nebo převzali nevýhody jiných kontextů.  
  
### <a name="consider-using-application-domains"></a>Zvažte použití aplikačních domén  
 Pokud zjistíte, že některá sestavení nelze nasadit v cestě zjišťování aplikace, zvažte vytvoření nové domény aplikace pro tato sestavení. Použijte <xref:System.AppDomainSetup> an k vytvoření nové domény <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> aplikace a použijte vlastnost k určení cesty, která obsahuje sestavení, která chcete načíst. Pokud máte více adresářů pro účely sondy, můžete <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> nastavit kořenový adresář a použít vlastnost k identifikaci podadresářů, které mají být sondovat. Případně můžete vytvořit více aplikačních domén <xref:System.AppDomainSetup.ApplicationBase%2A> a nastavit každou doménu aplikace na příslušnou cestu pro její sestavení.  
  
 Všimněte si, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> že můžete použít metodu k načtení těchto sestavení. Vzhledem k tomu, že jsou nyní v cestě zjišťování, budou načteny do výchozího kontextu zatížení namísto kontextu zatížení z. Doporučujeme však přepnout <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> na metodu a zadat úplné sestavení zobrazované názvy, aby bylo zajištěno, že správné verze jsou vždy používány.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>
