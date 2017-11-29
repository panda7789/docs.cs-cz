---
title: "Aplikační domény"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process boundaries for isolation
- application isolation
- application domains, about
- common language runtime, application domains
- application domains
- runtime, application domains
- isolation between applications
- code, verification process
- verification testing code
ms.assetid: 113a8bbf-6875-4a72-a49d-ca2d92e19cc8
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a41a6bf29ec9310d88778b55aa0c27672ba0568
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="application-domains"></a>Aplikační domény
Operační systémy a běhová prostředí obvykle poskytují určitou formu izolace mezi aplikacemi. Například Windows používá procesy k izolování aplikací. Tato izolace je nutné zajistit, že kód spuštěný v jedné aplikaci nemůže mít nepříznivý vliv na jiné nesouvisející aplikace.  
  
 Aplikační domény zadejte hranici izolace, zabezpečení, spolehlivost a správa verzí a uvolnění sestavení. Aplikační domény jsou obvykle vytvoří pomocí modulu runtime hostitelů, které jsou zodpovědní za zavádění modul common language runtime před spuštěním aplikace.  
  
 Témata v této části dokumentace popisují, jak používat k zajištění izolace mezi sestaveními domény aplikace.  
  
 Tento přehled obsahuje následující části:  
  
-   [Výhody izolace aplikací](#benefits)  
  
-   [Referenční dokumentace](#reference)  
  
<a name="benefits"></a>   
## <a name="the-benefits-of-isolating-applications"></a>Výhody izolace aplikací  
 Hranice procesu v minulosti, již byly použity k izolování aplikací, které běží na stejném počítači. Každá aplikace je načten do samostatný proces, který ji izoluje aplikace od dalších aplikací běžících na stejném počítači.  
  
 Aplikace jsou izolovány. vzhledem k tomu, že jsou adresy paměti procesu relativní; ukazatel paměti předaný z jednoho procesu nelze použít v jakékoli smysluplný způsobem tento cílový proces. Kromě toho je možné volat přímo mezi dvěma procesy. Místo toho musíte použít proxy servery, které poskytují úroveň dereference.  
  
 Spravovaný kód musí být předán procesem ověření před spuštěním (pokud správce má oprávnění k přeskočení ověření). Proces ověření určuje, jestli kód se můžete pokusit o přístup k paměti neplatné adresy nebo provádět jiné akce, který by mohl způsobit procesu, ve kterém je spuštěna nemůže pracovat správně. Kód, který projde testem ověření se říká, že bezpečnost typů. Schopnost ověřit kód jako bezpečnost typů umožňuje modul common language runtime poskytovat tak skvělou úroveň izolace jako hranice procesu a v mnohem nižší výkon.  
  
 Aplikační domény zadejte maximalizace zabezpečení a všestranné jednotka zpracování, který modul common language runtime můžete použít k zajištění izolace mezi aplikacemi. Několik domén aplikace můžete spustit v jediném procesu se stejnou úrovní izolace, která by existovat v oddělených procesech, ale bez další režie volání mezi procesy nebo přepínání mezi procesy. Umožňuje spouštění více aplikací v rámci jednoho procesu výrazně zlepšuje škálovatelnost serveru.  
  
 Izolace aplikací je také důležité pro zabezpečení aplikací. Ovládací prvky můžete například spustit z několika webových aplikací v jediném procesu prohlížeče tak, že ovládací prvky přístup k datům a prostředkům.  
  
 Izolace poskytované aplikační domény má následující výhody:  
  
-   Chyby v jedné aplikaci nemůže mít vliv na ostatní aplikace. Protože kód bezpečnost typů nemůže způsobit chyby paměti, používání domén aplikací zajišťuje, že kód spuštěný v jedné doméně nemůže mít vliv na jiné aplikace v procesu.  
  
-   Bez zastavení celý proces se dá zastavit jednotlivých aplikací. Používání domén aplikací umožňuje uvolnit kód spuštěný v jedné aplikaci.  
  
    > [!NOTE]
    >  Nelze uvolnit samostatná sestavení nebo typy. Pouze úplná doména může být odpojen.  
  
-   Kód spuštěný v jedné aplikaci nelze přímo přístupového kódu nebo prostředky z jiné aplikace. Modul common language runtime vynucuje tato izolace brání přímá volání mezi objekty v různých doménách aplikace. Objekty, které předávají mezi doménami jsou zkopírovány nebo zpřístupněny pomocí proxy serveru. Pokud je objekt zkopírován, je místní volání objektu. To znamená volající a odkazovaný objekt jsou ve stejné doméně aplikace. Pokud objekt přistupuje prostřednictvím proxy serveru, volání objektu je vzdálený. V takovém případě volající a odkazovaný objekt jsou v různých doménách aplikace. Volání mezi doménami používat stejnou infrastrukturu vzdálené volání jako volání mezi dvěma procesy nebo mezi dvěma počítači. Metadata pro objekt, který se na ně odkazovat jako takový musí být k dispozici pro obě domény aplikace umožňující volání metody, které chcete být kompilována správně. Pokud volání domény nemá přístup k metadatům pro volaný objekt, kompilace může selhat s výjimkou typu **System.IO.FileNotFound**. V tématu [vzdálených objektů](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58) další podrobnosti. Tento mechanismus pro určení, jak jsou objekty přístupná napříč doménami je určen podle objektu. Další informace naleznete v tématu <xref:System.MarshalByRefObject?displayProperty=nameWithType>.  
  
-   Chování kódu je určeno aplikací, ve které běží. Jinými slovy doménu aplikace obsahuje nastavení konfigurace, jako jsou například zásady verze aplikací, umístění žádné vzdálené sestavení, který přistupuje k a informace o tom, kde najít sestavení, která jsou načtena do domény.  
  
-   Oprávnění udělená kódu se dá nastavit podle domény aplikace, ve kterém kód běží.  
  
  
## <a name="application-domains-and-assemblies"></a>Domény a sestavení aplikací  
 Toto téma popisuje vztah mezi doménami aplikací a sestaveními. Předtím, než můžete spustit kód, který obsahuje, je nutné načíst sestavení do domény aplikace. Spuštění Typická aplikace způsobí, že několik sestavení, které mají být načtena do domény aplikace.  
  
 Způsob, jakým je načteno sestavení určuje, zda jeho v běhu (JIT) zkompilovaný kód může sdílet více domén aplikací v procesu, a zda může být uvolněna z procesu sestavení.  
  
-   Pokud je sestavení načteno-neutrální, udělte všechny domény aplikace, které sdílejí stejné zabezpečení sady můžete sdílet stejný kód kompilována, což snižuje velikost paměti požadované aplikací. Však sestavení může nikdy být uvolněna z procesu.  
  
-   Pokud sestavení není načteno-neutrální, musí být kompilována v každé doméně aplikace, ve kterém je načtena. Sestavení však může být uvolněna z procesu podle uvolnění všechny aplikační domény, ve kterých je načtena.  
  
 Hostitel modulu runtime určuje, zda se načíst sestavení jako neutrální, jakmile se načte modul runtime do procesu. Pro spravované aplikace, použijte <xref:System.LoaderOptimizationAttribute> atribut metodu vstupní bod pro proces a zadejte hodnotu od přidruženého <xref:System.LoaderOptimization> výčtu. Pro nespravované aplikace, které jsou hostiteli modul common language runtime zadejte odpovídající příznak při volání [CorBindToRuntimeEx – funkce](../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) metoda.  
  
 Existují tři možnosti pro načtení domény jazykově neutrální sestavení:  
  
-   <xref:System.LoaderOptimization>načte žádné sestavení jako jazykově neutrální, s výjimkou Mscorlib, které je vždy načteno domény jazykově neutrální. Toto nastavení se nazývá jednu doménu, protože se běžně používá, když na hostiteli běží pouze jednu aplikaci v procesu.  
  
-   <xref:System.LoaderOptimization>načte všechna sestavení jako domény jazykově neutrální. Toto nastavení použijte, pokud je v procesu, všechny spouští stejný kód více domén aplikací.  
  
-   <xref:System.LoaderOptimization>načte sestavení se silným názvem jako neutrální, pokud jejich a všechny jejich závislosti byly nainstalovány v globální mezipaměti sestavení. Další sestavení jsou načtena a kompilována samostatně pro každou doménu aplikace, ve kterém jsou načteny a proto mohou být uvolněna z procesu. Pomocí tohoto nastavení při spuštění více než jednu aplikaci ve stejném procesu, nebo pokud máte směs sestavení, které jsou sdíleny mnoho aplikační domény a sestavení, které musí být uvolněna z procesu.  
  
 Kompilována kód nemůže být sdílen sestavení kontextu, pomocí <xref:System.Reflection.Assembly.LoadFrom%2A> metodu <xref:System.Reflection.Assembly> třídy, nebo z obrazů pomocí přetížení <xref:System.Reflection.Assembly.Load%2A> metoda, která zadejte bajtová pole.  
  
 Sestavení, které byly zkompilovány do nativního kódu pomocí [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) lze sdílet mezi doménami aplikací, v případě, že jsou načtená domény jazykově neutrální prvním načtení do procesu.  
  
 Kompilována kód pro sestavení, které obsahuje vstupní bod aplikace je sdílet pouze v případě, že je možné sdílet jeho závislé součásti.  
  
 Domény jazykově neutrální sestavení může být kompilována více než jednou. Například když zabezpečení udělit nastaví dvě aplikace domény se liší, se nemohou sdílet stejný kód kompilována. Každá kopie sestavení kompilována však lze sdílet s ostatními doménami aplikací, které mají udělenou stejnou sadu.  
  
 Pokud se rozhodnete, jestli se má načíst sestavení jako neutrální, je nutné provést kompromis mezi snižuje využití paměti a dalších faktorů výkonu.  
  
-   Přístup k datům statickou a metody je pomalejší pro domény jazykově neutrální sestavení z důvodu nutnosti izolovat sestavení. Každou doménu aplikace, který přistupuje k sestavení musí mít samostatnou kopii statických dat, aby se zabránilo odkazy na objekty v statických polí překračování hranic domén. V důsledku toho modul runtime obsahuje další logiku k nasměrování volajícího k příslušné kopii statických dat nebo metoda. Tato dodatečná logika zpomaluje volání.  
  
-   Všechny závislosti sestavení musí být umístěn a načtou při sestavení je načteno-neutrální, protože závislost, kterou nelze načíst domény jazykově neutrální brání sestavení načítá domény jazykově neutrální.  
  
## <a name="application-domains-and-threads"></a>Domény aplikace a vlákna  
 Domény aplikace tvoří hranici izolace zabezpečení, správy verzí, spolehlivost a uvolnění spravovaného kódu. Vlákno je konstrukce operační systém používá modul common language runtime ke spouštění kódu. Všechny spravovaného kódu v době běhu je načteno do domény aplikace a spustí jeden nebo více spravovaných vláknech.  
  
 Není k dispozici 1: 1 korelace mezi doménami aplikací a vláken. Několik vláken můžete spustit v jediné doméně aplikace v každém okamžiku a konkrétní vlákno není omezeno na jediné doméně aplikace. To znamená jsou volně hranicemi aplikační domény; vláken nové vlákno se nevytvoří pro každou doménu aplikace.  
  
 V každém okamžiku spustí každých vlákno domény aplikace. Nula, jednu nebo více vláken, může být spuštěno v libovolné doméně aplikace. Čas spuštění uchovává informace o v doménách, které aplikace běží. Můžete vyhledat domény, ve kterém je prováděna vlákno kdykoli voláním <xref:System.Threading.Thread.GetDomain%2A?displayProperty=nameWithType> metoda.  
  
### <a name="application-domains-and-cultures"></a>Aplikační domény a kultury  
 Jazykové verze, která je reprezentována <xref:System.Globalization.CultureInfo> objektu, je přidružen vláken. Jazyková verze, která souvisí s aktuálně prováděné vlákno pomocí můžete získat <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost a můžete získat nebo nastavit jazykovou verzi, která souvisí s aktuálně prováděné vlákno pomocí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnost. Pokud jazykovou verzi, která souvisí s vlákno je pomocí explicitně nastavená <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnost, pokračuje má být přidružena k této přístup z více vláken, když vlákno překračuje hranice domény aplikace. Jinak hodnota jazykové verze, která souvisí s vlákno v každém okamžiku je dáno hodnotu <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> vlastnost v doméně aplikace, ve kterém je prováděna vlákno:  
  
-   Pokud je hodnota vlastnosti není `null`, jazykovou verzi, která je vrácena vlastností souvisí s vlákno (a proto vrácený <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti).  
  
-   Pokud je hodnota vlastnosti `null`, je přidružen vlákno aktuální systémovou kulturu.  
  
## <a name="programming-with-application-domains"></a>Programování pomocí domén aplikace  
 Aplikační domény jsou obvykle vytvoří a manipulovat prostřednictvím kódu programu modulu runtime. Ale někdy aplikační program také chtít pracovat s aplikační domény. Programu aplikace může například načíst komponentu aplikace do domény, aby mohli mít za následek uvolnění domény (a součástí) bez nutnosti zastavení celou aplikaci.  
  
 <xref:System.AppDomain> Je programovací rozhraní pro aplikační domény. Tato třída obsahuje metody pro vytvoření a uvolnění domén, vytváření instancí typy v doménách a k registraci různých upozornění, jako je například uvolnění domény aplikace. Následující tabulka uvádí běžně používané <xref:System.AppDomain> metody.  
  
|Doména AppDomain – metoda|Popis|  
|----------------------|-----------------|  
|<xref:System.AppDomain.CreateDomain%2A>|Vytvoří novou doménu aplikace. Je doporučeno používat přetížení této metody, která určuje <xref:System.AppDomainSetup> objektu. Toto je upřednostňovaný způsob, jak nastavit vlastnosti novou doménu, jako je například základ cesty aplikace nebo kořenový adresář pro aplikaci. umístění konfiguračního souboru pro doménu; a cestu vyhledávání, která je modul common language runtime sloužící k načtení sestavení do domény.|  
|<xref:System.AppDomain.ExecuteAssembly%2A>a<xref:System.AppDomain.ExecuteAssemblyByName%2A>|Spustí sestavení v doméně aplikace. Toto je metoda instance, takže ho můžete použít ke spuštění kódu v jiné doméně aplikace, ke které máte odkaz.|  
|<xref:System.AppDomain.CreateInstanceAndUnwrap%2A>|Vytvoří instanci zadaného typu v doméně aplikace a vrátí proxy server. Tuto metodu použijte, chcete-li se vyhnout načtení sestavení obsahující vytvořený typ do volajícího sestavení.|  
|<xref:System.AppDomain.Unload%2A>|Provede řádné vypnutí domény. Doména aplikace není odpojen, dokud všechny podprocesy spuštěné v doméně byla buď zastavena nebo již nejsou v doméně.|  
  
> [!NOTE]
>  Modul common language runtime nepodporuje serializaci globálních metod, takže delegáti nelze použít k provádění globálních metod v jiných doménách aplikace.  
  
 Nespravovaná rozhraní popsané v modulu common language runtime hostování specifikace rozhraní také poskytnout přístup k aplikační domény. Modul runtime hostitelů můžete použít rozhraní z nespravovaného kódu k vytvoření a získání přístupu k doménám aplikace v rámci procesu.  
  
## <a name="complusloaderoptimization-environment-variable"></a>COMPLUS_LoaderOptimization – proměnná prostředí  
 Proměnná prostředí, která nastaví výchozí zásady optimalizace zavaděč spustitelný soubor aplikace.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
COMPLUS_LoaderOptimization = 1  
```  
  
### <a name="remarks"></a>Poznámky  
 Typická aplikace načte několik sestavení do domény aplikace, aby bylo možné spustit kód, který obsahují.  
  
 Způsob, jakým je načteno sestavení určuje, zda jeho v běhu (JIT) zkompilovaný kód může sdílet více domén aplikací v procesu.  
  
-   Pokud je sestavení načteno-neutrální, všechny domény aplikace, které sdílejí stejnou sadu grant zabezpečení můžete sdílet stejný kód kompilována. Tím se snižuje velikost paměti požadované aplikací.  
  
-   Pokud sestavení není načteno-neutrální, musí být kompilována v každé doméně aplikace, ve kterém je načten a zavaděč nesmí sdílet interním prostředkům napříč doménami aplikací.  
  
 Pokud nastavíte hodnotu 1, vynutí příznak COMPLUS_LoaderOptimization prostředí runtime hostitele k načtení všech sestavení způsobem domény neutrální známé jako SingleDomain. SingleDomain načte žádné sestavení jako jazykově neutrální, s výjimkou Mscorlib, které je vždy načteno domény jazykově neutrální. Toto nastavení se nazývá jednu doménu, protože se běžně používá, když na hostiteli běží pouze jednu aplikaci v procesu.  
  
> [!CAUTION]
>  Příznak COMPLUS_LoaderOptimization prostředí je určen k použití v rámci diagnostiky a testovací scénáře. S příznak zapnutý, můžete způsobit vážné zpomalování a zvýšit využití paměti.  
  
### <a name="code-example"></a>Příklad kódu  
 Vynutit všechna sestavení není možné načíst jako domény jazykově neutrální spustit službu dosáhnout připojením `COMPLUS_LoaderOptimization=1` víceřetězcovou hodnotu v prostředí v klíči HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN.  
  
```  
Key = HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\IISADMIN  
Name = Environment  
Type = REG_MULTI_SZ  
Value (to append) = COMPLUS_LoaderOptimization=1  
```  
  
<a name="reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.MarshalByRefObject?displayProperty=nameWithType>
