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
ms.openlocfilehash: b05ec604f8493ba773d9de9af19acc70c023b8bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394150"
---
# <a name="best-practices-for-assembly-loading"></a>Doporučené postupy pro načtení sestavení
Tento článek popisuje způsoby, jak se vyhnout potížím typ identity, který může vést k <xref:System.InvalidCastException>, <xref:System.MissingMethodException>a dalších chyb. Článek popisuje následující doporučení:  
  
-   [Porozumět výhodám a nevýhodám kontexty zatížení](#load_contexts)  
  
-   [Vyhněte se vazbu na názvy částečného sestavení](#avoid_partial_names)  
  
-   [Vyhněte se načtení sestavení do více kontexty](#avoid_loading_into_multiple_contexts)  
  
-   [Vyhněte se načtení více verzí sestavení do stejného kontextu](#avoid_loading_multiple_versions)  
  
-   [Zvažte možnost Výchozí kontext načtení](#switch_to_default)  
  
 První doporučení [pochopit výhody a nevýhody zatížení kontextů](#load_contexts), obsahuje základní informace pro ostatní doporučení, protože jsou všechny závislé na znalost kontexty zatížení.  
  
<a name="load_contexts"></a>   
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Porozumět výhodám a nevýhodám kontexty zatížení  
 V doméně aplikace sestavení může být načtena do jednoho ze tří kontextů, nebo je lze načíst bez kontextu:  
  
-   Výchozí kontext načtení obsahuje sestavení nalezena zjišťování globální mezipaměti sestavení, úložišti sestavení hostitele, pokud je modul runtime hostovaná (například v systému SQL Server) a <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A> domény aplikace. Většina přetížení <xref:System.Reflection.Assembly.Load%2A> metoda načtení sestavení do tohoto kontextu.  
  
-   Načtení z kontextu obsahuje sestavení, které jsou načteny z umístění, které se neprohledávají zavaděčem. Například může být nainstalováno doplňky v adresáři, který není v cestě aplikace. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>, a <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> jsou příklady metod, které načíst cestou.  
  
-   Kontext pouze pro reflexi obsahuje sestavení načtená <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> a <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody. Kód v tomto kontextu nelze provést, takže není zde popsané. Další informace najdete v tématu [postupy: načtení sestavení do kontextu Reflection](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
-   Pokud jste vygenerovali přechodný dynamické sestavení pomocí reflexe emitování, sestavení, není v libovolném kontextu. Kromě toho většina sestavení, která jsou načtena pomocí <xref:System.Reflection.Assembly.LoadFile%2A> metoda jsou načteny bez kontextu a sestavení, která jsou načtena z bajtových polí jsou načteny bez kontextu, pokud jejich identity (Pokud je zásada použita) určuje, že jsou v globální mezipaměť sestavení.  
  
 Kontexty provádění mít výhody a nevýhody, jak je popsáno v následujících částech.  
  
### <a name="default-load-context"></a>Výchozí kontext načtení  
 Pokud jsou načtena do výchozí kontext načtení sestavení, závislé načteny automaticky. Pro sestavení v výchozí kontext načtení nebo načtení z kontextu jsou automaticky nalezeny závislosti, které jsou načteny do výchozí kontext načtení. Načítání sestavení identita zvyšuje stabilitu aplikace tím, že zajistí, že se nepoužívají Neznámá verze sestavení (najdete v článku [vyhnout vazby na částečné názvy sestavení](#avoid_partial_names) části).  
  
 Použití výchozí kontext načtení má tyto nevýhody:  
  
-   Závislosti, které jsou načteny v jiných kontextech nejsou k dispozici.  
  
-   Sestavení nelze načíst z míst mimo testování cestu do výchozí kontext načtení.  
  
### <a name="load-from-context"></a>Načtení z kontextu  
 Načtení z kontextu umožňuje načíst sestavení z cestu, která není v cestě aplikace a proto není zahrnut v zjišťování. Umožňuje závislosti a jejich načíst z cesty, protože informace o cestě se spravuje pomocí kontextu. Kromě toho můžete sestavení v tomto kontextu použít závislosti, které jsou načteny do výchozí kontext načtení.  
  
 Načtení sestavení pomocí <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metoda nebo jednu z metod, které načítají cestou, má tyto nevýhody:  
  
-   Pokud už je načtený, sestavení se stejnou identitou <xref:System.Reflection.Assembly.LoadFrom%2A> vrátí načíst sestavení i v případě, že byl zadán jinou cestu.  
  
-   Pokud je sestavení načíst s <xref:System.Reflection.Assembly.LoadFrom%2A>a později v výchozí kontext načtení sestavení se pokusí načíst do stejného sestavení podle zobrazovaného názvu, zatížení pokus selže. Tato situace může nastat, když je sestavení rekonstruovat.  
  
-   Pokud je sestavení načíst s <xref:System.Reflection.Assembly.LoadFrom%2A>, a testování cesta obsahuje sestavení se stejnou identitou, ale v jiném umístění, <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, nebo může dojít k jiné neočekávanému chování.  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A> Požadavky <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> a <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>, nebo <xref:System.Net.WebPermission>, na zadané cestě.  
  
-   Pokud existuje nativních bitových kopií pro sestavení, se nepoužije.  
  
-   Sestavení nelze načíst jako domény jazykově neutrální.  
  
-   V rozhraní .NET Framework verze 1.0 a 1.1 není použita zásad.  
  
### <a name="no-context"></a>Žádný kontext.  
 Načítání bez kontextu je jedinou možností pro přechodný sestavení, které jsou generovány pomocí reflexe emitování. Načítání bez kontextu je jediný způsob, jak načíst více sestavení, které mají stejnou identitu do domény jednu aplikaci. Náklady na zkušební fáze se vyhnout.  
  
 Sestavení, která jsou načtena z bajtových polí jsou načteny bez kontextu, pokud identita sestavení, které naváže, když je zásada použitá, odpovídá identitě sestavení v globální mezipaměti sestavení; v takovém případě je načteno sestavení z globální mezipaměti sestavení.  
  
 Načtení sestavení bez kontextu má tyto nevýhody:  
  
-   Ostatních sestavení nelze vytvořit vazbu na sestavení, která jsou načtena bez kontextu, pokud zpracováváte <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.  
  
-   Závislosti automaticky nenačtou. Můžete je přednačtení bez kontextu, přednačtení je do výchozí kontext načtení nebo je načíst pomocí zpracování <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.  
  
-   Načtení více sestavení se stejnou identitou bez kontextu může způsobit problémy identity typu podobné těm, které jsou způsobené načtení sestavení se stejnou identitou do více kontexty. V tématu [vyhnout načtení sestavení do více kontexty](#avoid_loading_into_multiple_contexts).  
  
-   Pokud existuje nativních bitových kopií pro sestavení, se nepoužije.  
  
-   Sestavení nelze načíst jako domény jazykově neutrální.  
  
-   V rozhraní .NET Framework verze 1.0 a 1.1 není použita zásad.  
  
<a name="avoid_partial_names"></a>   
## <a name="avoid-binding-on-partial-assembly-names"></a>Vyhněte se vazby na názvy částečného sestavení  
 Vazba částečný název nastane, když zadáte pouze část zobrazovaný název sestavení (<xref:System.Reflection.Assembly.FullName%2A>) při načtení sestavení. Například může zavolat <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda s jednoduchý název sestavení, vynechejte verze, jazykové verze a tokenu veřejného klíče. Nebo může zavolat <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> metoda, která první volání <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda a pokud to nepomůže k nalezení sestavení, vyhledá globální mezipaměti sestavení a načte nejnovější verzi sestavení, která je k dispozici.  
  
 Částečný název vazby může způsobit mnoho problémy, včetně následujících:  
  
-   <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> Metoda může načíst jiném sestavení s stejný jednoduchý název. Například dvě aplikace může nainstalovat dvě úplně jiné sestavení, že mají jednoduchý název `GraphicsLibrary` do globální mezipaměti sestavení.  
  
-   Sestavení, které je ve skutečnosti načteno nemusí být zpětně kompatibilní. Například není určení verze může způsobit načítání mnohem novější verze než verze, že váš program byl původně zapsán používat. Změny v novější verzi může způsobit chyby ve vaší aplikaci.  
  
-   Sestavení, které je ve skutečnosti načteno nemusí být dopřednou. Například můžete mít vytvořené a testovat aplikaci s nejnovější verzí sestavení, ale částečné vazby může načíst mnohem starší verzi, která nemá funkce, které vaše aplikace používá.  
  
-   Instalace nové aplikace může dojít k narušení stávající aplikace. Aplikace, která používá <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metoda možné ho rozdělit nainstalováním novější, nekompatibilní verzi je sdílený sestavení.  
  
-   Může dojít, načítání neočekávané závislostí. Ji načíst tuto sdílenou složku, závislost, jejich načtení se částečné vazby může dojít v jednom sestavení pomocí komponenty, která nebyla dvou sestavení vytvořené nebo testovány s.  
  
 Z důvodu problémů, může to způsobit <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metoda má byly označeny jako zastaralé. Doporučujeme vám, že používáte <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda místo toho a zadejte úplný sestavení zobrazované názvy. V tématu [pochopit výhody a nevýhody zatížení kontextů](#load_contexts) a [zvažte výchozí kontext načtení](#switch_to_default).  
  
 Pokud chcete použít <xref:System.Reflection.Assembly.LoadWithPartialName%2A> metoda vzhledem k tomu, že umožňuje easy, načítání sestavení zvažte, že aplikaci selhat s chybovou zprávu, která identifikuje chybějící sestavení je může zajistit lepší uživatelské prostředí, než automaticky pomocí Neznámá verze sestavení, což by mohlo způsobit nepředvídatelné chování a zabezpečení díry.  
  
<a name="avoid_loading_into_multiple_contexts"></a>   
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Vyhněte se načtení sestavení do více kontexty  
 Načtení sestavení do více kontexty může způsobit problémy identity typu. Pokud je stejný typ načten ze stejného sestavení do dvou různých kontextů, je to, jako kdyby měl načetl dva různé typy se stejným názvem. <xref:System.InvalidCastException> Je vyvolána, pokud se pokusíte převést jeden typ na druhý s matoucí zprávu, která zadejte `MyType` nelze přetypovat na typ `MyType`.  
  
 Předpokládejme například, že `ICommunicate` rozhraní je deklarován v sestavení s názvem `Utility`, který se odkazuje, podle vašeho programu a také podle dalších sestavení, která načte vašeho programu. Tyto další sestavení obsahuje typy, které implementují `ICommunicate` rozhraní, což váš program používat.  
  
 Nyní zvažte, co se stane, když je program spustit. Sestavení, které je odkazováno dle vašeho programu jsou načtena do výchozí kontext načtení. Při načítání sestavení cíl podle svou identitu, pomocí <xref:System.Reflection.Assembly.Load%2A> metoda, bude ve výchozím kontextu zatížení, a proto bude jeho závislé součásti. Váš program a cíl sestavení se bude používat stejné `Utility` sestavení.  
  
 Předpokládejme však, že načtení sestavení cíl podle cesty k souboru pomocí <xref:System.Reflection.Assembly.LoadFile%2A> metoda. Sestavení je načíst bez kontextu, takže jeho závislé součásti nenačtou automaticky. Můžete mít obslužnou rutinu pro <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> může načíst události má poskytnout závislost a `Utility` sestavení s žádný kontext pomocí <xref:System.Reflection.Assembly.LoadFile%2A> metoda. Teď při vytváření instance typu, který je součástí cílového sestavení a pokuste se ji přiřadit proměnné typu `ICommunicate`, <xref:System.InvalidCastException> je vyvolána, protože modul runtime posuzuje `ICommunicate` rozhraní dvě kopie `Utility` sestavení, které má být různých typů.  
  
 Existuje mnoho dalších scénářů, ve kterých může být načtena do více kontexty sestavení. Nejlepším postupem je aby nedocházelo ke konfliktům přemístění cíl sestavení v cestu vaší aplikace a pomocí <xref:System.Reflection.Assembly.Load%2A> metodu se úplný zobrazovaný název. Sestavení je pak načten do výchozí kontext načtení a obě sestavení použít stejné `Utility` sestavení.  
  
 Pokud cílový sestavení musí zůstat mimo cestu vaší aplikace, můžete použít <xref:System.Reflection.Assembly.LoadFrom%2A> metodu pro načtení do načtení z kontextu. Pokud cílový sestavení bylo kompilováno s odkazem k vaší aplikaci `Utility` sestavení, se bude používat `Utility` sestavení, které aplikaci načetl do výchozí kontext načtení. Všimněte si, že problémy může dojít, pokud cílový sestavení je závislý na kopii `Utility` sestavení nacházejících se mimo cestu vaší aplikace. Pokud je toto sestavení načtena do načtení z kontextu před zatížení vaší aplikace `Utility` sestavení, zatížení vaší aplikace se nezdaří.  
  
 [Zvažte přepnutí do kontextu výchozí zatížení](#switch_to_default) část se věnuje alternativy pomocí zatížení cesta k souboru, jako třeba <xref:System.Reflection.Assembly.LoadFile%2A> a <xref:System.Reflection.Assembly.LoadFrom%2A>.  
  
<a name="avoid_loading_multiple_versions"></a>   
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Vyhněte se načtení více verzí sestavení do stejného kontextu  
 Načítání více verzí sestavení do kontextu jeden zatížení může způsobit problémy identity typu. Pokud je stejný typ načten z dvě verze stejného sestavení, je to, jako kdyby měl načetl dva různé typy se stejným názvem. <xref:System.InvalidCastException> Je vyvolána, pokud se pokusíte převést jeden typ na druhý s matoucí zprávu, která zadejte `MyType` nelze přetypovat na typ `MyType`.  
  
 Například váš program může načíst jednu verzi `Utility` sestavení přímo a později ho může načíst jiná sestavení, která načte jinou verzi `Utility` sestavení. Nebo v kódu je chyba může způsobit dvě cesty jiný kód ve vaší aplikaci načíst různé verze sestavení.  
  
 Ve výchozí kontext načtení tento problém může vzniknout při použití <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda a zadejte dokončení sestavení zobrazované názvy, které zahrnují různých čísel verzí. Pro sestavení, které jsou načteny bez kontextu, může být způsobeno problém pomocí <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> metoda načíst do stejného sestavení z jiné cesty. Modul runtime zvažuje dvou sestavení, které jsou načteny z jiné cesty na různých sestavení, i v případě jejich identity.  
  
 Kromě typu identity problémy, může způsobit více verzí sestavení <xref:System.MissingMethodException> Pokud typ, který je načten z jedné verze sestavení je předán kód, který očekává typu z jiné verze. Například kód by se dalo očekávat metoda, která byla přidána na novější verzi.  
  
 Více jemně chyby může dojít, pokud se změní chování typu mezi verzemi. Metoda může být například neočekávanou výjimku nebo vrátit neočekávanou hodnotu.  
  
 Pečlivě zkontrolujte kód a ujistěte se, že pouze jedna je načíst verzi sestavení. Můžete použít <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> metoda k určení, které sestavení jsou načteny v daném okamžiku.  
  
<a name="switch_to_default"></a>   
## <a name="consider-switching-to-the-default-load-context"></a>Zvažte možnost Výchozí kontext načtení  
 Zkontrolujte vzory pro načítání a nasazení sestavení vaší aplikace. Můžete eliminovat sestavení, která jsou načtena z bajtových polí? Můžete přesunout do testování cesta sestavení? Pokud sestavení jsou umístěny v globální mezipaměti sestavení nebo v doméně aplikace je zjišťování cesta (který je jeho <xref:System.AppDomainSetup.ApplicationBase%2A> a <xref:System.AppDomainSetup.PrivateBinPath%2A>), můžete načíst sestavení svou identitu.  
  
 Pokud není možné uvést všechna sestavení v cestě k testování, zvažte možnosti, například pomocí doplňku model rozhraní .NET Framework, umístění sestavení do globální mezipaměti sestavení nebo vytváření domény aplikace.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>Zvažte použití Model doplňku rozhraní .NET Framework  
 Pokud používáte načtení z kontextu pro implementaci doplňků, které nejsou obvykle nainstalovány v základní aplikace, pomocí rozhraní .NET Framework doplňku modelu. Tento model zajišťuje izolaci na úrovni domény nebo proces aplikace bez nutnosti spravovat aplikační domény sami. Informace týkající se modelu najdete v tématu [doplňky a rozšíření](../../../docs/framework/add-ins/index.md).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Zvažte použití globální mezipaměti sestavení  
 Místní sestavení v globální mezipaměti sestavení pro získat výhody sestavení sdílené cesty, která je mimo základ, aplikace bez ztráty výhody výchozí kontext načtení nebo trvá v jiných kontextech nevýhody.  
  
### <a name="consider-using-application-domains"></a>Zvažte použití aplikační domény  
 Pokud určíte, že některé z vašich sestavení nelze nasadit v cestě k testování aplikace, zvažte vytvoření nové domény aplikace pro tyto sestavení. Použijte <xref:System.AppDomainSetup> k vytvoření nové domény aplikace a používat <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> vlastnosti a určit cestu, která obsahuje sestavení, které chcete zatížení. Pokud máte několik adresářů, testovat, můžete nastavit <xref:System.AppDomainSetup.ApplicationBase%2A> kořenový adresář a používání <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> vlastnost k identifikaci podadresáře testovat. Alternativně můžete vytvořit více domén aplikací a nastavit <xref:System.AppDomainSetup.ApplicationBase%2A> jednotlivých domén aplikace příslušné cestě pro jeho sestavení.  
  
 Všimněte si, že můžete použít <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu pro načtení těchto sestavení. Protože teď jsou v cestě k testování, budou načtena do výchozí kontext načtení místo načtení z kontextu. Doporučujeme však, že přejdete na <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodu a zadejte úplné názvy zobrazení sestavení zajistit, že se vždycky použijí správná verze.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>  
 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>  
 [Doplňky a rozšíření](../../../docs/framework/add-ins/index.md)
