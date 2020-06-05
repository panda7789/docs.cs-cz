---
title: Migrace moderních aplikací klasické pracovní plochy
description: Vše, co potřebujete znát o procesu migrace pro moderní desktopové aplikace.
ms.date: 05/12/2020
ms.openlocfilehash: a015b266dc5c36fcef38dad04b9f4f048ee5906a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446915"
---
# <a name="migrating-modern-desktop-applications"></a>Migrace moderních aplikací klasické pracovní plochy

V této kapitole prozkoumáme nejběžnější problémy a problémy, které můžete při migraci existující aplikace z .NET Framework do .NET Core směřovat.

Složitá desktopová aplikace nefunguje v izolaci a potřebuje určitý druh interakce s subsystémy, které se můžou nacházet v místním počítači nebo na vzdáleném serveru. Bude pravděpodobně potřebovat určitý druh databáze pro připojení jako úložiště trvalosti buď místně, nebo vzdáleně. Díky tomu, že jsou architektury zaměřené na Internet a službu, je běžné, že máte aplikaci připojenou k nějakému druhu služby umístěnému na vzdáleném serveru nebo v cloudu. K implementaci některých funkcí může být potřeba mít přístup k systému souborů počítače. Alternativně můžete použít některé funkce, které se nachází v objektu COM mimo vaši aplikaci, což je běžný scénář, pokud například integrujete sestavení Office ve vaší aplikaci.

Kromě toho existují rozdíly v ploše rozhraní API, které jsou zpřístupněny .NET Framework a .NET Core, a některé funkce, které jsou k dispozici v .NET Framework nejsou k dispozici v rozhraní .NET Core. Proto je důležité znát a vzít si je v úvahu při plánování migrace.

## <a name="configuration-files"></a>Konfigurační soubory

Konfigurační soubory nabízejí možnost ukládat sady vlastností, které jsou čteny v době běhu, a ovlivnit chování našich aplikací, například kde najít databázi nebo kolikrát spustit smyčku. Krásy této techniky je, že můžete upravit některé aspekty aplikace bez nutnosti Recode a znovu kompilovat. To je užitečné, když například stejný kód aplikace běží ve vývojovém prostředí s určitou sadou konfiguračních hodnot a v produkčním prostředí s jinou.

### <a name="configuration-on-net-framework"></a>Konfigurace v .NET Framework

Máte-li funkční desktopovou aplikaci .NET Framework, je pravděpodobné, že máte k dispozici soubor *App. config* prostřednictvím <xref:System.Configuration.AppSettingsSection> třídy z `System.Configuration` oboru názvů.

V rámci infrastruktury .NET Framework existuje hierarchie konfiguračních souborů, které dědí vlastnosti z jejích nadřazených prvků. Můžete najít soubor *Machine. config* , který definuje mnoho vlastností a konfiguračních oddílů, které lze použít nebo přepsat v jakémkoli konfiguračním souboru následníka.

### <a name="configuration-on-net-core"></a>Konfigurace v .NET Core

V .NET Core World není k dispozici soubor *Machine. config* . A i když můžete i nadále používat starý <xref:System.Configuration> obor názvů, můžete zvážit přechod na moderní <xref:Microsoft.Extensions.Configuration> , což nabízí dobrý počet vylepšení.

Rozhraní API pro konfiguraci podporuje koncept poskytovatele konfigurace, který definuje zdroj dat, který se má použít k načtení konfigurace. Existují různé druhy integrovaných zprostředkovatelů, například:

- Objekty .NET v paměti
- Soubory INI
- Soubory JSON
- Soubory XML
- Argumenty příkazového řádku
- Proměnné prostředí
- Šifrované úložiště uživatelů

 Můžete si také vytvořit vlastní.

Nová konfigurace umožňuje vytvořit seznam párů název-hodnota, které lze seskupit do hierarchie s více úrovněmi. Veškerá uložená hodnota je mapována na řetězec a je integrována podpora vazby, která umožňuje deserializaci nastavení do vlastního objektu typu objektu CLR (POCO).

<xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>Objekt vám umožňuje přidat tolik poskytovatelů konfigurace, které můžete pro svou aplikaci potřebovat, pomocí pravidla priority můžete vyřešit preference. Proto bude poslední zprostředkovatel, který přidáte do kódu, přepsán ostatními. Jedná se o skvělou funkci pro správu různých prostředí pro provádění, protože můžete definovat různé konfigurace pro vývojové, testovací a produkční prostředí a spravovat je v jedné funkci v rámci vašeho kódu.

