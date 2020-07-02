---
title: Doporučené postupy pro načtení sestavení
description: Prozkoumejte osvědčené postupy pro načítání sestavení v .NET. Vyhněte se problémům typu identity, které mohou vést k neplatným přetypování, chybějícím metodám a jiným výjimkám.
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
ms.openlocfilehash: 8ee5243258ea1b853b4690b79ec032c46d1b3777
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803494"
---
# <a name="best-practices-for-assembly-loading"></a>Doporučené postupy pro načtení sestavení
Tento článek popisuje způsoby, jak zabránit problémům s typem identity, který může vést k <xref:System.InvalidCastException> <xref:System.MissingMethodException> chybám, a. Tento článek popisuje následující doporučení:  
  
- [Porozumění výhodám a nevýhodám zátěžových kontextů](#load_contexts)  
  
- [Vyhněte se vazbě na částečných názvech sestavení](#avoid_partial_names)  
  
- [Vyhnout se načítání sestavení do více kontextů](#avoid_loading_into_multiple_contexts)  
  
- [Vyhněte se načítání více verzí sestavení do stejného kontextu](#avoid_loading_multiple_versions)  
  
- [Zvažte přechod na výchozí kontext načtení.](#switch_to_default)  
  
 První doporučení, [porozumět výhodám a nevýhodám zátěžových kontextů](#load_contexts), poskytuje základní informace o dalších doporučeních, protože všechny jsou závislé na znalostech kontextů zatížení.  
  
<a name="load_contexts"></a>
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Porozumění výhodám a nevýhodám zátěžových kontextů  
 V rámci domény aplikace mohou být sestavení načtena do jednoho ze tří kontextů, nebo mohou být načtena bez kontextu:  
  
- Výchozí kontext načtení obsahuje sestavení zjištěná při zjišťování globální mezipaměti sestavení (GAC), úložiště sestavení hostitele, pokud je modul runtime hostován (například v SQL Server), a v <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> doméně aplikace. Většina přetížení <xref:System.Reflection.Assembly.Load%2A> metody načítají sestavení do tohoto kontextu.  
  
- Kontext načtení z obsahuje sestavení, která jsou načtena z umístění, která nejsou prohledávána zavaděčem. Například doplňky mohou být nainstalovány v adresáři, který není v cestě aplikace. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType> a <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> jsou příklady metod, které jsou načteny podle cesty.  
  
- Kontext pouze pro reflexi obsahuje sestavení načítaná s <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metodami a. Kód v tomto kontextu nelze provést, takže zde není popsán. Další informace naleznete v tématu [Postupy: načtení sestavení do kontextu pouze pro reflexi](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
- Pokud jste vygenerovali přechodné dynamické sestavení pomocí generování reflexe, sestavení není v žádném kontextu. Kromě toho většina sestavení, která jsou načtena pomocí <xref:System.Reflection.Assembly.LoadFile%2A> metody, je načítána bez kontextu a sestavení, která jsou načtena z bajtových polí, jsou načtena bez kontextu, pokud jejich identita (po použití zásady) zjistí, že jsou v globální mezipaměti sestavení (GAC).  
  
 Kontexty spuštění mají své výhody a nevýhody, jak je popsáno v následujících částech.  
  
### <a name="default-load-context"></a>Výchozí kontext načtení  
 Když jsou sestavení načtena do výchozího kontextu načtení, jejich závislosti jsou načteny automaticky. Závislosti, které jsou načteny do výchozího kontextu načtení, jsou automaticky nalezeny pro sestavení ve výchozím kontextu načtení nebo v kontextu načtení z. Načítání podle identity sestavení zvyšuje stabilitu aplikací tím, že zajišťují, že nejsou použity neznámé verze sestavení (viz oddíl [Vyhněte se vazbám v částečných názvech sestavení](#avoid_partial_names) ).  
  
 Použití výchozího kontextu zatížení má následující nevýhody:  
  
- Závislosti, které jsou načteny do jiných kontextů, nejsou k dispozici.  
  
- Sestavení nelze načíst z umístění mimo cestu pro zjišťování do výchozího kontextu načtení.  
  
### <a name="load-from-context"></a>Načíst z kontextu  
 Kontext načtení z umožňuje načíst sestavení z cesty, která není v cestě aplikace, a proto není zahrnuto do zjišťování. Umožňuje umístění a načtení závislostí z této cesty, protože informace o cestě jsou udržovány v kontextu. Kromě toho sestavení v tomto kontextu mohou používat závislosti, které jsou načteny do výchozího kontextu načtení.  
  
 Načítání sestavení pomocí <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody nebo jedné z jiných metod, které jsou načítány pomocí cesty, má následující nevýhody:  
  
- Pokud je již načteno sestavení se stejnou identitou, <xref:System.Reflection.Assembly.LoadFrom%2A> vrátí načtené sestavení i v případě, že byla zadána jiná cesta.  
  
- Pokud je sestavení načteno pomocí <xref:System.Reflection.Assembly.LoadFrom%2A> a později se sestavení ve výchozím kontextu načtení pokusí načíst stejné sestavení pomocí zobrazovaného názvu, pokus o načtení se nezdaří. K tomu může dojít, když je sestavení deserializováno.  
  
- Pokud je sestavení načteno pomocí <xref:System.Reflection.Assembly.LoadFrom%2A> a cesta ke zjišťování obsahuje sestavení se stejnou identitou, ale v jiném umístění, <xref:System.InvalidCastException> <xref:System.MissingMethodException> může být, nebo jiné neočekávané chování.  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A>požaduje <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> a <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType> , nebo <xref:System.Net.WebPermission> v zadané cestě.  
  
- Pokud pro sestavení existuje nativní bitová kopie, není použita.  
  
- Sestavení nelze načíst jako doménově neutrální.  
  
- V .NET Framework verzích 1,0 a 1,1 se zásada nepoužívá.  
  
### <a name="no-context"></a>Žádný kontext  
 Načtení bez kontextu je jedinou možností pro přechodná sestavení, která jsou generována pomocí generování reflexe. Načtení bez kontextu je jediným způsobem, jak načíst více sestavení, která mají stejnou identitu do jedné domény aplikace. Náklady na zjišťování se vyhne.  
  
 Sestavení, která jsou načtena z polí bajtů, jsou načtena bez kontextu, pokud není identita sestavení, která je vytvořena při použití zásady, shodná s identitou sestavení v globální mezipaměti sestavení (GAC). v takovém případě je sestavení načteno z globální mezipaměti sestavení (GAC).  
  
 Načítání sestavení bez kontextu má následující nevýhody:  
  
- Jiná sestavení nemohou vytvořit vazby na sestavení, která jsou načtena bez kontextu, pokud událost nezpracováváte <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> .  
  
- Závislosti nejsou načteny automaticky. Můžete je předem načíst bez kontextu, předčítat je do výchozího kontextu načtení nebo je načíst pomocí zpracování <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> události.  
  
- Načtení více sestavení se stejnou identitou bez kontextu může způsobit problémy s identitou typu podobné těm, které způsobily načtení sestavení se stejnou identitou do více kontextů. Viz [Vyhněte se načítání sestavení do více kontextů](#avoid_loading_into_multiple_contexts).  
  
- Pokud pro sestavení existuje nativní bitová kopie, není použita.  
  
- Sestavení nelze načíst jako doménově neutrální.  
  
- V .NET Framework verzích 1,0 a 1,1 se zásada nepoužívá.  
  
<a name="avoid_partial_names"></a>
## <a name="avoid-binding-on-partial-assembly-names"></a>Vyhněte se vazbě na částečných názvech sestavení  
 Částečná vazba názvu nastane, pokud při načítání sestavení zadáte pouze část zobrazovaného názvu sestavení ( <xref:System.Reflection.Assembly.FullName%2A> ). Například můžete zavolat <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodu pouze s jednoduchým názvem sestavení a vynechání verze, jazykové verze a tokenu veřejného klíče. Případně můžete zavolat <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metodu, která první volá <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodu a, pokud se nepovede najít sestavení, prohledá globální mezipaměť sestavení a načte nejnovější dostupnou verzi sestavení.  
  
 Částečná vazba názvu může způsobit mnoho problémů, včetně následujících:  
  
- <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>Metoda může načíst jiné sestavení se stejným jednoduchým názvem. Například dvě aplikace mohou nainstalovat dvě zcela odlišná sestavení, která obě mají jednoduchý název `GraphicsLibrary` do globální mezipaměti sestavení (GAC).  
  
- Sestavení, které je skutečně načteno, nemusí být zpětně kompatibilní. Například pokud není zadána verze, může dojít k nasazování mnohem novější verze než verze, kterou program původně napsal. Změny v novější verzi můžou způsobit chyby ve vaší aplikaci.  
  
- Sestavení, které je skutečně načteno, nemusí být kompatibilní s dopředné. Mohli jste například sestavit a otestovat aplikaci pomocí nejnovější verze sestavení, ale Částečná vazba může načíst mnohem starší verzi, která postrádá funkce, které vaše aplikace používá.  
  
- Instalace nových aplikací může přerušit stávající aplikace. Aplikace, která používá <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metodu, může být poškozena instalací novější nekompatibilní verze sdíleného sestavení.  
  
- Může dojít k neočekávanému načtení závislostí. Načtete dvě sestavení, která sdílejí závislost, a jejich načítání s částečnou vazbou může mít za následek jedno sestavení pomocí komponenty, kterou nebyl sestaven nebo testován pomocí.  
  
 Z důvodu problémů, které může způsobit, byla <xref:System.Reflection.Assembly.LoadWithPartialName%2A> Metoda označena jako zastaralá. Doporučujeme <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> místo toho použít metodu a zadat úplné zobrazované názvy sestavení. Přečtěte si informace [o výhodách a nevýhodách zátěžových](#load_contexts) kontextů a [zvažte přechod na výchozí kontext načtení](#switch_to_default).  
  
 Pokud chcete použít <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metodu, protože usnadňuje načítání sestavení, zvažte, že aplikace selže s chybovou zprávou, která identifikuje chybějící sestavení, bude pravděpodobně poskytovat lepší uživatelské prostředí, než automaticky používá neznámou verzi sestavení, což může způsobit nepředvídatelné chování a bezpečnostní otvory.  
  
<a name="avoid_loading_into_multiple_contexts"></a>
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Vyhnout se načítání sestavení do více kontextů  
 Načtení sestavení do více kontextů může způsobit problémy s identitou typu. Pokud je stejný typ načten ze stejného sestavení do dvou různých kontextů, jedná se o to, aby byly načteny dva různé typy se stejným názvem. <xref:System.InvalidCastException>Výjimka je vyvolána, pokud se pokusíte přetypovat jeden typ na druhý, přičemž zpráva, kterou typ není `MyType` možné přetypovat na typ `MyType` .  
  
 Předpokládejme například, že `ICommunicate` rozhraní je deklarováno v sestavení s názvem `Utility` , které je odkazováno v programu a také jinými sestaveními, které program načítá. Tato další sestavení obsahují typy, které implementují `ICommunicate` rozhraní, což umožňuje programu jejich použití.  
  
 Nyní zvažte, co se stane, když se program spustí. Sestavení, na která se odkazuje váš program, se načtou do výchozího kontextu zatížení. Pokud načtete cílové sestavení pomocí jeho identity pomocí <xref:System.Reflection.Assembly.Load%2A> metody, bude ve výchozím kontextu načtení, a proto bude jeho závislosti. Aplikace i cílové sestavení budou používat stejné `Utility` sestavení.  
  
 Předpokládejme však, že nahrajete cílové sestavení pomocí cesty k souboru pomocí <xref:System.Reflection.Assembly.LoadFile%2A> metody. Sestavení je načteno bez kontextu, takže jeho závislosti nejsou automaticky načteny. Je možné, že máte obslužnou rutinu pro <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost k poskytnutí závislosti a může načíst sestavení bez `Utility` kontextu pomocí <xref:System.Reflection.Assembly.LoadFile%2A> metody. Nyní když vytvoříte instanci typu, která je obsažena v cílovém sestavení a pokusíte se ji přiřadit proměnné typu `ICommunicate` , <xref:System.InvalidCastException> je vyvolána výjimka, protože modul runtime považuje `ICommunicate` rozhraní ve dvou kopiích `Utility` sestavení za rozdílné typy.  
  
 Existuje mnoho dalších scénářů, ve kterých může být sestavení načteno do více kontextů. Nejlepším řešením je vyhnout se konfliktům tím, že v cestě aplikace přemístěte cílové sestavení a použijete <xref:System.Reflection.Assembly.Load%2A> metodu s úplným zobrazovaným názvem. Sestavení je poté načteno do výchozího kontextu zatížení a obě sestavení používají stejné `Utility` sestavení.  
  
 Pokud cílové sestavení musí zůstat mimo cestu aplikace, můžete použít <xref:System.Reflection.Assembly.LoadFrom%2A> metodu pro načtení do kontextu load-from. Pokud bylo cílové sestavení zkompilováno s odkazem na sestavení vaší aplikace `Utility` , bude použito `Utility` sestavení, které vaše aplikace načetla do výchozího kontextu načtení. Všimněte si, že problémy mohou nastat, pokud cílové sestavení má závislost na kopii `Utility` sestavení nacházející se mimo cestu k vaší aplikaci. Pokud je toto sestavení načteno do kontextu load-from předtím, než vaše aplikace načte `Utility` sestavení, zatížení vaší aplikace selže.  
  
 [Přechod na výchozí část kontextu zatížení](#switch_to_default) se zabývá alternativami k použití načtených cest souborů, jako jsou <xref:System.Reflection.Assembly.LoadFile%2A> a <xref:System.Reflection.Assembly.LoadFrom%2A> .  
  
<a name="avoid_loading_multiple_versions"></a>
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Vyhněte se načítání více verzí sestavení do stejného kontextu  
 Načítání více verzí sestavení do jednoho kontextu načtení může způsobit problémy s identitou typu. Pokud je stejný typ načten ze dvou verzí stejného sestavení, je to tak, že byly načteny dva různé typy se stejným názvem. <xref:System.InvalidCastException>Výjimka je vyvolána, pokud se pokusíte přetypovat jeden typ na druhý, přičemž zpráva, kterou typ není `MyType` možné přetypovat na typ `MyType` .  
  
 Například váš program může načítat jednu verzi `Utility` sestavení přímo a později může načíst jiné sestavení, které načte jinou verzi `Utility` sestavení. Nebo Chyba kódování může v aplikaci způsobit dvě různé cesty kódu pro načtení různých verzí sestavení.  
  
 Ve výchozím kontextu načtení k tomuto problému může dojít při použití <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody a zadání úplných zobrazovaných názvů sestavení, které obsahují různá čísla verzí. Pro sestavení, která jsou načtena bez kontextu, může být problém způsoben použitím <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> metody pro načtení stejného sestavení z různých cest. Modul runtime považuje dvě sestavení, která jsou načtena z různých cest v různých sestaveních, a to i v případě, že jsou jejich identity stejné.  
  
 Kromě potíží s identitou typu může více verzí sestavení způsobit, že <xref:System.MissingMethodException> Pokud typ, který je načten z jedné verze sestavení, je předán kódu, který tento typ z jiné verze očekává. Kód může například očekávat metodu, která byla přidána do novější verze.  
  
 K dalším drobným chybám může dojít, pokud se chování typu změnilo mezi verzemi. Například metoda může vyvolat neočekávanou výjimku nebo vracet neočekávanou hodnotu.  
  
 Pečlivě zkontrolujte kód a zajistěte, aby byla načtena pouze jedna verze sestavení. Můžete použít <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> metodu k určení, která sestavení jsou načtena v daném okamžiku.  
  
<a name="switch_to_default"></a>
## <a name="consider-switching-to-the-default-load-context"></a>Zvažte přechod na výchozí kontext načtení.  
 Prověřte načítání sestavení aplikace a vzory nasazení. Můžete eliminovat sestavení, která jsou načtena z bajtových polí? Můžete přesunout sestavení do cesty pro zjišťování? Pokud jsou sestavení umístěna v globální mezipaměti sestavení (GAC) nebo v cestě ke zjišťování domény aplikace (to znamená, že <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A> ), můžete sestavení načíst pomocí jeho identity.  
  
 Pokud není možné umístit všechna vaše sestavení do cesty pro zjišťování, zvažte alternativy, jako je například použití modelu doplňku .NET Framework, umístění sestavení do globální mezipaměti sestavení (GAC) nebo vytváření domén aplikace.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>Zvažte použití .NET Frameworkho modelu doplňku  
 Pokud používáte kontext načtení z k implementaci doplňků, které obvykle nejsou nainstalovány v základu aplikace, použijte Model doplňku .NET Framework. Tento model poskytuje izolaci na úrovni domény aplikace nebo procesu bez nutnosti spravovat domény aplikace sami. Informace o modelu doplňku naleznete v tématu [Doplňky a rozšiřitelnost](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Zvažte použití globální mezipaměti sestavení (GAC)  
 Umístěte sestavení do globální mezipaměti sestavení (GAC), abyste získali výhodu sdílené cesty sestavení, která je mimo základ aplikace, aniž by došlo ke ztrátě výhod výchozího kontextu zatížení nebo k nevýhodám ostatních kontextů.  
  
### <a name="consider-using-application-domains"></a>Zvažte použití aplikačních domén.  
 Pokud určíte, že některá z vašich sestavení nelze nasadit v cestě ke zjišťování aplikace, zvažte vytvoření nové aplikační domény pro tato sestavení. Použijte <xref:System.AppDomainSetup> k vytvoření nové domény aplikace a <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> vlastnost použijte k určení cesty obsahující sestavení, která chcete načíst. Pokud máte k dispozici více adresářů, můžete nastavit <xref:System.AppDomainSetup.ApplicationBase%2A> kořenový adresář a použít <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> vlastnost k identifikaci podadresářů k testování. Alternativně můžete vytvořit více domén aplikace a nastavit <xref:System.AppDomainSetup.ApplicationBase%2A> každou doménu aplikace na odpovídající cestu pro její sestavení.  
  
 Všimněte si, že <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> k načtení těchto sestavení lze použít metodu. Vzhledem k tomu, že jsou nyní v cestě zjišťování, budou načteny do výchozího kontextu zatížení namísto kontextu load-from. Nicméně doporučujeme, abyste přešli na <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodu a poskytovali úplné zobrazované názvy sestavení, aby se zajistilo, že se vždy použijí správné verze.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>
