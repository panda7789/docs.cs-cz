---
title: "Co je nového v rozhraní .NET Framework"
ms.custom: updateeachrelease
ms.date: 05/02/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d540e3201f0a310641005d95d9c3c0f3dc1d501
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2018
---
# <a name="whats-new-in-the-net-framework"></a>Co je nového v rozhraní .NET Framework
<a name="introduction"></a>Tento článek shrnuje hlavní nové funkce a vylepšení v následujících verzích rozhraní .NET Framework:  
 
[Rozhraní .NET framework 4.7.1](#v471)    
[Rozhraní .NET framework 4.7](#v47)   
[Rozhraní .NET framework 4.6.2](#v462)   
[Rozhraní .NET framework 4.6.1](#v461)   
[Rozhraní .NET 2015 a rozhraní .NET Framework 4.6](#v46)   
[Rozhraní .NET framework 4.5.2](#v452)   
[Rozhraní .NET framework 4.5.1](#v451)   
[Rozhraní .NET framework 4.5](#v45)   

Tento článek neposkytuje komplexní informace o každé nové funkce a mohou podléhat změnám. Obecné informace o rozhraní .NET Framework najdete v tématu [Začínáme](../../../docs/framework/get-started/index.md). Podporované platformy, najdete v části [požadavky na systém](~/docs/framework/get-started/system-requirements.md). Odkazy na stažení a pokyny k instalaci najdete v tématu [Průvodce instalací](../../../docs/framework/install/guide-for-developers.md).

> [!NOTE]
> Tým služby rozhraní .NET Framework uvolní také funkce vzdálené správy s NuGet k rozšíření podpory platformy a zavádět nové funkce, jako je například neměnných kolekcích a podporou SIMD vektoru typy. Další informace najdete v tématu [další knihovny tříd a rozhraní API](../additional-apis/index.md) a [rozhraní .NET Framework a Out-of-Band verze](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md). V tématu [úplný seznam balíčků NuGet](https://blogs.msdn.microsoft.com/dotnet/p/nugetpackages/) pro rozhraní .NET Framework, nebo přihlášení k odběru [náš informační kanál](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).

<a name="v471"></a> 
## <a name="introducing-the-net-framework-471"></a>Představení 4.7.1 rozhraní .NET Framework

Rozhraní .NET Framework 4.7.1 založený na rozhraní .NET Framework 4.6, 4.6.1, 4.6.2 a 4.7 přidáním nové opravy mnoha a několik nových funkcí při zbývající velmi stabilní produktu.

### <a name="downloading-and-installing-the-net-framework-471"></a>Stažení a instalace rozhraní .NET Framework 4.7.1
 
Rozhraní .NET Framework 4.7.1 si můžete stáhnout z těchto míst:

- [Instalační program webové rozhraní .NET framework 4.7.1](http://go.microsoft.com/fwlink/?LinkId=852095)

- [NET Framework 4.7.1 Offline instalačního programu](http://go.microsoft.com/fwlink/?LinkId=852107)

Rozhraní .NET Framework 4.7.1 lze nainstalovat na Windows 10, Windows 8.1, Windows 7 SP1 a odpovídající serverových platforem počínaje systémem Windows Server 2008 R2 SP1. Rozhraní .NET Framework 4.7.1 můžete nainstalovat pomocí instalačního programu webové nebo offline instalačního programu. Doporučený způsob pro většinu uživatelů je použití webovou Instalační službu.

Rozhraní .NET Framework 4.7.1 v sadě Visual Studio 2012 nebo později po instalaci můžete cílit [rozhraní .NET Framework 4.7.1 Developer Pack](http://go.microsoft.com/fwlink/?LinkId=852105). 

### <a name="whats-new-in-the-net-framework-471"></a>Co je nového v rozhraní .NET Framework 4.7.1

Rozhraní .NET Framework 4.7.1 obsahuje nové funkce v těchto oblastech:
 
- [Jádro](#core471)
- [Modul common language runtime (CLR)](#clr)
- [Síťové služby](#net471)
- [ASP.NET](#asp-net471) 

Kromě toho je hlavní fokusu v rozhraní .NET Framework 4.7.1 vylepšení přístupu, který umožňuje aplikaci poskytnout příslušné prostředí pro uživatele technologie usnadnění. Informace o vylepšení přístupnosti v rozhraní .NET Framework 4.7.1 najdete v tématu [co je nového v usnadnění v rozhraní .NET Framework](whats-new-in-accessibility.md). 

<a name="core471" />
#### <a name="core"></a>Jádro

**Podpora pro rozhraní .NET Standard 2.0**

[.NET standard](~/docs/standard/net-standard.md) definuje sadu rozhraní API, která musí být k dispozici na každou implementaci rozhraní .NET, který podporuje tuto verzi standard. Rozhraní .NET Framework 4.7.1 plně podporuje standardní rozhraní .NET 2.0 a přidá [přibližně 200 rozhraní API](https://github.com/dotnet/standard/blob/master/netstandard/src/ApiCompatBaseline.net461.txt) , jsou definovány v rozhraní .NET 2.0 standardní a rozhraní .NET Framework 4.6.1, 4.6.2 a 4.7 chybí. (Všimněte si, že tyto verze rozhraní .NET Framework podporují rozhraní .NET 2.0 standardní pouze v případě, že další soubory podpory aplikace .NET standardní také nasazených v cílovém systému.) Další informace najdete v tématu "BCL – standardní 2.0 podpora v rozhraní .NET" v [Runtime rozhraní .NET Framework 4.7.1 a funkce kompilátoru](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) příspěvku na blogu.

**Podpora pro konfiguraci počítačů**

Konfigurace počítačů umožňují vývojářům vložit a konfigurace nastavení pro aplikace sestavení dynamicky za běhu. Vlastní konfigurace počítačů lze použít k úpravě existující data v konfiguračním oddílu nebo k vytvoření konfigurační sekce úplně od začátku. Bez konfigurace počítačů jsou statické soubory .config a jejich nastavení jsou definovány nějakou dobu, než spustí aplikaci.

Pokud chcete vytvořit vlastní konfigurace tvůrce, odvozujete od abstraktní vaší Tvůrce <xref:System.Configuration.ConfigurationBuilder> třídy a přepsat její <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> a <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>. Také definovat vaše počítačů v souboru .config. Další informace najdete v části "Konfigurace počítačů" v [rozhraní .NET Framework 4.7.1 ASP.NET a konfiguraci funkce](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) příspěvku na blogu. 

**Spuštění funkce zjišťování**

<xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> Třída poskytuje mechanismus pro určení, zda je na daný implementace rozhraní .NET v době kompilace nebo běhu podporován předdefinované funkce. Při kompilaci můžete kompilátor zkontrolujte, zda zadané pole existuje k určení, zda je podporováno funkci; Pokud ano, je generování kódu, který využívá této funkce. V době běhu aplikace může volat <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> metody před vytváření kódu v době běhu. Další informace najdete v tématu [přidejte pomocnou metodu popisující funkce podporovaná modulem runtime](https://github.com/dotnet/corefx/issues/17116).

**Jsou Serializovatelné typy hodnot řazené kolekce členů**

Od verze rozhraní .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> a jeho přidružené obecné typy jsou označeny jako [Serializable](xref:System.SerializableAttribute), což umožňuje binární serializace. To měli migrace řazené kolekce členů typy, jako například <xref:System.Tuple%603> a <xref:System.Tuple%604>, na hodnota řazené kolekce členů typy jednodušší. Další informace najdete v tématu "Kompilátoru – ValueTuple je serializovatelný" v [Runtime rozhraní .NET Framework 4.7.1 a funkce kompilátoru](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) příspěvku na blogu.

**Podpora pro odkazy jen pro čtení**

Rozhraní .NET Framework 4.7.1 přidá <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>. Tento atribut slouží k označení členy, kteří mají návratové typy ref jen pro čtení, nebo parametry kompilátory jazyka. Další informace najdete v tématu "Kompilátoru – podpora pro ReadOnlyReferences" v [Runtime rozhraní .NET Framework 4.7.1 a funkce kompilátoru](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) příspěvku na blogu. Informace o návratové hodnoty ref najdete v tématu [Ref vrátit hodnoty a ref lokální proměnné (C# průvodce)](~/docs/csharp/programming-guide/classes-and-structs/ref-returns.md) a [Ref návratové hodnoty (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr" />
#### <a name="common-language-runtime-clr"></a>Modul common language runtime (CLR)

**Vylepšení výkonu kolekce paměti**

Změny uvolňování paměti (GC) v rozhraní .NET Framework 4.7.1 zvýšit celkový výkon, hlavně pro přidělení haldy velkého objektu (LOH). V rozhraní .NET Framework 4.7.1 samostatné zámky slouží pro malé objektu haldy (SOH) a LOH přidělení, což umožňuje přidělení LOH nastat, když pozadí GC (BGC) je komínů prohlášení o stavu. V důsledku toho aplikací, které velký počet přidělených LOH měli vidět snížení spory uzamčení přidělení a lepší výkon. Další informace najdete v části "Vylepšení výkonu GC – modul Runtime" v [Runtime rozhraní .NET Framework 4.7.1 a funkce kompilátoru](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features/) příspěvku na blogu. 

**Podpora pro přenosné soubory PDB**

Rozhraní .NET Framework, počínaje verzí 4.7.1 podporuje přenosné soubory PDB. Standardní soubory PDB jsou pouze pro systém Windows, přenosné soubory PDB můžete vytvořit a čtení na všech platformách. Ve většině případů je formát souboru pro aplikace běžící na konkrétní implementace rozhraní .NET transparentní. Výjimkou je aplikace, která dynamicky vysílá sestavení za běhu; v takovém případě můžete možnost pro vydávání přenosné PDB nabízejí zlepšení výkonu a redukuje paměti aplikace. 

V době běhu můžete určit, zda přenosné PDB podporují na aktuální implementace rozhraní .NET předáním řetězec "PortablePdb" <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported(System.String)?displayProperty=nameWithType> metoda před generováním sestavení.  
 
<a name="net471"/>
#### <a name="networking"></a>Síťové služby

**Podpora Message.HashAlgorithm SHA-2**

V rozhraní .NET Framework 4.7 a dřívějších verzích <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> hodnot vlastností, které jsou podporovány <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> a <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> pouze. Od verze rozhraní .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, a <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> jsou také podporovány. Tom, jestli tato hodnota se používá ve skutečnosti závisí na služby MSMQ, protože <xref:System.Messaging.Message> samotná instance nemá žádné algoritmu hash, ale na hodnoty jednoduše předává do služby MSMQ. Další informace najdete v části "podpora SHA-2 Message.HashAlgorithm" v [rozhraní .NET Framework 4.7.1 ASP.NET a konfiguraci funkce](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features/) příspěvku na blogu.

<a name="asp-net471" />
#### <a name="aspnet"></a>ASP.NET

**Provedení kroků v aplikacích ASP.NET**

ASP.NET zpracovává požadavky v předdefinované kanál, který zahrnuje 23 události. ASP.NET provede každou obslužnou rutinu události jako krok provádění. Ve verzi technologie ASP.NET až 4.7 rozhraní .NET Framework nejde ASP.NET toku kontext provádění z důvodu přepínání mezi nativní a spravovaná vláken. Místo toho ASP.NET selektivně toků pouze <xref:System.Web.HttpContext>. Od verze rozhraní .NET Framework 4.7.1, <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> metoda také umožňuje moduly vedlejším data obnovit. Tato funkce je zaměřený na knihovny nevadí trasování profilace, diagnostiky nebo transakcí, například, které jsou pro vás o toku spuštění aplikace. Další informace najdete v části "Spuštění krok funkce ASP.NET" v [rozhraní .NET Framework 4.7.1 ASP.NET a konfiguraci funkce](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) příspěvku na blogu. 

**Analýza HttpCookie ASP.NET**

Rozhraní .NET Framework 4.7.1 zahrnuje nové metody, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, poskytuje standardizovaná způsob, jak vytvořit <xref:System.Web.HttpCookie> objekt z řetězce a přesně přiřadit hodnoty souboru cookie, jako je například datum vypršení platnosti a cestu. Další informace najdete v tématu "ASP.NET HttpCookie analýza" v [rozhraní .NET Framework 4.7.1 ASP.NET a konfiguraci funkce](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) příspěvku na blogu. 

**Možnosti hash SHA-2 pro ověřovací pověření formuláře ASP.NET**

V rozhraní .NET Framework 4.7 a starší verze povolené ASP.NET vývojářům ukládat přihlašovací údaje uživatele s hashovaná hesla v konfiguračních souborech použití MD5 nebo SHA1. Od verze rozhraní .NET Framework 4.7.1, ASP.NET podporuje nové zabezpečené možnosti hash SHA-2, například SHA256, SHA384 a SHA512. SHA1 zůstává výchozí a jiné než výchozí šifrovací algoritmus, který lze definovat v konfiguračním souboru webu. Příklad:

```xml
<system.web>
    <authentication mode="Forms">
        <forms loginUrl="~/login.aspx">
          <credentials passwordFormat="SHA512">
            <user name="jdoe" password="6D003E98EA1C7F04ABF8FCB375388907B7F3EE06F278DB966BE960E7CBBD103DF30CA6D61F7E7FD981B2E4E3A64D43C836A4BEDCA165C33B163E6BCDC538A664" />
          </credentials>
        </forms>
    </authentication>
</system.web>
```

<a name="v47"></a> 
### <a name="whats-new-in-the-net-framework-47"></a>Co je nového v 4.7 rozhraní .NET Framework

Rozhraní .NET Framework 4.7 obsahuje nové funkce v těchto oblastech:

- [Jádro](#Core47)
- [Síťové služby](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

Seznam nových rozhraní API se přidá do 4.7 rozhraní .NET Framework, najdete v části [rozhraní .NET Framework 4.7 API změny](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) na Githubu. Seznam vylepšení funkcí a opravy chyb v 4.7 rozhraní .NET Framework, naleznete v části [rozhraní .NET Framework 4.7 změny seznamu](http://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) na Githubu.  Další informace najdete v tématu [uvedení rozhraní .NET Framework 4.7](https://blogs.msdn.microsoft.com/dotnet/2017/04/05/announcing-the-net-framework-4-7/) v blogu .NET.

<a name="Core47" />
#### <a name="core"></a>Jádro

Rozhraní .NET Framework 4.7 zlepšuje serializace pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:

**Rozšířené funkce s šifrování ECC (Elliptic Curve)***

V 4.7 rozhraní .NET Framework `ImportParameters(ECParameters)` metody byly přidány do <xref:System.Security.Cryptography.ECDsa> a <xref:System.Security.Cryptography.ECDiffieHellman> tříd pro povolení pro objekt představující klíčem už vytvořené. `ExportParameters(Boolean)` Metoda se taky přidala pro export klíče pomocí explicitní křivky parametry.

4.7 rozhraní .NET Framework také přidává podporu pro další křivek (včetně suite křivky Brainpool) a přidal předdefinované definice pro snadné vytváření prostřednictvím nové <xref:System.Security.Cryptography.ECDsa.Create%2A> a <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> metodami pro vytváření.

Můžete zobrazit [příklad rozhraní .NET Framework 4.7 kryptografie vylepšení](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) na Githubu.

**Lepší podporu pomocí objektu DataContractJsonSerializer. řídicí znaky**

V 4.7 rozhraní .NET Framework <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serializuje řídicí znaky v souladu s standardní ECMAScript 6. Toto chování je povolené ve výchozím nastavení pro aplikace, které cílí rozhraní .NET Framework 4.7 a je funkce opt-in pro aplikace, které jsou spuštěny rozhraní .NET Framework 4.7 ale cílení na předchozí verzi rozhraní .NET Framework. Další informace najdete v tématu [Změna orientace změny rozhraní .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="net47" />
#### <a name="networking"></a>Síťové služby

Rozhraní .NET Framework 4.7 přidá následující funkce související se sítí:

**Výchozí operační systém podporující protokoly TLS***

Zásobník protokolu TLS, který je používán <xref:System.Net.Security.SslStream?displayProperty=nameWithType> a součásti zásobníku až např. HTTP, FTP a SMTP, umožňuje vývojářům používat protokoly TLS výchozí operačním systémem podporována. Vývojáři nutné žádné delší pevný kódu TLS verze.

<a name="ASP-NET47" />
#### <a name="aspnet"></a>ASP.NET

Technologie ASP.NET v 4.7 rozhraní .NET Framework, obsahuje následující nové funkce:

**Objekt mezipaměti rozšiřitelnosti**

Od verze .NET Framework 4.7, ASP.NET přidá novou sadu rozhraní API, která umožňují vývojářům nahradit výchozí implementace technologie ASP.NET pro ukládání do mezipaměti v paměti objekt a monitorování paměti. Vývojáři, můžete nyní může nahradit některé z následujících tří součástí Pokud implementace technologie ASP.NET není dostatečný:

- **Objekt mezipaměť**. Pomocí nové konfigurační oddíl zprostředkovatelé mezipaměti můžete vývojáři zařadit nové implementace objekt mezipaměti pro aplikaci ASP.NET pomocí nové **ICacheStoreProvider** rozhraní.
 
- **Sledování paměti**. Monitorování paměti výchozí technologie ASP.NET aplikace upozorní, když používají blíží limitu nakonfigurované nesdílených bajtů pro proces, nebo když je počítač má nedostatek celkové dostupné fyzické paměti RAM. Když se blíží tyto limity oznámení při vyvolání. Některé aplikace jsou oznámení aktivována, nakonfigurované limitům umožňující užitečné reakce příliš zavřete. Vývojáři nyní můžete napsat vlastní paměti monitorování nahradit výchozí pomocí <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> vlastnost.

- **Reakce Limit paměti**. Ve výchozím nastavení, technologie ASP.NET pokusí trim mezipaměti objektů a pravidelně volala <xref:System.GC.Collect%2A?displayProperty=nameWithType> po limit soukromých bajtů procesu blízkosti. Některé aplikace, Četnost volání <xref:System.GC.Collect%2A?displayProperty=nameWithType> nebo neefektivní velikost mezipaměti, která je oříznuta. Vývojáři teď můžete nahradit nebo doplnit výchozí chování prostřednictvím registrace **IObserver** implementace monitorování paměti aplikace.

<a name="wcf47" />
#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WFC) přidává tyto funkce a změny:

**Umožňuje nakonfigurovat výchozí nastavení zabezpečení zprávy do protokolu TLS 1.1 a TLS 1.2**

Od verze 4.7 rozhraní .NET Framework, WCF umožňuje nakonfigurovat TSL 1.1 nebo TLS 1.2 kromě SSL 3.0 a TSL 1.0 jako protokol zabezpečení výchozí zpráva. Toto nastavení přihlášení; je ho Pokud chcete zapnout, je nutné přidat následující položku na vašem konfiguračním souboru aplikace:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" /> 
</runtime>
```

**Vylepšení spolehlivosti aplikací WCF a serializace WCF**

WCF zahrnuje několik změn kódu, takže časování, tím lepší výkon a spolehlivost možnosti serializace. Mezi ně patří:

- Lepší podpory pro kombinování kódu v volání asynchronní a synchronní **SocketConnection.BeginRead** a **SocketConnection.Read**.
- Vyšší spolehlivost, pokud přerušení připojení s **SharedConnectionListener** a **DuplexChannelBinder**.
- Zvýšit spolehlivost operací serializace při volání metody <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> metoda.
- Při odebírání číšník voláním zvýšit spolehlivost **ChannelSynchronizer.RemoveWaiter** metoda.

<a name="wf47" />
#### <a name="windows-forms"></a>Windows Forms

Windows Forms v 4.7 rozhraní .NET Framework, zlepšuje podporu pro vysokou monitorování DPI.

**Podpora vysoké DPI**

Počínaje aplikací cílených rozhraní .NET Framework 4.7, rozhraní .NET Framework funkce vysoké DPI a dynamické DPI podporu pro aplikace Windows Forms. Podpora vysoké DPI zvyšuje rozložení a vzhled forms a ovládacích prvků na vysokou monitorování DPI. Dynamické DPI změny rozložení a vzhled formulářů a řídí, když uživatel změní měřítko DPI nebo zobrazení spuštěné aplikace.

Podpora vysoké DPI je výslovný funkce, které nakonfigurujete tak, že definujete [ \<System.Windows.Forms.ConfigurationSection >](../configure-apps/file-schema/winforms/index.md) oddíl v konfiguračním souboru aplikace. Další informace o přidání vysoké DPI podporu a podporu dynamické DPI do aplikace Windows Forms, najdete v části [vysoké DPI podporují ve Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47"></a> 
#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

WPF v 4.7 rozhraní .NET Framework, obsahuje následující vylepšení:

**Podpora pro touch/pera zásobníku, na základě zpráv Windows WM_POINTER**

Nyní máte možnost pomocí touch/pera zásobníku, na základě [WM_POINTER zprávy](https://msdn.microsoft.com/library/windows/desktop/hh454903.aspx) místo systému Windows rukopisu služby platformy BEZDRÁTOVÉHO. Toto je funkce přihlášení v rozhraní .NET Framework. Další informace najdete v tématu [Změna orientace změny rozhraní .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

**Nové implementace pro tisk přes rozhraní API grafický subsystém WPF**

WPF je tisk rozhraní API v <xref:System.Printing.PrintQueue?displayProperty=nameWithType> třída volání Windows [tisk dokumentu balíčku API](https://msdn.microsoft.com/library/windows/desktop/hh448418(v=vs.85).aspx) místo zastaralé [XPS tiskových API](https://msdn.microsoft.com/library/windows/desktop/ff686814(v=vs.85).aspx). Dopad této změny na kompatibilitu aplikací, najdete v části [Změna orientace změny rozhraní .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md). 

<a name="v462"></a> 
## <a name="whats-new-in-the-net-framework-462"></a>Co je nového v rozhraní .NET Framework 4.6.2

[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Obsahuje nové funkce v těchto oblastech:

- [ASP.NET](#ASPNET462)

- [Znak kategorií](#Strings)

- [Kryptografie](#Crypto462)

- [SqlClient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Modelu Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#ClickOnce)

- [Převod na aplikace UWP Windows Forms a aplikace WPF](#UWPConvert)

- [Vylepšení ladění](#Debug462)

Seznam nových rozhraní API se přidá do rozhraní .NET Framework 4.6.2, najdete v části [změny rozhraní API rozhraní .NET Framework 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) na Githubu. Seznam vylepšení funkcí a opravy chyb v rozhraní .NET Framework 4.6.2, naleznete v části [rozhraní .NET Framework 4.6.2 seznamu změny](http://go.microsoft.com/fwlink/?LinkId=708778) na Githubu.  Další informace najdete v tématu [uvedení rozhraní .NET Framework 4.6.2](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/) v blogu .NET.

<a name="ASPNET462"></a> 
### <a name="aspnet"></a>ASP.NET
 V [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ASP.NET obsahuje následující vylepšení:

 **Vylepšená podpora pro lokalizované chybové zprávy v datové poznámky validátory** Data poznámky validátory umožňují provádět ověření můžete přidat jeden nebo více atributů na vlastnost třídy. Atributu <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> element definuje text chybové zprávy, pokud se ověřování nezdaří. Od verze [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ASP.NET usnadňuje lokalizaci chybové zprávy. Pokud bude možné lokalizovat chybové zprávy:

1.  <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> Je součástí ověřovací atribut.

2.  Soubor prostředků je uložen ve složce App_LocalResources.

3.  Název souboru lokalizované prostředky má tvar `DataAnnotation.Localization.{` *název*`}.resx`, kde *název* je název jazykové verze ve formátu *languageCode* `-` *země/regionCode* nebo *languageCode*.

4.  Název klíče prostředku je řetězec přiřazený k <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> atribut a jeho hodnota je lokalizované chybové zprávě.

 Například následující poznámky atribut dat definuje výchozí jazykovou verzi chybovou zprávu pro neplatný hodnocení.

```csharp
public class RatingInfo
{
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]
   [Display(Name = "Your Rating")]
   public int Rating { get; set; }
}
```

```vb
Public Class RatingInfo
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>
   <Display(Name = "Your Rating")>
   Public Property Rating As Integer = 1
End Class
```

 Potom můžete vytvořit soubor prostředků DataAnnotation.Localization.fr.resx, jehož klíč je řetězec chybové zprávy a jehož hodnota je lokalizované chybové zprávě. Soubor je nutné nalézt ve `App.LocalResources` složky. Například následující je klíč a její hodnota v lokalizovaných francouzština (fr) jazyk chybová zpráva:

| Název                                 | Hodnota                                     |
| ------------------------------------ | ----------------------------------------- |
| Hodnocení musí být mezi 1 a 10. | Poznámka: la provedení être tvoří entre 1 et 10. |

 Tento soubor pak můžete

 Kromě toho je rozšiřitelný lokalizace poznámky data. Vývojářům můžete zařadit vlastní řetězec lokalizátora zprostředkovatele implementací <xref:System.Web.Globalization.IStringLocalizerProvider> rozhraní uložení řetězce lokalizace někde jinak než v souboru prostředků.

 **Asynchronní podpora zprostředkovatelům ukládání stavu relace** ASP.NET teď umožňuje vrácení úloh metody pro použití s poskytovatelů úložiště stavu relace, a tím umožní získat výhody škálovatelnost asynchronní aplikace ASP.NET. To podporuje asynchronní operace se stav relace ukládat poskytovatelů, technologie ASP.NET obsahuje nové rozhraní <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, který dědí z <xref:System.Web.IHttpModule> a umožňuje vývojářům implementovat vlastní zprostředkovatele stavu relace modul a asynchronních relace úložiště. Rozhraní je definován následujícím způsobem:

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

 Kromě toho <xref:System.Web.SessionState.SessionStateUtility> třída obsahuje dvě nové metody, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> a <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, který lze použít pro podporu asynchronní operace.

 **Asynchronní podpora poskytovatelů výstupní mezipaměti** začínající [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], úloha vrácení metody můžete použít se výstupní mezipaměti zajistit škálovatelnost výhod asynchronní.  Zprostředkovatelé, kteří implementují tyto metody snížit blokování vlákna na webovém serveru a zlepšit škálovatelnost služby ASP.NET.

 Byly přidány následující rozhraní API pro podporu asynchronní poskytovatelů výstupní mezipaměti:

- <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> Třídy, která dědí z <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> a umožňuje vývojářům implementovat asynchronní poskytovatele výstupní mezipaměti.

- <xref:System.Web.Caching.OutputCacheUtility> Třídy, která poskytuje pomocné metody pro konfiguraci výstupní mezipaměti.

- 18 nové metody v <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> třídy. Mezi ně patří <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, a <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.

- 2 nové metody v <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> – třída: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> a <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.

- 2 nové metody v <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> – třída: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> a <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.

- 2 nové metody v <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> – třída: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> a <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.

- V <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> třídy, <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> metoda.

- V <xref:System.Web.Caching.CacheDependency>, <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> metoda.

<a name="Strings"></a> 
### <a name="character-categories"></a>Znak kategorií
 Znaků [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] jsou klasifikovány podle [standardu Unicode, verze 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/). V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] a [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], znaky byly klasifikovány podle kategorií znaků Unicode 6.3.

 Podpora pro Unicode 8.0 je omezena na klasifikace znaků pomocí <xref:System.Globalization.CharUnicodeInfo> třídy a pro typy a metody, které na ni tedy spoléhat. Patří mezi ně <xref:System.Globalization.StringInfo> třídy, přetížené <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> metody a [znak třídy](../../../docs/standard/base-types/character-classes-in-regular-expressions.md) rozpoznáno modul regulárního výrazu rozhraní .NET Framework.  Znak a řetězec porovnání a řazení je tato změna nemá vliv a nadále spoléhají na příslušný operační systém, nebo na systémech Windows 7, na textová data poskytované rozhraní .NET Framework.

 Změny v kategoriích znak Unicode 6.0 na kódování Unicode 7.0, najdete v části [ve standardu Unicode, verze 7.0.0](http://www.unicode.org/versions/Unicode7.0.0/) na webu Consortium kódování Unicode. Změny z kódování Unicode 7.0 Unicode 8.0, najdete v části [ve standardu Unicode, verze 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/) na webu Consortium kódování Unicode.

<a name="Crypto462"></a> 
### <a name="cryptography"></a>Kryptografie
 **Podpora pro X509 certifikátů obsahujících FIPS 186 3 DSA** [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] přidává podporu pro DSA (digitální podpis algoritmus) X509 certifikáty, jejichž klíče překročit FIPS limit 1024 bitů 186-2.

 Také podporuje větší velikosti klíče standardu FIPS 186-3, [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] umožňuje computing podpisy, řady SHA-2 algoritmů hash (SHA256, SHA384 a SHA512). FIPS 186 3 podpora je k dispozici novými <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> třídy.

 V souladu s posledních změn <xref:System.Security.Cryptography.RSA> třídy v rozhraní .NET Framework 4.6 a <xref:System.Security.Cryptography.ECDsa> – třída v rozhraní .NET Framework 4.6.1, <xref:System.Security.Cryptography.DSA> abstraktní základní třída v [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] má další metody, které umožňují volající využít funkce bez přetypování. Můžete volat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> metodu rozšíření k podepisování dat, jak ukazuje následující příklad.

```csharp
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPrivateKey())
    {
        return dsa.SignData(data, HashAlgorithmName.SHA384);
    }
}
```

```vb 
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()
    Using DSA As DSA = cert.GetDSAPrivateKey()
        Return DSA.SignData(data, HashAlgorithmName.SHA384)
    End Using
End Function
```

 A můžete volat <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> metodu rozšíření k ověření podepsaná data, jak ukazuje následující příklad.

```csharp
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPublicKey())
    {
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);
    }
}
```

```vb
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean
    Using dsa As DSA = cert.GetDSAPublicKey()
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)
    End Using
End Function
```

 **Vyšší přehlednost pro vstupy pro rutiny odvození klíče ECDiffieHellman** rozhraní .NET Framework 3.5 přidala se podpora pro Ellipic křivky Diffie-Hellman klíč smlouvu s tři různé rutiny klíč odvození – funkce (KDF). Vstupy do rutiny a rutiny sami, byly nakonfigurovány pomocí vlastnosti na <xref:System.Security.Cryptography.ECDiffieHellmanCng> objektu. Ale vzhledem k tomu, že ne každé rutiny čtení všech vlastností, vstupní, byl dostatečným místnosti nedorozuměním v minulosti vývojář.

 Chcete-li vyřešit v [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], byly přidány následující tři metody do <xref:System.Security.Cryptography.ECDiffieHellman> základní třída pro více jasně představují tyto rutiny KDF a jejich vstupy:

|ECDiffieHellman – metoda|Popis|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Odvozuje materiál klíče pomocí vzorce<br /><br /> Hodnoty HASH (secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> Hodnota HASH (secretPrepend orelse – *x* orelse – secretAppend)<br /><br /> kde *x* je počítaný výsledkem algoritmu Diffie-Hellman ES.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Odvozuje materiál klíče pomocí vzorce<br /><br /> Metoda HMAC (hmacKey, secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> Metoda HMAC (hmacKey secretPrepend orelse – *x* orelse – secretAppend)<br /><br /> kde *x* je počítaný výsledkem algoritmu Diffie-Hellman ES.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Odvozuje materiál klíče pomocí algoritmu odvození TLS Pseudonáhodná funkce (PRF).|

 **Podpora pro trvalé klíče symetrického šifrování** kryptografie knihovny systému Windows (CNG) přidaná podpora pro ukládání trvalou symetrické klíče a pomocí hardwaru uložené symetrické klíče a [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] mades možné pro vývojáře, aby Pomocí této funkce.  Vzhledem k tomu, že pojem názvy klíčů a klíče zprostředkovatele je specifický pro implementace, použití této funkce vyžaduje využitím konstruktoru konkrétní implementaci typů místo upřednostňované factory přístup (například volání `Aes.Create`).

 Existuje trvalé klíče symetrického šifrování podpora pro AES (<xref:System.Security.Cryptography.AesCng>) a 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algoritmy. Příklad:

```csharp
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)
{
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))
    {
        aes.IV = iv;

        // Using the zero-argument overload is required to make use of the persisted key
        using (ICryptoTransform encryptor = aes.CreateEncryptor())
        {
            if (!encryptor.CanTransformMultipleBlocks)
            {
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");
            }

            return encryptor.TransformFinalBlock(data, 0, data.Length);
        }
    }
}
```

```vb 
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)
        Aes.IV = iv

        ' Using the zero-argument overload Is required to make use of the persisted key
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()
            If Not encryptor.CanTransformMultipleBlocks Then
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

 **Podpora SignedXml algoritmu hash SHA-2** [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] přidá podporu, aby <xref:System.Security.Cryptography.Xml.SignedXml> třídy pro referenční dokumentace SHA256, SHA384 a SHA512 a RSA SHA256, RSA SHA384 a RSA SHA512 PKCS č. 1 podpis metody ověřování algoritmem digest algoritmy.

 Konstanty URI jsou zveřejněné na <xref:System.Security.Cryptography.Xml.SignedXml>:

|SignedXml pole|Konstanta|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Všechny programy, které zapsány vlastní <xref:System.Security.Cryptography.SignatureDescription> obslužnou rutinu do <xref:System.Security.Cryptography.CryptoConfig> přidat podporu pro tyto algoritmy bude i nadále fungovat jako tomu bylo v minulosti, ale vzhledem k tomu, že jsou teď výchozí platformy, <xref:System.Security.Cryptography.CryptoConfig> registrace je už nezbytné.

<a name="SQLClient"></a> 
### <a name="sqlclient"></a>SqlClient
 Zprostředkovatel dat .NET framework pro SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) zahrnuje následující nové funkce [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]:

 **Sdružování připojení a vypršení časových limitů s databází Azure SQL** Pokud je povoleno sdružování připojení a dojde k vypršení časového limitu nebo jiné chybě přihlášení, výjimku se uloží do mezipaměti a uložená v mezipaměti k výjimce při pokusu o všechny následné připojení pro další 5 sekund na 1 minutu.  Další podrobnosti najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).

 Toto chování není žádoucí, pokud připojení k databázím SQL Azure, vzhledem k tomu, že pokusy o připojení může selhat s přechodné chyby, které jsou obvykle obnovit rychle. Pro lepší Optimalizujte opakování rozhraní pro připojení k, Doba blokování připojení fondu, chování je odebrána, pokud dojde k selhání připojení k databázím SQL Azure.

 Přidání nové `PoolBlockingPeriod` – klíčové slovo umožňuje vyberte blokování období nejvhodnější pro vaši aplikaci. Hodnoty:

 `Auto`Je zakázané fondu připojení blokování období pro aplikaci, která se připojuje k databázi SQL Azure a je povolená fondu připojení blokování období pro aplikaci, která se připojuje k jiné instanci serveru SQL Server. Jedná se o výchozí hodnotu. Pokud název koncového bodu serveru skončí s žádným z následujících, jsou považovány za databází SQL Azure:

- . database.windows.net

- . database.chinacloudapi.cn

- . database.usgovcloudapi.net

- . database.cloudapi.de

 `AlwaysBlock`Blokování období fondu připojení je vždy povolena.

 `NeverBlock`Blokování období fondu připojení je k dispozici.

 **Vylepšení funkce Always Encrypted** SQLClient zavádí dvě vylepšení funkce Always Encrypted:

- Pokud chcete zvýšit výkon parametrizované dotazy proti sloupců šifrované databáze, metadata šifrování pro parametry dotazu je nyní v mezipaměti. Pomocí <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> vlastnost nastavena na hodnotu `true` (což je výchozí hodnota), pokud stejný dotaz je volat vícekrát, klient načte metadata parametru ze serveru pouze jednou.

- Sloupec šifrovací klíče položky v mezipaměti klíče jsou nyní vyřazování po nastavitelném časovém intervalu, nastavit pomocí <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> vlastnost.

<a name="WCF"></a> 
### <a name="windows-communication-foundation"></a>Windows Communication Foundation
 V [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Communication Foundation je vylepšená v následujících oblastech:

 **Podpora zabezpečení přenosu WCF pro certifikáty uložené pomocí CNG** zabezpečení přenosu WCF podporuje certifikáty uložené pomocí knihovny kryptografie systému Windows (CNG). V [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], tato podpora je omezena na použití certifikátů s veřejný klíč, který má v délka exponentu delší než 32 služby bits. Pokud aplikace cílena [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], tato funkce je ve výchozím.

 Pro aplikace, které cílí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a starší ale běží na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], tato funkce se dá nastavit tak, že přidáte následující řádek do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části app.config nebo web.config soubor.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

To lze také provést prostřednictvím kódu programu s kódem takto:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

 **Lepší podpora pro více pravidel úpravy letního času v třídě objektu DataContractJsonSerializer** zákazníci mohou používat nastavení konfigurace aplikace k určení zda <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> třída podporuje více úpravy pravidla pro jeden časové pásmo. Toto je funkce přihlášení. Chcete-li ji povolit, přidejte do souboru app.config následující nastavení:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Pokud je tato funkce povolena, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> objektu používá <xref:System.TimeZoneInfo> zadejte místo <xref:System.TimeZone> typ k deserializaci data a času. <xref:System.TimeZoneInfo>podporuje více pravidel úpravy, které umožňuje pracovat s daty historické časové pásmo;   <xref:System.TimeZone> neexistuje.

Další informace o <xref:System.TimeZoneInfo> strukturu a úpravy časové pásmo, najdete v části [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md).

**Podpora pro zachování UTC čas, kdy serializace a deserializace pomocí třídy XMLSerializer** normálně, když <xref:System.Xml.Serialization.XmlSerializer> třída se používá k serializaci UTC <xref:System.DateTime> hodnoty vytvoří řetězec serializovaných čas, který zachovává Datum a čas, ale předpokládá se místní čas.  Například pokud vytvoříte instanci datum a čas UTC voláním následující kód:

```csharp
DateTime utc = new DateTime(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc);
```

```vb
Dim utc As New Date(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc)
```

Výsledkem je řetězec serializovaných čas "03:00:00.0000000-08:00" pro systém osm hodin za čas UTC.  A serializovaných hodnot se vždy deserializovat jako hodnoty místního data a času.

 Nastavení konfigurace aplikace můžete určit, zda <xref:System.Xml.Serialization.XmlSerializer> uchovává informace o časovém pásmu UTC při serializaci a deserializaci <xref:System.DateTime> hodnoty:

```xml 
<runtime>
     <AppContextSwitchOverrides 
          value="Switch.System.Runtime.Serialization.DisableSerializeUTCDateTimeToTimeAndDeserializeUTCTimeToUTCDateTime=false" />
</runtime>
```

Pokud je tato funkce povolena, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> objektu používá <xref:System.TimeZoneInfo> zadejte místo <xref:System.TimeZone> typ k deserializaci data a času. <xref:System.TimeZoneInfo>podporuje více pravidel úpravy, které umožňuje pracovat s daty historické časové pásmo;   <xref:System.TimeZone> neexistuje.

Další informace o <xref:System.TimeZoneInfo> strukturu a úpravy časové pásmo, najdete v části [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md).

 **Nejlepší shodu – NetNamedPipeBinding** WCF má nové nastavení aplikace, které lze nastavit u klientských aplikací, aby vždy připojí ke službě naslouchání v identifikátoru URI, který nejlépe odpovídá ten, který požádají. Při tomto nastavení aplikace nastavte na `false` (výchozí), je možné pro klienty, kteří používají <xref:System.ServiceModel.NetNamedPipeBinding> k pokusu o připojení ke službě, naslouchá na identifikátor URI, který je podřetězcem požadovaný identifikátor URI.

 Například se klient pokusí se připojit k naslouchání služby v `net.pipe://localhost/Service1`, ale jinou službu na tomto počítači spuštěna s oprávněním správce naslouchá na `net.pipe://localhost`. Při tomto nastavení aplikace nastavte na `false`, klient se pokusí připojit k nesprávnou službu. Po nastavení nastavení aplikace nastavte na `true`, klient se vždy připojí k nejlépe odpovídající služby.

> [!NOTE]
>  Klienti, kteří používají <xref:System.ServiceModel.NetNamedPipeBinding> nalezení služeb na základě základní adresa služby (pokud existuje) namísto adresa úplné koncového bodu. Ujistěte se, toto nastavení vždy funguje služba měli použít jedinečnou základní adresu.

 Chcete-li tuto změnu, přidejte následující nastavení aplikace do souboru App.config nebo Web.config klientské aplikace:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

 **Protokol SSL 3.0 není protokol výchozí** po NetTcp pomocí zabezpečení přenosu a typ přihlašovacích údajů certifikátu, SSL 3.0 již není výchozí protokol, který slouží pro vyjednávání zabezpečené připojení. Ve většině případů, měla by existovat žádný vliv na stávající aplikace, protože TLS 1.0 je obsažena v seznamu protokolů pro NetTcp. Všichni existující klienti byste měli mít připojení pomocí na minimálně TLS 1.0. Pokud Ssl3 je potřeba, použijte jednu z následujících mechanismů konfigurace přidat do seznamu vyjednané protokolů.

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> Vlastnost

- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> Vlastnost

- [ \<Přenosu >](../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) části [ \<netTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) části

- [ \<SslStreamSecurity >](../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) části [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) části

<a name="WPF462"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 V [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Presentation Foundation je vylepšená v následujících oblastech:

 **Řazení skupiny** aplikaci, která používá <xref:System.Windows.Data.CollectionView> objektu k seskupení dat můžete nyní explicitně deklarovat jak řadit skupiny. Explicitní řazení adres neintuitivním řazení, které k problému dochází při aplikaci dynamicky přidá nebo odebere skupiny, nebo když se změní hodnotu vlastnosti položky zahrnutých v seskupení. Můžete také zvýšit výkon procesu vytváření skupiny přesunutím porovnávání vlastností seskupení z řazení úplné kolekce řazení skupin.

 Pro podporu řazení skupiny, nové <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> a <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> vlastnosti popisují, jak řadit kolekce skupin vytvářených <xref:System.ComponentModel.GroupDescription> objektu. Toto je obdobou stejně jako s názvem způsob <xref:System.Windows.Data.ListCollectionView> vlastnosti popisují, jak řadit datové položky.

 Dvě nové statické vlastnosti <xref:System.Windows.Data.PropertyGroupDescription> třídy, <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> a <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, lze použít pro nejběžnější případy.

 Například následující data skupiny XAML podle stáří, skupiny stáří ve vzestupném pořadí řazení a seskupit položky v rámci jednotlivých skupin stáří podle příjmení.

```xaml
<GroupDescriptions>
     <PropertyGroupDescription 
         PropertyName="Age" 
         CustomSort= 
              "{x:Static PropertyGroupDescription.CompareNamesAscending}"/>
     </PropertyGroupDescription>
</GroupDescriptions>

<SortDescriptions>
     <SortDescription PropertyName="LastName"/>
</SortDescriptions>
```

 **Softwarová klávesnice podporu** logicky klávesnice podpora umožňuje zaměřit sledování v aplikacích WPF automaticky vyvoláním a zavření nové softwarové klávesnice v systému Windows 10 při stiskem vstup je přijatých ovládacího prvku, který může trvat textový vstup.

 V předchozích verzích rozhraní .NET Framework nemůže aplikace WPF účast v fokus sledování bez zakázání podpory gesto pera/touch WPF.  Aplikace WPF v důsledku toho musíte zvolit plná podpora touch WPF nebo spoléhají na Windows myši povýšení.

 **DPI za monitorování** pro podporu poslední rozšiřování vysokou hodnotou DPI a hybridní DPI prostředí pro aplikace WPF, grafického subsystému WPF v [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] umožňuje sledování na monitorování. Najdete v článku [ukázky a příručka vývojáře](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) na Githubu Další informace o tom, jak povolit aplikaci WPF se za monitorování DPI vědět.

 V předchozích verzích rozhraní .NET Framework jsou aplikace WPF systému hodnotou DPI. Jinými slovy aplikace uživatelského rozhraní je škálovat podle operačního systému podle potřeby, v závislosti na DPI monitorování, na kterém je aplikace vykreslen. ,

 Pro aplikace běžící v rámci [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], můžete přidáním výpis konfigurace, který chcete zakázat DPI za monitorování změn v aplikacích WPF [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) souboru část konfigurace aplikace, následujícím způsobem:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462"></a> 
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)
 V [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], modelu Windows Workflow Foundation je vylepšená v následující oblasti:

 **Podpora pro výrazy jazyka C# a IntelliSense v Návrháři WF Re-hosted** začínající [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], WF podporuje výrazy jazyka C# v obou návrháři sady Visual Studio a v pracovních postupech kódu. Re-hosted návrháře pracovních postupů je klíčovou funkcí WF, které umožňuje návrháře pracovních postupů v aplikaci mimo Visual Studio (například v grafickém subsystému WPF).  Windows Workflow Foundation nabízí možnost podpory výrazy jazyka C# a IntelliSense v Návrháři pracovních postupů Re-hosted. Další informace najdete v tématu [modelu Windows Workflow Foundation blog](http://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409).

 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`Ve verzích rozhraní .NET Framework před verzí [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], IntelliSense návrhář WF je poškozená, pokud zákazník znovu sestaví projekt pracovního postupu ze sady Visual Studio. Při sestavení projektu je úspěšné, typy pracovního postupu nebyly nalezeny v designeru a zobrazí upozornění IntelliSense pro chybějící typy pracovního postupu v **seznam chyb** okno. [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Řeší tento problém a zpřístupní IntelliSense.

 **Pracovní postup aplikace V1 s pracovního postupu pro sledování na nyní spustit v režimu FIPS** počítače s režimu dodržování standardů FIPS povolené teď můžete úspěšně spustit pracovní postup verze 1-style aplikace s pracovním postupem sledování. Chcete-li povolit tento scénář, musíte provést následující změny do souboru app.config:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

 Pokud je tento scénář není povoleno, spuštění aplikace nadále vygeneruje výjimka se zobrazí zpráva "Tato implementace není součástí systému Windows platformy FIPS ověřit kryptografické algoritmy."

 **Vylepšení pracovní postup při používání dynamické aktualizace s návrháři pracovních postupů sady Visual Studio** Návrháři pracovních postupů, Návrhář aktivity vývojový diagram a dalších návrháře aktivit pracovního postupu nyní úspěšně načíst a zobrazit pracovní postupy, které byly uloženy Po volání <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> metoda. Ve verzích rozhraní .NET Framework, než [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], načítání souboru XAML v sadě Visual Studio pro pracovní postup, který byl uložen po volání <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> může mít za následek následující problémy:

- Návrháře pracovních postupů nelze správně načíst soubor XAML (Pokud <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> je na konci řádku).

- Vývojový diagram Návrhář aktivity nebo jiných návrháře aktivit pracovního postupu se může zobrazovat všechny objekty v jejich výchozí umístění a přidružená vlastnost hodnoty.

<a name="ClickOnce"></a> 
### <a name="clickonce"></a>ClickOnce
 ClickOnce aktualizoval na podporu protokolu TLS 1.1 a TLS 1.2 kromě 1.0 protokol, který již podporuje. ClickOnce automaticky rozpozná, protokol, který je vyžadován; žádné další kroky v rámci aplikace ClickOnce jsou požadovány pro povolení TLS 1.1 a 1.2 podporu.

<a name="UWPConvert"></a> 
### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Převod na aplikace UWP Windows Forms a aplikace WPF
 Windows teď nabízí možnosti, aby existující aplikace plochy Windows, včetně aplikace WPF a Windows Forms, pro univerzální platformu Windows (UWP). Tato technologie slouží jako most povolením postupně migraci váš stávající kód základní UPW, a tím přináší vaší aplikace na všech zařízeních s Windows 10.

 Převedený desktopových aplikací získáte identity aplikace, která je podobná identity aplikace UWP aplikací, které umožňuje rozhraní API UWP přístup k povolení funkcí, jako je například Live dlaždice a oznámení. Aplikace nadále chovat jako dříve a spouští jako aplikace úplný vztah důvěryhodnosti. Po převedení aplikace se o proces kontejneru aplikace lze přidat do procesu existující úplný vztah důvěryhodnosti přidat adaptivní uživatelské rozhraní. Pokud všechny funkce je přesunuta do procesu kontejneru aplikací, proces úplný vztah důvěryhodnosti lze odebrat a nové aplikace pro UPW může být dostupné na všech zařízeních s Windows 10.

<a name="Debug462"></a> 
### <a name="debugging-improvements"></a>Vylepšení ladění
 *Nespravovaného rozhraní API pro ladění* má [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] provádět další analýzu při <xref:System.NullReferenceException> je vyvolána, aby bylo možné určit, které proměnná na jediném řádku zdrojový kód je `null`.   Pro podporu tohoto scénáře, byly přidány následující rozhraní API do nespravovaného rozhraní API pro ladění.

- [ICorDebugCode4](../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md), a [ICorDebugVariableHomeEnum](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) rozhraní, které zveřejňují nativní bytech spravované proměnné. To umožňuje ladicí programy udělat některé analýza toku kódu při <xref:System.NullReferenceException> dojde k a zpětně určit spravované proměnné, která odpovídá nativní umístění, která byla `null`.

- [ICorDebugType2::GetTypeID](../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metoda poskytuje mapování pro ICorDebugType k [cor_typeid –](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), což umožňuje ladicí program k získání [cor_typeid –](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bez instance z ICorDebugType. Stávajících rozhraní API na [cor_typeid –](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) lze použít k určení rozložení – třída typu.

<a name="v461"></a> 
## <a name="whats-new-in-the-net-framework-461"></a>Co je nového v rozhraní .NET Framework 4.6.1
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Obsahuje nové funkce v těchto oblastech:

- [Kryptografie](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profilace](#Profile461)

- [NGen](#NGEN461)

 Další informace o [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], najdete v následujících tématech:

- [Rozhraní .NET Framework 4.6.1 seznam změn](http://go.microsoft.com/fwlink/?LinkId=622964)

- [Kompatibilita aplikací v 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

- [.NET Framework API rozdílové](http://go.microsoft.com/fwlink/?LinkId=622989) (na Githubu)

<a name="Crypto"></a> 
### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Šifrování: Podpora pro X509 certifikáty obsahující ECDSA
 Rozhraní .NET Framework 4.6 přidání podpory RSACng pro X509 certifikáty. [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Přidává podporu pro ECDSA (Elliptic Curve Digital algoritmus podpisu) X509 certifikáty.

 ECDSA nabízí lepší výkon a je bezpečnější algoritmus šifrování než RSA, poskytuje ideální volbou kde zabezpečení TLS (Transport Layer) výkon a škálovatelnost je důležité. Implementace rozhraní .NET Framework zabalí volání do stávajících funkcí systému Windows.

 Následující příklad kódu ukazuje, jak je snadné ke generování podpisu pro datový proud bajtů pomocí nové podpory pro ECDSA X 509 certifikáty, které jsou součástí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].

 [!code-csharp[whatsnew.461.crypto#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
 [!code-vb[whatsnew.461.crypto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

 To nabízí označený kontrast kódu potřebné ke generování podpis v rozhraní .NET Framework 4.6.

 [!code-csharp[whatsnew.461.crypto#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
 [!code-vb[whatsnew.461.crypto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461"></a> 
### <a name="adonet"></a>ADO.NET
 Toto jsou přidané do ADO.NET:

 Vždycky šifrovaný podporu pro hardware chráněné klíče ADO.NET nyní podporuje nativně ukládání vždy šifrované sloupce hlavního klíče v modulech hardwarového zabezpečení (HSM). Tato podpora zákazníkům využít asymetrické klíče uložený v modulech HSM, bez nutnosti psaní poskytovatelé úložiště hlavní klíč vlastního sloupce a jejich registrace v aplikacích.

 Zákazníci muset nainstalovat poskytovatele CSP zadaný dodavatele modulu hardwarového zabezpečení nebo poskytovatelů úložiště klíčů CNG na aplikační servery nebo klientské počítače pro přístup vždycky šifrovaná data chráněná pomocí sloupce hlavního klíče uložené v modul HSM.

 Zlepšení <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> připojení chování AlwaysOn SqlClient nyní automaticky poskytuje rychlejší připojení dostupnosti skupin AlwaysOn (AG). Transparentně zjišťuje, jestli vaše aplikace se připojuje ke skupině dostupnosti AlwaysOn (AG) v jiné podsíti a rychle zjistí aktuální aktivní server a poskytuje připojení k serveru. Před touto verzí aplikace bylo potřeba nastavit připojovací řetězec k zahrnují `"MultisubnetFailover=true"` indikující, že se připojení ke skupině dostupnosti AlwaysOn. Bez nastavení – klíčové slovo připojení `true`, aplikaci, může dojít k vypršení časového limitu při připojování ke skupině dostupnosti AlwaysOn. Tato verze aplikace nemá *není* je nutné nastavit <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> k `true` už. Další informace o podpoře SqlClient pro skupiny dostupnosti Always On najdete v tématu [SqlClient podporu pro vysokou dostupnost a zotavení po havárii](../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 Windows Presentation Foundation zahrnují řadu vylepšení a změny.

 Zvýšení výkonu v bylo opraveno zpoždění v aktivaci touch událostí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Kromě toho se zadáním v <xref:System.Windows.Controls.RichTextBox> řízení už blokuje vykreslení vlákno během rychlého vstup.

 Pravopisu kontrola vylepšení, které kontrola pravopisu v grafickém subsystému WPF se aktualizovala na Windows 8.1 a novější verze operačního systému využít podporu pro kontrolu pravopisu další jazyky.  Neexistuje žádné změny ve funkcích v systému Windows verze starší než Windows 8.1.

 Jako v předchozích verzích rozhraní .NET Framework, jazyk <xref:System.Windows.Controls.TextBox> řízení ora <xref:System.Windows.Controls.RichTextBox> bloku se zjišťují pomocí vyhledávání informací v následujícím pořadí:

- `xml:lang`, pokud je k dispozici.

- Aktuální jazyk.

- Jazykové verze aktuálního vlákna.

 Další informace o podpoře jazyků v nástroji WPF, najdete v článku [příspěvek blogu grafického subsystému WPF v rozhraní .NET Framework 4.6.1 funkce](http://go.microsoft.com/fwlink/?LinkID=691819).

 Další podporu pro jednotlivé uživatele vlastní slovníků v [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], WPF rozpozná vlastní slovníky, které jsou registrovány globálně. Tato možnost je k dispozici kromě možnost registrovat, je-control.

 V předchozích verzích WPF vlastní slovník nerozpoznal vyloučené slova a seznamy automatických oprav. Že jsou podporované v Windows 8.1 a Windows 10 prostřednictvím soubory, které se dají umístit pod `%AppData%\Microsoft\Spelling\<language tag>` adresáře.  K těmto souborům platí následující pravidla:

- Soubory by měl mít rozšíření DIC (pro přidání slova), .exc (pro vyloučené slova) nebo ACL (pro automatické opravy).

- Soubory by měl být UTF-16 LE jako prostý text, který začíná značky pořadí bajtů (BOM).

- Každý řádek by měla obsahovat slova (v seznamech přidané a vyloučených word) nebo dvojici automatické opravy s slova oddělená svislá čára ("&#124;") (v seznamu aplikace word automatické opravy).

- Tyto soubory jsou považovány za jen pro čtení a se nemění v systému.

> [!NOTE]
>  Tyto nové formáty souborů přímo nepodporuje rozhraní API kontroly pravopisu WPF a vlastní slovník zadaný do grafického subsystému WPF v aplikacích by měly být nadále používat .lex soubory.

 Ukázky počet [WPF ukázky](https://msdn.microsoft.com/library/ms771633.aspx) na webu MSDN. Více než 200 nejoblíbenější vzorků (na základě jejich využití) bude přesunut do [úložiště GitHub otevřený zdroj](https://github.com/Microsoft/WPF-Samples). Pomozte nám vylepšit naše ukázky nám pošlete žádost o přijetí změn nebo otevírání [potíže Githubu](https://github.com/Microsoft/WPF-Samples/issues).

 Rozšíření rozhraní DirectX zahrnuje WPF [balíček NuGet](http://go.microsoft.com/fwlink/?LinkID=691342) poskytuje nové implementace <xref:System.Windows.Interop.D3DImage> to usnadní můžete spolupracovat s DX10 Dx11 obsahu. Kód pro tento balíček byl open source a je k dispozici [na Githubu](https://github.com/Microsoft/WPFDXInterop).

<a name="WWF461"></a> 
### <a name="windows-workflow-foundation-transactions"></a>Modelu Windows Workflow Foundation: transakce
 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> Metoda můžete nyní používat Správce distribuovaných transakcí než služba MSDTC podporovat transakce. To uděláte tak, že zadáte identifikátor GUID transakce vykonavatel do nového <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> přetížení. Pokud je tato operace úspěšná, existují omezení, které jsou umístěny na možnostech transakce. Jakmile je zařazena vykonavatel transakce jiné služby MSDTC, následující metody throw <xref:System.Transactions.TransactionPromotionException> vzhledem k tomu, že tyto metody vyžadují povýšení ke službě:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

 Jakmile je zařazena vykonavatel transakce jiné služby MSDTC, musíte ho použít pro budoucí zařazení trvanlivý pomocí protokolů, které ho definuje. <xref:System.Guid> Transakce nelze získat vykonavatel pomocí <xref:System.Transactions.Transaction.PromoterType%2A> vlastnost. Pokud transakce zvýší úroveň, poskytuje vykonavatel transakce <xref:System.Byte> pole, které představuje propagovaných token. Aplikaci můžete získat propagovaných token pro jiný MSDTC povýší transakce s <xref:System.Transactions.Transaction.GetPromotedToken%2A> metoda.

 Uživatelé nový <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> přetížení třeba postupovat podle pořadí konkrétní volání v pořadí pro operaci povýšení úspěšně dokončit. Tato pravidla jsou popsané v dokumentaci na metodu.

<a name="Profile461"></a> 
### <a name="profiling"></a>Profilace
 Profilace nespravovaného rozhraní API byla rozšířené následovně:

 Lepší podpora pro přístup k PDB v [ICorProfilerInfo7](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) rozhraní v ASP.Net 5, je čím dál víc společné pro sestavení, které může být kompilované v paměti podle Roslyn. Vývojářům provedení nástrojů pro profilaci to znamená, že soubory PDB, které byly v minulosti serializovány na disku může být už existuje. Soubory PDB Profiler nástrojů často používají pro mapování kódu zpět do zdroje řádků pro úlohy, jako je analýza výkonu pokrytí nebo řádek po řádku kódu. [ICorProfilerInfo7](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) rozhraní teď obsahuje dvě nové metody [ICorProfilerInfo7::GetInMemorySymbolsLength](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) a [ICorProfilerInfo7::ReadInMemorySymbols](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md) , tyto nástroje profileru poskytnout přístup k datům PDB v paměti, pomocí nových rozhraní API, profileru může získat obsah PDB v paměti jako bajtové pole a pak ji zpracovat nebo serializovat na disk.

 Lepší instrumentace s rozhraním ICorProfiler Profilery, které používají `ICorProfiler` ReJit funkce rozhraní API pro dynamické instrumentace nyní můžete upravit některé metadat. Dříve by takové nástroje instrumentace IL kdykoli, ale metadata může upravit pouze v době načtení modulu. Protože IL odkazuje metadata, to omezené druhy instrumentation, které může být provedeno. Budeme mít některé z těchto omezení zrušeno přidáním [ICorProfilerInfo7::ApplyMetaData](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) metoda pro podporu podmnožinu metadata úpravy po modul načte, zejména přidáním nové `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, a `UserString` záznamy. Tato změna umožňuje mnohem širší rozsah ve průběžně instrumentace.

<a name="NGEN461"></a> 
### <a name="native-image-generator-ngen-pdbs"></a>Soubory PDB (NGEN) Generátor nativních bitových kopií
 Trasování událostí mezi počítači umožňuje zákazníkům profilu program na počítači A a podívejte se na data profilování s mapování řádku zdroje na počítači B. používání předchozích verzích rozhraní .NET Framework, uživatel by zkopírujte všechny moduly a nativní bitové kopie z PROFILOVANÉHO počítač analysis počítač, který obsahuje PDB IL vytvořit zdroj nativní mapování. Během tohoto procesu může fungovat i v případě, že soubory jsou relativně malé, například pro telefonní aplikace, soubory může být velmi velké v systémech klientů a vyžadují významné čas potřebný ke kopírování.

 S Ngen PDB můžete vytvořit NGen PDB, který obsahuje mapování IL nativní bez závislosti na IL PDB. V našem scénáři trasování událostí mezi počítači všechno, co je potřeba je zkopírovat nativních bitových kopií PDB, který je generovaný počítače A počítač b a použití [ladění rozhraní API přístup](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) číst IL PDB zdroj IL mapování a nativního bitové kopie na PDB IL nativní mapování. Kombinace obou mapování poskytuje zdroj nativní mapování. Vzhledem k tomu, že nativních bitových kopií PDB je mnohem menší než všechny moduly a nativní bitové kopie, proces kopírování z počítače A počítač b je mnohem rychlejší.

<a name="v46"></a> 
## <a name="whats-new-in-net-2015"></a>Co je nového v rozhraní .NET 2015
 Představuje rozhraní .NET 2015 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] a .NET Core. Některé nové funkce, platí pro obě a další funkce, které jsou specifické pro [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] nebo [!INCLUDE[net_core](../../../includes/net-core-md.md)].

- **ASP.NET 5**

     Rozhraní .NET 2015 zahrnuje ASP.NET 5, který je Štíhlá implementace rozhraní .NET pro vytváření moderní cloudové aplikace. ASP.NET 5 je modulární, takže můžete zahrnout jenom ty funkce, které jsou potřeba v aplikaci. Může být hostované ve službě IIS nebo samoobslužně hostované ve vlastní proces, který a aplikací s různými verzemi nástroje rozhraní .NET Framework můžete spustit na stejném serveru. Zahrnuje nový systém konfigurace prostředí, která je určená pro nasazení cloudu.

     Do jednoho rozhraní nazývá MVC 6 se unified MVC, Web API a webové stránky. Můžete vytvářet aplikace ASP.NET 5 pomocí nových nástrojů v sadě Visual Studio 2015. Existující aplikace budou fungovat na nové rozhraní .NET Framework; ale pokud chcete vytvořit aplikaci, která používá MVC 6 nebo SignalR 3, musí používat systém projektu v sadě Visual Studio 2015.

     Informace najdete v tématu [ASP.NET 5](http://go.microsoft.com/fwlink/?LinkId=518238).

- **Aktualizace ASP.NET**

    - **Založený na úlohách rozhraní API pro vyčištění pro asynchronní odpovědi**

         ASP.NET teď poskytuje jednoduché rozhraní API založené na úlohách vyprázdnění asynchronní odpovědi, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, odpovědi asynchronně zapsány pomocí svůj jazyk, který umožňuje `async/await` podporovat.

    - `Model binding supports task-returning methods`

         V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], přidat funkci vazby modelu, který povolený přístup rozšiřitelný, zaměřené na kód k operace CRUD na základě dat v stránky webových formulářů a uživatelských ovládacích prvků technologie ASP.NET. Teď podporuje vazby modelu systému <xref:System.Threading.Tasks.Task>-vrácení metody vazby modelu. Tato funkce umožňuje webových formulářů vývojářům získat výhody škálovatelnost asynchronní snadno vazby dat systému při použití novější verze ORMs, včetně rozhraní Entity Framework.

         Vazby modelu asynchronní řídí `aspnet:EnableAsyncModelBinding` nastavení konfigurace.

        ```xml
        <appSettings>
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
        </appSettings>
        ```

         Na aplikace, cíl [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], nastaví se jako výchozí `true`. Na aplikace běžící na [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] , cílení na dřívější verzi rozhraní .NET Framework, bude `false` ve výchozím nastavení. Může být povoleno nastavením nastavení konfigurace na `true`.

    - **Podpora protokolu HTTP nebo 2 (Windows 10)**

         [HTTP/2](http://www.wikipedia.org/wiki/HTTP/2) novou verzi protokolu HTTP, která poskytuje mnohem lepší využití připojení (méně odezvy mezi klientem a serverem), výsledkem nižší latenci webové stránky načítání pro uživatele.  Webové stránky (na rozdíl od služby) využívat většinu z HTTP/2, protože protokol optimalizuje pro více artefakty požadovány v rámci jedné prostředí. Byla přidána podpora protokolu HTTP/2 do technologie ASP.NET v rozhraní .NET Framework 4.6. Protože síťových funkcí v několika vrstev existuje, nové funkce nebyly potřeba v systému Windows, služby IIS a ASP.NET povolit HTTP/2. Musíte používat na Windows 10 pomocí protokolu HTTP/2 s technologií ASP.NET.

         HTTP/2 je podporováno také a zapnuto ve výchozím nastavení pro Windows 10 Universal Windows Platform (UWP) aplikace, které používají <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> rozhraní API.

         Aby bylo možné poskytnout způsob, jak používat [PUSH_PROMISE](http://http2.github.io/http2-spec/#PUSH_PROMISE) funkce v aplikacích ASP.NET, nové metody se dvěma přetížení, <xref:System.Web.HttpResponse.PushPromise%28System.String%29> a <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, byl přidán do <xref:System.Web.HttpResponse> – třída.

        > [!NOTE]
        >  I když ASP.NET 5 podporuje protokol HTTP/2, podpora pro funkce nabízené PROMISE nebyl ještě přidán.

         V prohlížeči a webový server (IIS v systému Windows) provádět všechny operace. Nemusíte dělat žádné těžký zrušení pro vaše uživatele.

         Většina [HTTP/2 podporují hlavní prohlížeče](http://www.wikipedia.org/wiki/HTTP/2), takže je pravděpodobné, že vaši uživatelé bude těžit z podpory protokolu HTTP/2, pokud váš server podporuje.

    - **Podpora pro protokol Token vazby**

         Společnost Microsoft a Google mít byla spolupráce na nový přístup k ověřování, volá se [Token vazby protokolu](https://github.com/TokenBinding/Internet-Drafts). Předpokládá se, tokeny ověřování (v mezipaměti vašeho prohlížeče) můžete odcizení a používá podvodníci jinak zabezpečený přístup k prostředkům (třeba účtu bank) bez nutnosti heslo nebo jiné privilegované znalostní báze. Cílem je nový protokol ke zmírnění tohoto problému.

         Token vazby protokolu budou prováděny v systému Windows 10 jako funkce prohlížeče. Aplikace ASP.NET se bude podílet na protokol, aby tokeny ověřování jsou ověřit jako legitimní. Implementace serveru a klienta vytvořit ochranu začátku do konce určeného protokol.

    - **Algoritmy hash náhodnou řetězec**

         Rozhraní .NET Framework 4.5 zavedená [algoritmus hash náhodnou řetězec](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md). Však nebyla podporovaná technologií ASP.NET z důvodu některých ASP.NET funkce závisí na stabilní hodnota hash. V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], náhodnou algoritmů hash řetězce jsou nyní podporovány. Chcete-li povolit tuto funkci, použijte `aspnet:UseRandomizedStringHashAlgorithm` nastavení konfigurace.

        ```xml
        <appSettings>
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
        </appSettings>
        ```

- **ADO.NET**

     ADO .NET teď podporuje funkci Always Encrypted k dispozici v SQL serveru 2016 Community Technology Preview 2 (CTP2). Vždycky šifrovaná SQL Server můžete provádět operace na šifrovaných dat a nejvhodnější šifrovacího klíče se nachází uvnitř důvěryhodného prostředí zákazníka a není na serveru aplikace. Vždy šifrovaný zabezpečuje data zákazníků, DBAs nemají přístup k datům ve formátu prostého textu. Šifrování a dešifrování dat se transparentně odehrává na úrovni ovladače, minimalizovat změny, které má být provedeno do stávajících aplikací mít. Podrobnosti najdete v tématu [vždycky šifrovaná (databázový stroj)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) a [vždycky šifrovaná (vývoj pro klienta)](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **64bitový kompilátor JIT pro spravovaný kód**

     Rozhraní .NET Framework 4.6 funkce novou verzi JIT 64bitový kompilátor (původně označován kódovým RyuJIT). Nové 64bitový kompilátor nabízí výrazné vylepšení výkonu v porovnání s starší 64bitový kompilátor JIT. Nové 64bitový kompilátor je povolený pro 64bitové procesy spuštění na rozhraní .NET Framework 4.6. Vaše aplikace poběží v procesu 64-bit, pokud je kompilován jako 64-bit nebo AnyCPU a běží na 64bitový operační systém. Když má byla pozor na přechod do nové kompilátoru jako průhledná nejblíže, změny v chování je možné. Bychom rádi uslyšíme přímo všechny problémy došlo při použití nové kompilátoru za běhu. Kontaktujte nás prostřednictvím [Microsoft Connect](http://connect.microsoft.com/) Pokud narazíte na potíže, které může souviset s novou JIT kompilátoru 64-bit.

     Nové 64bitový kompilátor JIT také zahrnuje SIMD funkce hardwarové akcelerace při kombinaci s povoleným SIMD typy v <xref:System.Numerics> názvů, který přispět vylepšení dobrý výkon.

- **Vylepšení zavaděč sestavení**

     Zavaděč sestavení teď používá paměť efektivněji a uvolnění sestavení IL po načtení bitovou kopii odpovídající NGEN. Tato změna snižuje virtuální paměti, která je zvlášť vhodné pro velké 32bitové aplikace (například Visual Studio) a navíc šetří fyzické paměti.

- **Základní třída knihovny změny**

     Mnoho nových rozhraní API přidané kolem [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] povolit klíčové scénáře. Mezi ně patří tyto změny a dodatky:

    - **IReadOnlyCollection\<T > Implementace**

         Další kolekce implementovat <xref:System.Collections.Generic.IReadOnlyCollection%601> například <xref:System.Collections.Generic.Queue%601> a <xref:System.Collections.Generic.Stack%601>.

    - **CultureInfo.CurrentCulture a CultureInfo.CurrentUICulture**

         <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnosti jsou teď pro čtení a zápis spíše než jen pro čtení. Chcete-li přiřadit nový <xref:System.Globalization.CultureInfo> objekt, který má tyto vlastnosti definované jazykové verze aktuálního vlákna `Thread.CurrentThread.CurrentCulture` aktuální uživatelského rozhraní a vlastnost vláken definované jazykovou verzi `Thread.CurrentThread.CurrentUICulture` také změnit vlastnosti.

    - **Vylepšení uvolňování paměti (GC)**

         <xref:System.GC> Třída nyní zahrnuje <xref:System.GC.TryStartNoGCRegion%2A> a <xref:System.GC.EndNoGCRegion%2A> metody, které vám umožní zakáže uvolňování paměti během provádění kritické cesty.

         Nové přetížení <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> metoda vám umožní řídit zda malé objektu haldy i velkého objektu haldy jsou, jež jsou a zkomprimovanou nebo pouze, jež jsou.

    - **SIMD povolené typy**

         <xref:System.Numerics> Obor názvů, jako teď obsahuje několik typů SIMD povoleno <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, a <xref:System.Numerics.Vector4>.

         Nové 64bitový kompilátor JIT také zahrnuje funkce hardwarové akcelerace SIMD, a proto zvláště významné zlepšení výkonu při se pomocí nového 64bitový kompilátor JIT SIMD povolené typy.

    - **Aktualizace kryptografie**

         <xref:System.Security.Cryptography?displayProperty=nameWithType> Aktualizovaných rozhraní API pro podporu [kryptografie Windows CNG rozhraní API](https://msdn.microsoft.com/library/windows/desktop/aa376214.aspx). Předchozí verze rozhraní .NET Framework máte zcela na nedoporučujeme využívat [dřívější verzi rozhraní API kryptografie systému Windows](https://msdn.microsoft.com/library/windows/desktop/aa380255.aspx) jako základ pro <xref:System.Security.Cryptography?displayProperty=nameWithType> implementace. Narazili jsme žádosti o podporu rozhraní API CNG vzhledem k tomu, že podporuje [moderní kryptografické algoritmy](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx#suite_b_support), které jsou důležité pro určité skupiny aplikací.

         Rozhraní .NET Framework 4.6 obsahuje následující nové vylepšení pro podporu kryptografie Windows CNG rozhraní API:

        - Sadu rozšiřující metody pro X509 certifikáty, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` a `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, které vrací implementací na základě CNG, nikoli na základě CAPI implementace, pokud je to možné. (Některé čipové karty, atd., stále vyžadují CAPI a zpracování záložní rozhraní API).

        - <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> Třídy, která poskytuje implementaci CNG algoritmu RSA.

        - Vylepšení rozhraní API RSA tak, aby běžné akce už nebudou potřebovat přetypování. Například šifrování dat pomocí <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> objekt vyžaduje kód takto v předchozích verzích rozhraní .NET Framework.

             [!code-csharp[WhatsNew.Casting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
             [!code-vb[WhatsNew.Casting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

             Kód, který využívá šifrování nové rozhraní API v rozhraní .NET Framework 4.6 můžete takto přepsána, aby se zabránilo přetypování.

             [!code-csharp[WhatsNew.Casting#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
             [!code-vb[WhatsNew.Casting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

    - **Podpora pro převod data a časy do nebo z času systému Unix**

         Byly přidány následující nové metody do <xref:System.DateTimeOffset> k podporovat převod hodnoty data a času do nebo z času Unix strukturu:

        - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - **Kompatibility přepínače**

         Nové <xref:System.AppContext> třída přidává nové funkce kompatibility, která umožňuje knihovny zapisovače zajistit uniform výslovný nesouhlas s mechanismus pro nové funkce pro své uživatele. Určuje kontraktu volně vázány mezi součástmi, chcete-li požadavek vyjádření výslovného nesouhlasu s komunikovat. Tato funkce je obvykle důležité při změně na stávající funkce. Naopak už je implicitní opt-in pro nové funkce.

         S <xref:System.AppContext>, definovat knihovny a zveřejněte kompatibility přepínače, při kód, který závisí na nich můžete nastavit tyto přepínače ovlivnit chování knihovny. Ve výchozím nastavení, knihovny přinášejí nové funkce a jejich pouze alter (to znamená, že poskytují předchozí funkce) Pokud je přepínač nastavený.

         Aplikace (nebo knihovnu) můžou deklarovat hodnota přepínače (což je vždy <xref:System.Boolean> hodnotu) definující knihovnu závislé. Přepínač je vždy implicitně `false`. Nastavení přepínače na `true` povolí ho. Explicitně nastavení přepínače na `false` poskytuje nové chování.

        ```csharp
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
        ```

         Knihovny musí zkontrolujte, zda příjemce deklaruje, hodnota přepínače a správně fungovat na něm.

        ```csharp
        if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow)) 
        {
           // This is the case where the switch value was not set by the application. 
           // The library can choose to get the value of shouldThrow by other means. 
           // If no overrides nor default values are specified, the value should be 'false'. 
           // A false value implies the latest behavior.
        }

           // The library can use the value of shouldThrow to throw exceptions or not.
           if (shouldThrow) 
           {
              // old code
           }
           else {
              // new code
           }
        }
        ```

         Je vhodné použít konzistentní formát pro přepínače, protože jsou formální smlouvu vystavené knihovny. Níže jsou uvedeny dva zjevné formáty.

        - *Přepínač*. *obor názvů*. *názevpřepínače*

        - *Přepínač*. *Knihovna*. *názevpřepínače*

    - **Změny se asynchronním vzorem (TAP) založený na úlohách**

         Pro aplikace, které cílí [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], <xref:System.Threading.Tasks.Task> a <xref:System.Threading.Tasks.Task%601> objekty dědí jazykovou verzi a jazykové verze uživatelského nástroje volající vlákno. Chování aplikace, která cílí na předchozích verzích rozhraní .NET Framework, nebo který není zaměřen na konkrétní verzi rozhraní .NET Framework je poškozena. Další informace najdete v části "Jazyková verze nebo založeného na úloze asynchronních operací" <xref:System.Globalization.CultureInfo> třída tématu.

         <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> Třída umožňuje představují vedlejším data, která je místní pro danou asynchronní řízení toku, například `async` metoda. Může sloužit k uchování dat napříč vlákny. Můžete také definovat metoda zpětného volání, která obdrží oznámení při každé změně vedlejším dat, buď protože <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> vlastnost byla explicitně změnit, nebo protože vlákno došlo k přechodu kontextu.

         Tři metody pohodlí <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, byly přidány do založený na úlohách asynchronního vzoru (TAP) vrátit dokončených úloh v určitém stavu.

         <xref:System.IO.Pipes.NamedPipeClientStream> Třída nyní podporuje asynchronní komunikaci pomocí svého nového <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>. Metoda.

    - **EventSource teď podporuje zápis do protokolu událostí**

         Teď můžete použít <xref:System.Diagnostics.Tracing.EventSource> třída protokolu pro správu nebo provozní zprávy do protokolu událostí, kromě pro všechny existující relace trasování událostí pro Windows na počítači vytvořit. V minulosti jste museli používat balíček Microsoft.Diagnostics.Tracing.EventSource NuGet pro tuto funkci. Tato funkce je nyní integrována do rozhraní .NET Framework 4.6.

         Balíček NuGet a rozhraní .NET Framework 4.6 byly aktualizovány s následující funkce:

        - **Dynamické události**

             Umožňuje událostí definovaných "průběžně" bez vytvoření metody události.

        - **Bohaté datové části**

             Umožňuje speciálně s atributy třídy a pole, jakož i primitivní typy, které mají být předány jako datové části

        - **Sledování aktivity**

             Způsobí, že události spuštění a ukončení značky události mezi nimi s Kódem, který reprezentuje všechny aktuálně aktivní aktivity.

         Pro podporu těchto funkcí, přetížené <xref:System.Diagnostics.Tracing.EventSource.Write%2A> metoda byl přidán do <xref:System.Diagnostics.Tracing.EventSource> – třída.

- **Windows Presentation Foundation (WPF)**

    - **Vylepšení HDPI**

         Podpora HDPI v grafickém subsystému WPF je teď lepší v [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Změny byly provedeny na rozložení zaokrouhlení ke snížení instancí výstřižek v ovládacích prvcích s ohraničení. Ve výchozím nastavení, tato funkce je povolená jenom v případě vaší <xref:System.Runtime.Versioning.TargetFrameworkAttribute> je nastaven na rozhraní .NET 4.6.  Aplikace, které cílí na starších verzích rozhraní framework, ale jsou spuštěny na [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] můžete vyjádřit výslovný souhlas pro nové chování přidáním následující řádek do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) v souboru app.config:

        ```xml
        <AppContextSwitchOverrides
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
        />
        ```

         WPF windows tažných více monitorů s různá nastavení DPI (instalace více DPI) jsou nyní úplně vykreslit bez oblasti blacked na více systémů. Toto chování může zamítnutí přidáním následující řádek do `<appSettings>` části soubor app.config a toto chování zakázat:

        ```xml
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>
        ```

         Podpora pro automatické načítání správné kurzor na základě nastavení DPI byl přidán do <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.

    - **Je lepší dotykového ovládání**

         Zákazník hlásí [připojit](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) který touch vytváří odstranily nepředvídatelné chování v [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Dvojité klepněte prahová hodnota pro aplikace pro Windows Store a WPF aplikace je nyní stejné ve Windows 8.1 a vyšší.

    - **Podpora transparentní podřízených oken**

         WPF v [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] podporuje transparentní podřízená okna ve Windows 8.1 a vyšší. Umožňuje vytvořit obdélníkový a transparentní podřízené windows v systému windows. nejvyšší úrovně. Můžete povolit tuto funkci nastavením <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> vlastnost `true`.

- **Windows Communication Foundation (WCF)**

    - **Podpora protokolu SSL**

         WCF teď podporuje SSL verze protokolu TLS 1.1 a TLS 1.2, kromě SSL 3.0 a TLS 1.0, při použití NetTcp s přenos ověřování zabezpečení a klienta. Nyní je možné vybrat protokol, který používat nebo zakažte staré protokoly nižší úrovně zabezpečení. To můžete provést buď nastavením <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> vlastnost nebo vložením následujícího textu do konfiguračního souboru.

        ```xml
        <netTcpBinding>
           <binding>
              <security mode= "None|Transport|Message|TransportWithMessageCredential" >
                 <transport clientCredentialType="None|Windows|Certificate"
                            protectionLevel="None|Sign|EncryptAndSign"
                            sslProtocols="Ssl3|Tls1|Tls11|Tls12">
                    </transport>
              </security>
           </binding>
        </netTcpBinding>
        ```

    - **Odesílání zpráv pomocí různých připojení prostřednictvím protokolu HTTP**

         WCF teď umožňuje uživatelům Ujistěte se, že některé zprávy jsou odesílány s jinou základní připojení protokolu HTTP. Toto lze provést dvěma způsoby:

        - **Pomocí předpony názvu skupiny připojení**

             Uživatelé mohou určit řetězec, který WCF bude používat jako dosáhnout předponu názvu skupiny připojení. Dvě zprávy s jinou předpony se posílají pomocí různých základní připojení protokolu HTTP. Nastavte předponu přidáním dvojici klíč/hodnota na zprávu <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> vlastnost. Klíč je "HttpTransportConnectionGroupNamePrefix"; hodnota je požadovaný předponu.

        - **Použití objektů Factory jiný kanál**

             Uživatele můžete také povolit funkce, která zajišťuje, že zprávy odeslané prostřednictvím kanálů vytvořit objekty pro vytváření jiný kanál použije jiný základní připojení protokolu HTTP. Chcete-li povolit tuto funkci, uživatelé musí nastavit následující `appSetting` k `true`:

            ```xml
            <appSettings>
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
            </appSettings>
            ```

- **Modelu Windows Workflow Foundation (WWF)**

     Nyní můžete určit počet sekund, po které služby pracovního postupu bude obsahovat na žádost o operaci pořadí se na více systémů, když dojde nezpracovaných záložek (bez protocol) před vypršením časového limitu požadavku. Záložka (bez protocol) je záložka, která nesouvisí se zbývající Receive aktivity. Některé aktivity vytvořit jiný protokol záložky v jejich provedení, proto nemusí být zřejmé, zda existuje jiný protokol záložky. Mezi ně patří, stavu a vybrat. Pokud máte implementováno s stavový stroj služby pracovních postupů nebo jste obsahující vybrat aktivity, bude s největší pravděpodobností proto máte jiný protokol záložky. Zadejte interval přidáním jako následující řádek `appSettings` části souboru app.config:

    ```xml
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
    ```

     Výchozí hodnota je 60 sekund. Pokud `value` je nastaven na hodnotu 0, se na pořadí požadavky byly zamítnuty okamžitě s porucha text, který vypadá takto:

    ```
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees. 
    ```

     Toto je stejná zpráva, která se zobrazí, pokud je doručena zpráva operace mimo pořadí a neobsahuje žádné jiný protokol záložky.

     Pokud hodnota `FilterResumeTimeoutInSeconds` element je nulová, jsou záložky jiný protokol a interval vypršení časového limitu vyprší, operace selže se zprávou časový limit.

- **Transakce**

     Nyní můžete zahrnout identifikátor distribuované transakce pro transakci, která způsobila výjimku odvozené z <xref:System.Transactions.TransactionException> vyvolání. To uděláte tak, že přidáte následující klíč `appSettings` části souboru app.config:

    ```xml
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/> 
    ```

     Výchozí hodnota je `false`.

- **Síťové služby**

    - **Opakované použití soketů**

         Windows 10 zahrnují nový vysokou škálovatelnost sítě algoritmus, který umožňuje lepší využití prostředků počítače opětovným použitím místní porty pro odchozí připojení TCP. Rozhraní .NET Framework 4.6 podporuje algoritmus nové povolení aplikace .NET, abyste mohli využívat nové chování. V předchozích verzích Windows bylo umělé souběžných připojení limit (obvykle 16384, výchozí velikost rozsahu dynamický port), který může omezit škálovatelnost služby tím, že na portu vyčerpání během zatížení.

         V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], byly přidány dva nové rozhraní API umožňující opakované použití portu, které efektivně odebere 64 tisíc limitu souběžných připojení:

        - <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> Hodnota výčtu.

        - <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> Vlastnost.

         Ve výchozím nastavení <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> vlastnost je `false` Pokud `HWRPortReuseOnSocketBind` hodnotu `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` klíč registru je nastavené na 0x1. Chcete-li povolit opakované použití místního portu na připojení prostřednictvím protokolu HTTP, nastavte <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> vlastnost `true`. To způsobí, že všechny odchozí připojení TCP soketu z <xref:System.Net.Http.HttpClient> a <xref:System.Net.HttpWebRequest> použít novou možnost soketu Windows 10, [SO_REUSE_UNICASTPORT](https://msdn.microsoft.com/library/windows/desktop/ms740532.aspx), která umožňuje opakované použití místního portu.

         Můžete zadat vývojáře, kteří vytvářejí aplikace jen sockets <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> možnost při volání metody, jako <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> tak, aby odchozí sockets znovu použít místní porty během vazby.

    - **Podpora mezinárodních názvů domén a PunyCode**

         Nové vlastnosti <xref:System.Uri.IdnHost%2A>, byl přidán do <xref:System.Uri> třída lepší podpory mezinárodních názvů domén a PunyCode.

- **Změna velikosti v ovládacích prvcích Windows Forms.**

     Tato funkce se rozšířila v [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] zahrnout <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> a <xref:System.Windows.Forms.ToolStripSplitButton> typy a rámeček určeného <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> vlastnost použitá při kreslení <xref:System.Drawing.Design.UITypeEditor> .

     Toto je funkce přihlášení. Chcete-li ji povolit, nastavte `EnableWindowsFormsHighDpiAutoResizing` element `true` v souboru aplikace (app.config) konfigurace:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Podpora pro kódování kódu stránky**

      [!INCLUDE[net_core](../../../includes/net-core-md.md)] primarily supports the Unicode encodings and by default provides limited support for code page encodings. You can add support for code page encodings available in the .NET Framework but unsupported in [!INCLUDE[net_core](../../../includes/net-core-md.md)] by registering code page encodings with the <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> method. For more information, see <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

     Aplikace pro Windows pro Windows 10 cílených [!INCLUDE[net_core](../../../includes/net-core-md.md)] a jsou napsané v C# nebo Visual Basic můžete využít výhod novou technologií kompilovaný aplikace do nativního kódu, nikoli IL. Vytvářejí charakteristické rychlejší spuštění a časy spuštění aplikace. Další informace najdete v tématu [kompilování aplikací pomocí .NET Native](../../../docs/framework/net-native/index.md). Přehled .NET Native která prověřuje, jak se liší od JIT – kompilace a NGEN a jaké, která znamená kódu, najdete v části [.NET Native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md).

     Aplikace jsou zkompilovány do nativního kódu ve výchozím nastavení při kompilaci s Visual Studiem 2015. Další informace najdete v tématu [Začínáme s .NET Native](../../../docs/framework/net-native/getting-started-with-net-native.md).

     Pro podporu ladění rozhraní .NET nativní aplikace, počet nové rozhraní a výčty jsou přidané do nespravovaného rozhraní API pro ladění. Další informace najdete v tématu [ladění (referenční dokumentace nespravovaného rozhraní API)](../../../docs/framework/unmanaged-api/debugging/index.md) tématu.

- **Open-source balíčky rozhraní .NET Framework**

      [!INCLUDE[net_core](../../../includes/net-core-md.md)] packages such as the immutable collections, [SIMD APIs](http://go.microsoft.com/fwlink/?LinkID=518639), and networking APIs such as those found in the <xref:System.Net.Http> namespace are now available as open source packages on [GitHub](https://github.com/). To access the code, see [NetFx on GitHub](http://go.microsoft.com/fwlink/?LinkID=518634). For more information and how to contribute to these packages, see [.NET Core and Open-Source](../../../docs/framework/get-started/net-core-and-open-source.md), [.NET Home Page on GitHub](http://go.microsoft.com/fwlink/?LinkID=518635).

 [Zpět na začátek](#introduction)

<a name="v452"></a> 
## <a name="whats-new-in-the-net-framework-452"></a>Co je nového v rozhraní .NET Framework 4.5.2

- **Nová rozhraní API pro aplikace ASP.NET.** Nové <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> a <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> metody umožňují kontrolovat a upravovat hlavičky odpovědi a stavový kód jako odpověď se vyprazdňuje do klientské aplikace. Zvažte použití těchto metod místo <xref:System.Web.HttpApplication.PreSendRequestHeaders> a <xref:System.Web.HttpApplication.PreSendRequestContent> události jsou účinnější a spolehlivější.

     <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> Metoda umožňuje naplánovat malé pozadí pracovní položky. ASP.NET sleduje tyto položky a zabrání náhle ukončení pracovního procesu, dokud všechny pracovní položky pozadí dokončili služby IIS. Tuto metodu nelze volat mimo doménu spravovanou aplikaci ASP.NET.

     Nové <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> a <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> vlastnosti vracejí logické hodnoty, které označuje, zda byla zapsána hlavičky odpovědi. Můžete použít tyto vlastnosti a ujistěte se, jako například volání rozhraní API <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (který generování výjimek, pokud byla zapsána hlavičky) bude úspěšné.

- **Změna velikosti v ovládacích prvcích Windows Forms.** Tato funkce se rozšířila. Nyní můžete nastavení DPI systému ke změně velikosti součástí tyto doplňkové ovládací prvky (například šipku rozevíracího seznamu v polích se seznamem):

     <xref:System.Windows.Forms.ComboBox>    <xref:System.Windows.Forms.ToolStripComboBox>    <xref:System.Windows.Forms.ToolStripMenuItem>    <xref:System.Windows.Forms.Cursor>    <xref:System.Windows.Forms.DataGridView>    <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

     Toto je funkce přihlášení. Chcete-li ji povolit, nastavte `EnableWindowsFormsHighDpiAutoResizing` element `true` v souboru aplikace (app.config) konfigurace:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Nové funkce.** Správce prostředků, který používá <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> – metoda (a proto implementace <xref:System.Transactions.IPromotableSinglePhaseNotification> rozhraní) použít novou <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> metoda požádat o následující:

    - Umožňuje zvýšit úroveň transakce Transaction Microsoft Distributed Transaction Coordinator služba MSDTC ().

    - Nahraďte <xref:System.Transactions.IPromotableSinglePhaseNotification> s <xref:System.Transactions.ISinglePhaseNotification>, což je trvanlivý zařazení, podporující jediné fázi potvrzení.

     To lze provést v rámci stejné domény aplikace a nevyžaduje žádné velmi nespravovaného kódu k interakci se služby MS DTC k povýšení. Nové metodu lze volat pouze v případě, že je zbývající volání ze <xref:System.Transactions?displayProperty=nameWithType> k <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` metoda, která je implementováno modulem možné zvýšit zařazení.

- **Profilace vylepšení.** Následující nové nespravované profilaci API poskytují robustnější profilace:

     [Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) [výčet Cor_prf_high_monitor](../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) [metoda GetAssemblyReferences](../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) [metoda GetEventMask2](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) [Metoda SetEventMask2](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) [metoda AddAssemblyReference](../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

     Předchozí `ICorProfiler` implementace podporované opožděného načítání závislá sestavení. Nové rozhraní API pro profilaci vyžadují závislá sestavení, které jsou vloženy profileru být načíst okamžitě, místo načítá po kompletní inicializaci aplikace. Tato změna nemá vliv uživatelé existující `ICorProfiler` rozhraní API.

- **Vylepšení ladění.** Následující nové nespravované ladění rozhraní API nabízí lepší integraci s profileru. Je možné nyní přístup metadata vložená profileru a také místní proměnné a kódu vytvořeného kompilátoru ReJIT požadavky při vypsat ladění.

     [Metoda SetWriteableMetadataUpdateMode](../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) [metoda EnumerateLocalVariablesEx](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) [metoda GetLocalVariableEx](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) [metoda GetCodeEx](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) [Metoda GetActiveReJitRequestILCode](../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md) [metoda GetInstrumentedILMap](../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Událost trasování změny.** Rozhraní .NET Framework 4.5.2 umožňuje trasování mimo proces, na základě trasování událostí pro Windows ETW aktivit pro větší útoku. To umožňuje dodavatelům Advanced Power Management (APM) poskytují jednoduché nástroje, které lépe sledovat náklady na jednotlivých požadavků a aktivity, které zasahují vláken.  Tyto události jsou vyvolány pouze v případě, že je; povolit řadiče trasování událostí pro Windows změny proto neovlivní dříve napsané ETW kód nebo kód, který běží s ETW zakázána.

- **Podpora transakcí a převodu na trvanlivý zařazení**

     <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType>nové rozhraní API přidání do rozhraní .NET Framework 4.5.2 a 4.6:

    ```csharp
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                              IPromotableSinglePhaseNotification promotableNotification,
                                              ISinglePhaseNotification enlistmentNotification,
                                              EnlistmentOptions enlistmentOptions)
    ```

     Metoda může být používán zařazení, která byla dříve vytvořená <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> v reakci <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> metoda. Požádá `System.Transactions` podporovat transakce transakce služby MS DTC a "převést" zařazení možné zvýšit na trvanlivý zařazení. Po úspěšném dokončení tato metoda <xref:System.Transactions.IPromotableSinglePhaseNotification> rozhraní bude odkazovat už `System.Transactions`, a všechny budoucí oznámení budou doručeny na zadaných <xref:System.Transactions.ISinglePhaseNotification> rozhraní. V zařazení musí fungovat jako trvanlivý zařazení, podpora protokolování transakcí a obnovení. Odkazovat na <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> podrobnosti. Kromě toho musí podporovat zařazení <xref:System.Transactions.ISinglePhaseNotification>.  Tato metoda může *pouze* volat při zpracování <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> volání. Pokud se nejedná o případ, <xref:System.Transactions.TransactionException> je vyvolána výjimka.

 [Zpět na začátek](#introduction)

<a name="v451"></a> 
## <a name="whats-new-in-the-net-framework-451"></a>Co je nového v rozhraní .NET Framework 4.5.1
 **Aktualizace. dubna 2014**:

- [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658) obsahuje aktualizace knihovny přenosných tříd šablon pro podporu těchto scénářích:

    - Můžete použít rozhraní API systému Windows Runtime v přenosné knihovny, které cílí na Windows 8.1, Windows Phone 8.1 a Windows Phone Silverlight 8.1.

    - Můžete zahrnout XAML (Windows.UI.XAML typy) přenosné knihovny k identifikaci Windows 8.1 nebo Windows Phone 8.1. Jsou podporovány následující šablony XAML: prázdná stránka, slovník prostředků, Šablonované řízení a uživatelský ovládací prvek.

    - Můžete vytvořit komponentu přenosného prostředí Windows Runtime (soubor .winmd) pro použití v aplikacích pro Store, které se zaměřují na Windows 8.1 a Windows Phone 8.1.

    - Můžete změnit cíl Windows Store nebo Windows Phone Store knihovny tříd jako přenosné knihovny tříd.

     Další informace o těchto změnách najdete v tématu [Přenosná knihovna tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- Rozhraní .NET Framework obsah nastavit teď obsahuje dokumentaci [!INCLUDE[net_native](../../../includes/net-native-md.md)], což je předkompilace technologie pro vytváření a nasazování aplikací pro Windows. [!INCLUDE[net_native](../../../includes/net-native-md.md)]zkompiluje aplikace přímo do nativního kódu, nikoli do převodního jazyka (IL) pro dosažení vyššího výkonu. Podrobnosti najdete v tématu [kompilování aplikací pomocí .NET Native](../../../docs/framework/net-native/index.md).

- [Zdroje referenční dokumentace rozhraní .NET Framework](http://referencesource.microsoft.com/) poskytuje nové možnosti procházení a rozšířené funkce. Teď můžete procházet zdrojový kód rozhraní .NET Framework online, [odkaz na stažení](http://referencesource.microsoft.com/download.html) pro zobrazení v režimu offline a projděte zdroje (včetně oprav a aktualizací) během ladění. Další informace naleznete v příspěvku blogu [nový vzhled pro rozhraní .NET odkaz na zdroj](https://blogs.msdn.microsoft.com/dotnet/2014/02/24/a-new-look-for-net-reference-source/).

 Hlavní nové funkce a vylepšení v rozhraní .NET Framework 4.5.1 patří:

- Automatického přesměrování vazby pro sestavení. Počínaje [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], když zkompilujete aplikaci, která cílí [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], přesměrování vazby mohou být přidány do konfiguračního souboru aplikace Pokud vaše aplikace nebo jeho součástí odkazovat více verzí stejného sestavení. Můžete také povolit tuto funkci pro projekty, které používají starší verze rozhraní .NET Framework. Další informace najdete v tématu [postupy: povolení a zakázání automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

- Schopnost shromažďovat diagnostické informace, což vývojářům zvýšit výkon serveru a cloudové aplikace. Další informace najdete v tématu <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> a <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> metody v <xref:System.Diagnostics.Tracing.EventSource> třídy.

- Schopnost explicitně compact velkého objektu haldy (LOH) během uvolňování paměti. Další informace najdete v tématu <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> vlastnost.

- Vylepšení výkonu další například pozastavení aplikace ASP.NET, vylepšení JIT více jader a rychlejší spuštění aplikace po rozhraní .NET Framework aktualizovat. Podrobnosti najdete v tématu [rozhraní .NET Framework 4.5.1 oznámení](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/) a [aplikace ASP.NET pozastavit](https://blogs.msdn.microsoft.com/dotnet/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting/) příspěvku na blogu.

 Vylepšení Windows Forms zahrnují:

- Změna velikosti v ovládacích prvcích Windows Forms. Nastavení DPI systému můžete použít ke změně velikosti součásti ovládacích prvků (například ikony, které se zobrazují v tabulce vlastností) podle vyjádření výslovného pomocí položku v konfiguračním souboru aplikace (app.config) pro vaši aplikaci. Tato funkce je aktuálně podporována v následujících ovládací prvky Windows Forms:

     <xref:System.Windows.Forms.PropertyGrid>    <xref:System.Windows.Forms.TreeView>Některé aspekty <xref:System.Windows.Forms.DataGridView> (viz [nové funkce ve verzi 4.5.2](#v452) pro další ovládací prvky podporované)

     Chcete-li povolit tuto funkci, přidejte nový \<appSettings > element do konfiguračního souboru (app.config) a nastavte `EnableWindowsFormsHighDpiAutoResizing` element `true`:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

 Vylepšení při ladění aplikace rozhraní .NET Framework v [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] zahrnují:

- Návratové hodnoty v ladicím programu sady Visual Studio. Když ladíte spravované aplikaci v [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], v okně se zobrazí automobily vrátit typy a hodnoty pro metody. Tyto informace jsou k dispozici pro stolní počítače, Windows Store a Windows Phone aplikace. Další informace najdete v tématu [vyhledejte návratových hodnot volání metod](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f\(v=vs.120\).aspx) v knihovně MSDN.

- Upravit a pokračovat pro 64bitové aplikace. [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]podporuje funkce upravit a pokračovat pro 64bitové spravované aplikace pro stolní počítače, Windows Store a Windows Phone. Existující omezení zůstávají v platnosti pro 32bitové a 64bitové verze aplikace (naleznete v části poslední [podporované změny kódu (C#)](/visualstudio/debugger/supported-code-changes-csharp) článku).

- Podporující asynchronní ladění. Aby bylo snazší ladit asynchronní aplikace v [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], zásobník volání skryje kód infrastruktury poskytované kompilátory pro podporu asynchronní programování a také řetězy v logické nadřazené rámce, můžete postupovat podle logické programu provádění více jasně. Okno úlohy nahradí okno paralelních úloh a zobrazí úlohy, které se vztahují ke konkrétní zarážek a také další úlohy, které jsou aktuálně aktivní nebo naplánované v aplikaci. Další informace o této funkci v části "podporující asynchronní ladění" [rozhraní .NET Framework 4.5.1 oznámení](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/).

- Lepší podporu výjimky pro součásti režimu Runtime systému Windows. V [!INCLUDE[win81](../../../includes/win81-md.md)], výjimky, které vznikají z aplikace pro Windows Store zachovat informace o této chybě, který způsobil výjimku, i přes hranice jazyk. Další informace o této funkci v části "Vývoj aplikací pro Windows Store" [rozhraní .NET Framework 4.5.1 oznámení](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/). 

 Počínaje [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], můžete použít [spravované profil na základě nástroj pro optimalizaci (Mpgo.exe)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md) za účelem optimalizace [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace a také aplikace klasické pracovní plochy.

 Nové funkce technologie ASP.NET 4.5.1, najdete v části [ASP.NET 4.5.1 a Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) na webu technologie ASP.NET.

 [Zpět na začátek](#introduction)

<a name="v45"></a> 
## <a name="whats-new-in-the-net-framework-45"></a>Co je nového v rozhraní .NET Framework 4.5

### <a name="core-new-features-and-improvements"></a>Hlavní nové funkce a vylepšení

- Umožňuje snížit systému restartuje zjišťuje a zavírání aplikací rozhraní .NET Framework 4 během nasazení. V tématu [omezení restartů systému při instalaci rozhraní .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md).

- Podpora pro pole, které jsou větší než 2 gigabajty (GB) na 64bitových platformách. Tato funkce se dá nastavit v konfiguračním souboru aplikace. Najdete v článku [ \<gcallowverylargeobjects – > element](../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), který také uvádí další omezení na velikost objektu a velikost pole.

- Lepší výkon díky pozadí uvolňování paměti pro servery. Pokud používáte server uvolňování paměti v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kolekce paměti na pozadí se automaticky povolí. Najdete v části kolekce paměti na pozadí serveru [základy uvolnění paměti](../../../docs/standard/garbage-collection/fundamentals.md) tématu.

- Kompilace v běhu (JIT) pozadí, která je volitelně k dispozici u vícejádrových procesorů pro zvýšení výkonu aplikací. V tématu <xref:System.Runtime.ProfileOptimization>.

- Možnost omezení jak dlouho modul regulárních výrazů se pokusí přeložit regulární výraz, než vyprší časový limit. Najdete v článku <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> vlastnost.

- Schopnost definovat výchozí jazykovou verzi pro doménu aplikace. Najdete v článku <xref:System.Globalization.CultureInfo> třídy.

- Podpora kódování Unicode (UTF-16) konzoly. Najdete v článku <xref:System.Console> třídy.

- Podpora pro správu verzí porovnání a řazení dat kulturního řetězec. Najdete v článku <xref:System.Globalization.SortVersion> třídy.

- Lepší výkon při načítání prostředků. V tématu [balení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Vylepšení komprese ZIP ke snížení velikosti komprimovaný soubor. Najdete v článku <xref:System.IO.Compression?displayProperty=nameWithType> oboru názvů.

- Schopnost přizpůsobit reflexe kontextu přepsat výchozí chování reflexe prostřednictvím <xref:System.Reflection.Context.CustomReflectionContext> třídy.

- Podpora pro verze 2008 aplikace (IDNA) mezinárodních názvů domén v případě standardní <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> třída se používá na [!INCLUDE[win8](../../../includes/win8-md.md)].

- Delegování porovnání řetězců do operačního systému, která implementuje 6.0 znakové sady Unicode, pokud rozhraní .NET Framework se používá na [!INCLUDE[win8](../../../includes/win8-md.md)]. Při spuštění na jiných platformách, rozhraní .NET Framework obsahuje vlastní řetězec porovnání data, která implementuje Unicode 5.x. Najdete v článku <xref:System.String> třídy a části poznámky <xref:System.Globalization.SortVersion> třídy.

- Schopnost na výpočetní kódů hash pro řetězce na základě domény aplikace. V tématu [ \<userandomizedstringhashalgorithm – > Element](../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Zadejte podporu reflexe rozdělit mezi <xref:System.Type> a <xref:System.Reflection.TypeInfo> třídy. V tématu [reflexe v rozhraní .NET Framework pro aplikace Windows Store](../../../docs/framework/reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Managed Extensibility Framework (MEF) obsahuje následující nové funkce:

- Podpora pro obecné typy.

- Založené na konvenci programovací model, který umožňuje vytvářet částí podle konvence pojmenování spíše než atributy.

- Víc oborů.

- Podmnožinu rozhraní MEF, který můžete použít při vytváření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace. Tato část je k dispozici jako [ke stažení balíčku](http://go.microsoft.com/fwlink/?LinkId=256238) z Galerie NuGet. Chcete-li nainstalovat balíček, otevřete projekt v sadě Visual Studio, zvolte **spravovat balíčky NuGet** z **projektu** nabídce a vyhledejte online `Microsoft.Composition` balíčku.

 Další informace najdete v tématu [Managed Extensibility Framework (MEF)](../../../docs/framework/mef/index.md).

### <a name="asynchronous-file-operations"></a>Operace asynchronní souborů
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], nový asynchronní funkce byly přidány do jazyků C# a Visual Basic. Tyto funkce přidání modelu založený na úlohách pro provádění asynchronní operace. Tento nový model, použití asynchronních metod v třídách vstupně-výstupní operace. V tématu [vstupně-výstupní asynchronní](../../../docs/standard/io/asynchronous-file-i-o.md).

<a name="tools"></a> 
### <a name="tools"></a>Nástroje
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Generátor zdrojových souborů (Resgen.exe) můžete vytvořit soubor .resw pro použití v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací ze souboru .resources vložených v sestavení rozhraní .NET Framework. Další informace najdete v tématu [Resgen.exe (Generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).

 Spravované profil optimalizace (Mpgo.exe) umožňuje vylepšit doba spuštění aplikace, využití paměti (velikost pracovní sady) a propustnost optimalizace sestavení nativních bitových kopií. Nástroj příkazového řádku generuje data profilu pro sestavení aplikace nativních bitových kopií. V tématu [Mpgo.exe (nástroj pro optimalizaci na základě spravované profilu)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Počínaje [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], Mpgo.exe můžete použít k optimalizaci [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace a také aplikace klasické pracovní plochy.

<a name="parallel"></a> 
### <a name="parallel-computing"></a>Paralelní výpočty.
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Poskytuje několik nových funkcí a vylepšení pro paralelní výpočty. Mezi ně patří lepší výkon, zvýšená řízení, vylepšenou podporou pro asynchronní programování, Nová knihovna toku dat a vylepšenou podporou pro paralelní ladění a analýza výkonu. Naleznete v příspěvku [co je nového pro paralelismus v rozhraní .NET 4.5](http://go.microsoft.com/fwlink/?LinkId=235061) v paralelní programování s blogu .NET.

<a name="web"></a> 
### <a name="web"></a>Web
 ASP.NET 4.5 a 4.5.1 přidat vazby modelu webových formulářů, podporu protokolu WebSocket, asynchronní obslužné rutiny, vylepšení výkonu a řadu dalších funkcí. Další informace naleznete v následujících materiálech:

- [ASP.NET 4.5 a Visual Studio 2012](http://msdn.microsoft.com/library/ac9bb7f6-f094-4af7-bad0-acf49a5dbc55) v knihovně MSDN.

- [ASP.NET 4.5.1 a Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) na webu technologie ASP.NET.

<a name="networking"></a> 
### <a name="networking"></a>Síťové služby
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Poskytuje nové programovací rozhraní pro aplikace HTTP. Další informace najdete v tématu nové <xref:System.Net.Http?displayProperty=nameWithType> a <xref:System.Net.Http.Headers?displayProperty=nameWithType> obory názvů.

 Podpora je rovněž obsažena pro nové programovací rozhraní pro přijímání a interakci s připojení protokolu WebSocket pomocí stávající <xref:System.Net.HttpListener> a související třídy. Další informace najdete v tématu nové <xref:System.Net.WebSockets> obor názvů a <xref:System.Net.HttpListener> třídy.

 Kromě toho [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] obsahuje následující vylepšení sítě:

- Podpora kompatibilní s RFC identifikátoru URI. Další informace najdete v tématu <xref:System.Uri> a související třídy.

- Podpora pro analýzu mezinárodní název domény (IDN). Další informace najdete v tématu <xref:System.Uri> a související třídy.

- Podpora pro e-mailovou adresu internacionalizace (EAI). Další informace najdete v tématu <xref:System.Net.Mail> oboru názvů.

- Vylepšená podpora protokolu IPv6. Další informace najdete v tématu <xref:System.Net.NetworkInformation> oboru názvů.

- Podpora duálních soketu. Další informace najdete v tématu <xref:System.Net.Sockets.Socket> a <xref:System.Net.Sockets.TcpListener> třídy.

<a name="client"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Windows Presentation Foundation (WPF) obsahuje změny a vylepšení v následujících oblastech:

- Nové <xref:System.Windows.Controls.Ribbon.Ribbon> řízení, které umožňuje implementovat uživatelské rozhraní pásu karet, který je hostitelem nástrojů Rychlý přístup, nabídku aplikace a karty.

- Nové <xref:System.ComponentModel.INotifyDataErrorInfo> rozhraní, která podporuje ověřování dat synchronní a asynchronní.

- Nové funkce <xref:System.Windows.Controls.VirtualizingPanel> a <xref:System.Windows.Threading.Dispatcher> třídy.

- Lepší výkon při zobrazení velkého nastaví seskupené dat a přístupu k kolekce na non-UI vláken.

- Datové vazby k statické vlastnosti, datové vazby na vlastní typy, které implementují <xref:System.Reflection.ICustomTypeProvider> rozhraní a načítání informace o vazbě dat z výrazu vazby.

- Přemístění dat jako hodnoty změnit (shaping za provozu).

- Schopnost zkontrolujte, zda je odpojen kontextu dat pro kontejner položek.

- Umožňuje nastavit dobu, která má uplynout mezi vlastnost změny a aktualizace zdrojů dat došlo k chybě.

- Vylepšená podpora pro implementace vzorů slabé událostí. Události můžete navíc teď přijmout rozšíření značek.

<a name="windows_communication_foundation"></a> 
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], aby bylo jednodušší k zápisu a udržovat aplikace Windows Communication Foundation (WCF) byly přidány následující funkce:

- Zjednodušení generované konfigurační soubory.

- Podpora pro vývoj s včasným kontrakt.

- Umožňuje snadno konfigurovat režim kompatibility ASP.NET.

- Změny ve výchozích přenosu hodnoty vlastností pro snížit pravděpodobnost, že budete muset nastavit je.

- Aktualizace <xref:System.Xml.XmlDictionaryReaderQuotas> třídy snížit pravděpodobnost, že budete muset ručně konfigurovat kvóty pro slovník čtečky XML.

- Ověření konfiguračních souborů WCF Visual Studio jako součást procesu sestavení, tak můžete zjistit chyby konfigurace předtím, než spustíte aplikaci.

- Nový asynchronní podpora streamování.

- Nové mapování protokolu HTTPS aby bylo snazší vystavit koncový bod HTTPS pomocí Internetové informační služby (IIS).

- Umožňuje generovat metadata do jednoho dokumentu WSDL připojením `?singleWSDL` na adresu URL služby.

- Technologie Websockets podporu a povolit true obousměrnou komunikaci přes porty 80 a 443 s přenos TCP podobné charakteristiky.

- Podpora konfigurace služeb v kódu.

- Popisy tlačítek editoru XML.

- <xref:System.ServiceModel.ChannelFactory>ukládání do mezipaměti podpory.

- Podpora binární kodér komprese.

- Podpora pro přenosu UDP, která umožňuje vývojářům zápis služeb, které používají "fire a zapomněli" zasílání zpráv. Klient odešle zprávu do služby a očekává žádná odpověď ze služby.

- Schopnost podporovat více režimy ověřování na jeden koncový bod WCF při používání přenosového protokolu HTTP a zabezpečení přenosu.

- Podpora pro služby WCF, které používají mezinárodní názvy domén (IDN).

 Další informace najdete v tématu [co je nového ve Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=228173).

<a name="windows_workflow_foundation"></a> 
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], několik nových funkcí byly přidány do systému Windows Workflow Foundation (WF), včetně:

- Stav počítače pracovních postupů, které byly uvedeny jako součást rozhraní .NET Framework 4.0.1 ([rozhraní .NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092)). Tato aktualizace zahrnuta několik nové třídy a aktivity, které umožňuje vývojářům vytvářet pracovní postupy stav počítače. Tyto třídy a aktivity aktualizace [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zahrnout:

    - Možnost nastavit zarážky na stavy.

    - Možnost Kopírovat a vkládat přechody v Návrháři pracovních postupů.

    - Podpora návrháře pro vytvoření přechodu sdílené aktivační události.

    - Aktivity pro vytváření pracovních postupů stavu počítače, včetně: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, a <xref:System.Activities.Statements.Transition>.

- Rozšířené funkce návrháře pracovních postupů, jako je následující:

    - Rozšířené možnosti vyhledávání pracovního postupu v sadě Visual Studio, včetně **rychlého hledání** a **hledání v souborech**.

    - Umožňuje automaticky vytvořit pořadí aktivitu, když je druhá aktivita podřízené přidán do aktivity kontejneru a zahrnout i aktivit do aktivity pořadí.

    - Posouvání podpory, což umožňuje viditelnou část pracovní postup se musí změnit bez použití posuvníky.

    - Nový **Osnova dokumentu** zobrazení, které zobrazuje součásti pracovního postupu v stromové zobrazení osnovy a umožňuje vyberte komponentu ve **Osnova dokumentu** zobrazení.

    - Možnost přidání poznámky do aktivity.

    - Možnost definice a používání delegátů aktivity pomocí návrháře pracovních postupů.

    - Automaticky připojit a automatické vkládání pro aktivity a přechody v počítači a vývojový diagram stavu pracovních postupů.

- Úložiště zobrazení informací o stavu pro pracovní postup v jednom elementu v souboru XAML, takže můžete snadno vyhledat a upravit informace o stavu zobrazení.

- Aktivita kontejneru NoPersistScope zabránit uložením podřízené aktivity.

- Podpora pro výrazy jazyka C#:

    - Projekty workflow, které používají Visual Basic použije výrazy jazyka Visual Basic a C# projekty pracovního postupu bude používat výrazy jazyka C#.

    - C# projekty workflow, byly vytvořeny v sadě Visual Studio 2010 a které mají výrazy jazyka Visual Basic jsou kompatibilní s projekty C# pracovní postup používající výrazy jazyka C#.

- Vylepšení správy verzí:

    - Nové <xref:System.Activities.WorkflowIdentity> třídy, která zajišťuje mapování mezi instanci trvalou pracovního postupu a jeho definice pracovního postupu.

    - Souběžně sdílená spouštění více verzí pracovního postupu na stejném hostiteli, včetně <xref:System.ServiceModel.Activities.WorkflowServiceHost>.

    - V dynamické aktualizaci, možnost upravit definici instanci trvalou pracovního postupu.

- První kontrakt vývoj služby pracovního postupu, který poskytuje podporu pro automatické generování aktivity tak, aby odpovídala stávající smlouvy služby.

 Další informace najdete v tématu [co je nového ve Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=228176).

<a name="tailored"></a> 
### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace jsou navrženy pro konkrétní typy zařízení a využít síly operačního systému Windows. Podmnožinu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nebo 4.5.1 je k dispozici pro vytvoření [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací pro Windows s použitím jazyka C# nebo Visual Basic. Tato část se nazývá [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] který je popsán v [přehled](http://go.microsoft.com/fwlink/?LinkId=228491) ve službě Windows Dev Center.

<a name="portable"></a> 
### <a name="portable-class-libraries"></a>Knihovny přenosných tříd
 Přenosná knihovna tříd projektu v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] (a novějších verzí) umožňuje zapsat a sestavení spravovaná sestavení, které pracují ve více platformách rozhraní .NET Framework. Pomocí projektu knihovny přenosných tříd, vyberte platformy (například Windows Phone a [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]) k cíli. Dostupné typy a členy ve vašem projektu jsou automaticky omezen na běžné typy a členy mezi tyto platformy. Další informace najdete v tématu [Přenosná knihovna tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Viz také
 [Rozhraní .NET Framework a Out-of-Band verze](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)   
 [Co je nového v usnadnění v rozhraní .NET Framework](whats-new-in-accessibility.md)   
 [Co je nového ve Visual Studio 2017](/visualstudio/ide/whats-new-in-visual-studio)   
 [ASP.NET](/aspnet)   
 [Co je nového v jazyce Visual C++](/cpp/what-s-new-for-visual-cpp-in-visual-studio) 