### <a name="migrating-configuration-files"></a>Migrace konfiguračních souborů

Můžete dál používat existující soubor App. config XML. Tuto příležitost ale můžete využít k migraci konfigurace, aby bylo možné využít několik vylepšení v .NET Core.

Chcete-li migrovat z původního stylu *App. config* do nového konfiguračního souboru, měli byste zvolit formát XML a formát JSON.

Pokud zvolíte XML, převod je jednoduchý. Vzhledem k tomu, že obsah je stejný, stačí přejmenovat soubor *App. config* na soubor s příponou XML. Pak změňte kód, který odkazuje na AppSettings na použití `ConfigurationBuilder` třídy. Tato změna by měla být snadná.

Pokud chcete použít formát JSON a nechcete migrovat ručně, je k dispozici nástroj [dotnet-config2json](https://www.nuget.org/packages/dotnet-config2json/) v .NET Core, který může převést soubor *App. config* na konfigurační soubor JSON.

Při použití konfiguračních oddílů, které byly definovány v souboru *Machine. config* , může docházet k několika problémům. Zvažte například následující konfiguraci:

```xml
<configuration>
    <system.diagnostics>
        <switches>
            <add name="General" value="4" />
        </switches>
        <trace autoflush="true" indentsize="2">
            <listeners>
                <add name="myListener"
                     type="System.Diagnostics.TextWriterTraceListener,
                           System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
                     initializeData="MyListener.log"
                     traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />
            </listeners>
        </trace>
    </system.diagnostics>
</configuration>
```

Pokud tuto konfiguraci převezmete do .NET Core, zobrazí se výjimka:

Nerozpoznaný konfigurační oddíl System. Diagnostics

K této výjimce dojde, protože tato část a sestavení zodpovědné za zpracování tohoto oddílu byly definovány v souboru *Machine. config* , který nyní neexistuje.

Chcete-li tento problém snadno vyřešit, můžete zkopírovat definici oddílu ze starého souboru *Machine. config* do nového konfiguračního souboru:

```xml
<configSections>
    <section name="system.diagnostics"
             type="System.Diagnostics.SystemDiagnosticsSection,
                   System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
</configSections>
```

## <a name="accessing-databases"></a>Přístup k databázím

Skoro každá desktopová aplikace potřebuje nějaký druh databáze. Pro Desktop je běžné najít architektury klient-server s přímým připojením mezi desktopovou aplikací a databázovým strojem. Tyto databáze mohou být místní nebo vzdálené v závislosti na potřebě sdílení informací mezi různými uživateli.

Z pohledu kódu existovala spousta technologií a platforem, které vývojářům umožňují připojit, dotazovat a aktualizovat databázi.

Nejběžnější příklady databáze, které můžete najít při komunikaci o desktopové aplikaci pro Windows, jsou Microsoft Access a Microsoft SQL Server. Pokud máte více než 20 let programování pro plochu, názvy jako ODBC, OLEDB, RDO, ADO, ADO.NET, LINQ a Entity Framework budou vypadat dobře.

### <a name="odbc"></a>ODBC

V rozhraní .NET Core můžete i nadále používat rozhraní ODBC, protože společnost Microsoft poskytuje `System.Data.Odbc` knihovnu kompatibilní s .NET Standard 2,0.

### <a name="ole-db"></a>OLE DB

[OLE DB](https://docs.microsoft.com/previous-versions/windows/desktop/ms722784(v=vs.85))   byl skvělý způsob, jak přistupovat k různým datovým zdrojům jednotným způsobem. Ale byl založen na modelu COM, což je technologie jenom pro Windows, a to tak, jak nejlíp vyhovuje technologii pro různé platformy, jako je .NET Core. V SQL Server verzích 2014 a novějších je také Nepodporovaná. Z těchto důvodů OLE DB nepodporují rozhraní .NET Core.

### <a name="adonet"></a>ADO.NET

V rozhraní .NET Core můžete nadále používat ADO.NET ze stávajícího kódu na ploše. Potřebujete jenom aktualizovat některé balíčky NuGet.

### <a name="ef-core-vs-ef6"></a>EF Core vs. EF6

K dispozici jsou dvě aktuálně podporované verze Entity Framework (EF) Entity Framework 6 (EF6) a EF Core.

Nejnovější technologie, která byla vydána jako součást .NET Framework World, je Entity Framework, 6,4 má nejnovější verzi. Po spuštění .NET Core společnost Microsoft také vydala novou sadu datových přístupů založenou na Entity Framework a s názvem Entity Framework Core.

Můžete použít EF 6,4 a EF Core z .NET Framework i .NET Core. Jaké jsou tedy rozhodovací ovladače, které vám pomůžou při rozhodování mezi nimi?

EF 6,3 je první verze EF6, kterou je možné spustit na .NET Core a pracovat na různých platformách. Hlavním cílem této verze je, aby bylo snazší migrovat existující aplikace, které používají EF6, do .NET Core.

EF Core byla navržena tak, aby poskytovala vývojářské prostředí podobně jako EF6. Většina rozhraní API nejvyšší úrovně zůstává stejná, takže EF Core se budou dobře rozumět vývojářům, kteří používali EF6.

I když je kompatibilní, existují rozdíly v implementaci, které byste měli před provedením rozhodnutí ověřit.
Další informace najdete v tématu [porovnání EF Core & EF6](/ef/efcore-and-ef6/).

Doporučení je nutné použít EF Core v těchto případech:

* Aplikace potřebuje funkce .NET Core.
* EF Core podporuje všechny funkce, které aplikace vyžaduje.

Zvažte použití EF6, pokud jsou splněny obě následující podmínky:

* Aplikace se spustí v systému Windows a .NET Framework 4,0 nebo novějším.
* EF6 podporuje všechny funkce, které aplikace vyžaduje.

### <a name="relational-databases"></a>Relační databáze

#### <a name="sql-server"></a>SQL Server

SQL Servera jedna z databází, kterou jste si zvolili, pokud jste vývoj pro plochu před několika lety. Při použití v nástroji <xref:System.Data.SqlClient> .NET Framework máte přístup k verzím SQL Server, které zapouzdřují protokoly pro konkrétní databáze.

V rozhraní .NET Core můžete najít novou `SqlClient` třídu, která je plně kompatibilní s existujícím v .NET Framework, ale nachází se v <xref:Microsoft.Data.SqlClient> knihovně. Stačí přidat odkaz na balíček NuGet [Microsoft. data. SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/) a udělat nějaké přejmenování pro obory názvů a vše by mělo fungovat podle očekávání.

#### <a name="microsoft-access"></a>Microsoft Access

Microsoft Access se používá po dobu let, pokud jste propracované a škálovatelné SQL Server nepotřebovali. Ke službě Microsoft Access se stále můžete připojit pomocí <xref:System.Data.Odbc> knihovny.

## <a name="consuming-services"></a>Využívání služeb

Při zvýšení architektury orientovaných na služby začaly aplikace klasické pracovní plochy vyvíjet z modelu klient-server až po tři vrstvy přístupu. V rámci přístupu typu klient-server je z klienta, který uchovává obchodní logiku obvykle v jednom souboru EXE, navázáno přímé připojení k databázi. Na druhé straně přístup ze tří vrstev naváže zprostředkující vrstvu služby implementující obchodní logiku a přístup k databázím, což umožňuje lepší zabezpečení, škálovatelnost a možnosti opětovné použitelnosti. Místo přímé práce s datovými sadami dat závisí přístup k vrstvě v sadě služeb, které implementují kontrakty a typy objektů jako způsob implementace přenosu dat.

Pokud máte desktopovou aplikaci využívající službu WCF a chcete ji migrovat do .NET Core, je třeba zvážit několik věcí.

První věc je způsob, jak vyřešit konfiguraci pro přístup ke službě. Vzhledem k tomu, že se konfigurace liší od .NET Core, budete muset provést některé aktualizace v konfiguračním souboru.

Za druhé budete muset klienta služby znovu vygenerovat novými nástroji, které jsou součástí sady Visual Studio 2019. V tomto kroku je nutné zvážit aktivaci generování synchronních operací, aby byl klient kompatibilní s vaším existujícím kódem.

Pokud zjistíte, že v rozhraní .NET Core existují knihovny, které potřebujete, můžete po migraci přidat odkaz na balíček NuGet [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a zjistit, jestli tam chybí funkce.

Pokud používáte <xref:System.Net.WebRequest> třídu k provádění volání webové služby, můžete najít určité rozdíly v .NET Core. Doporučujeme místo toho použít System .NET. http. HttpClient.

## <a name="consuming-a-com-object"></a>Spotřebovávání objektu COM

V současné době neexistuje způsob, jak přidat odkaz na objekt modelu COM ze sady Visual Studio 2019 pro použití s .NET Core. Proto je nutné ručně upravit soubor projektu.

Vložte `COMReference` strukturu do souboru projektu, jako v následujícím příkladu:

```xml
<ItemGroup>
    <COMReference Include="MSHTML">
        <Guid>{3050F1C5-98B5-11CF-BB82-00AA00BDCE0B}\</Guid>
        <VersionMajor>4</VersionMajor>
        <VersionMinor>0</VersionMinor>
        <Lcid>0</Lcid>
        <WrapperTool>primary</WrapperTool>
        <Isolated>false</Isolated>
    </COMReference>
</ItemGroup>
```

## <a name="more-things-to-consider"></a>Další věci, které je potřeba vzít v úvahu

Pro rozhraní .NET Core není k dispozici několik technologií .NET Framework knihoven. Pokud váš kód spoléhá na některé z těchto technologií, zvažte použití alternativních přístupů popsaných v této části.

[Sada Windows Compatibility Pack](../../core/porting/windows-compat-pack.md) poskytuje přístup k rozhraním API, která byla dříve k dispozici pouze pro .NET Framework. Dá se použít v projektech .NET Core a .NET Standard.

Další informace o kompatibilitě rozhraní API najdete v dokumentaci k zásadním změnám a zastaralým/starším rozhraním API na <https://docs.microsoft.com/dotnet/core/compatibility/fx-core> .

### <a name="appdomains"></a>Objektů třídy AppDomains

Aplikační domény (AppDomains) izolují aplikace od sebe navzájem. Třídy AppDomains vyžadují podporu modulu runtime a jsou nákladné. Vytváření dalších aplikačních domén se nepodporuje. Pro izolaci kódu doporučujeme samostatné procesy nebo jako alternativu použít kontejnery. Pro dynamické načítání sestavení doporučujeme novou  <xref:System.Runtime.Loader.AssemblyLoadContext> třídu.

Aby mohla migrace kódu z .NET Framework snazší, rozhraní .NET Core zpřístupňuje některé z ploch rozhraní API AppDomain. Některá z funkcí rozhraní API obvykle (například  <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType> ), některé členy nedělají nic (například  <xref:System.AppDomain.SetCachePath%2A> ) a některé z nich vyvolají <xref:System.PlatformNotSupportedException> (například  <xref:System.AppDomain.CreateDomain%2A> ).

### <a name="remoting"></a>Vzdálenou

Pro komunikaci mezi doménami AppDomain se použila Vzdálená komunikace .NET, která už není podporovaná. Vzdálená komunikace také vyžaduje běhovou podporu, která je náročná na údržbu. Z těchto důvodů není vzdálená komunikace v .NET podporovaná v .NET Core.

Pro komunikaci mezi procesy byste měli zvážit mechanismus komunikace mezi procesy (IPC) jako alternativu ke vzdálené komunikaci, jako je například <xref:System.IO.Pipes?displayProperty=nameWithType> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> třída nebo.

V různých počítačích použijte jako alternativu řešení založené na síti. Pokud chcete, můžete použít nešifrovaný protokol prostého textu, jako je například HTTP. Webový server Kestrel, který používá ASP.NET Core, je zde možnost.

### <a name="code-access-security-cas"></a>Zabezpečení přístupu kódu (CAS)

Sandboxing, která spoléhá na modul runtime nebo na rozhraní k omezení prostředků, které spravovaná aplikace nebo knihovna používá nebo běží, se v .NET Core nepodporuje.

Používejte hranice zabezpečení poskytované operačním systémem, jako je virtualizace, kontejnery nebo uživatelské účty pro spouštění procesů s minimální sadou oprávnění.

### <a name="security-transparency"></a>Transparentnost zabezpečení

Podobně jako certifikační autorita, transparentnost zabezpečení odděluje kód v izolovaném prostoru z kódu kritického zabezpečení deklarativním způsobem, ale již není podporována jako hranice zabezpečení.

Používejte hranice zabezpečení poskytované operačním systémem, jako je virtualizace, kontejnery nebo uživatelské účty pro spouštění procesů s minimální sadou oprávnění.

>[!div class="step-by-step"]
>[Předchozí](whats-new-dotnet-core.md ) 
> [Další](windows-migration.md)
