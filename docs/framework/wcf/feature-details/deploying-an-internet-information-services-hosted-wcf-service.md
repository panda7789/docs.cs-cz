---
title: Nasazení služby WCF hostované Internetovou informační službou
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 67f6877546951bd92b235218f10f6ccc7011ef5c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463858"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Nasazení služby WCF hostované Internetovou informační službou

Vývoj a nasazení služby WCF (Windows Communication Foundation), která je hostována v Internetové informační službě (IIS), se skládá z následujících úkolů:

- Ujistěte se, že iis, ASP.NET, WCF a wcf aktivační součást jsou správně nainstalovány a registrovány.

- Vytvořte novou aplikaci služby IIS nebo znovu použijte existující ASP.NET aplikaci.

- Vytvořte soubor SVC pro službu WCF.

- Nasaďte implementaci služby do aplikace služby IIS.

- Nakonfigurujte službu WCF.

Podrobný návod k vytvoření služby WCF hostované službou IIS naleznete v tématu [How to: Host a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Ujistěte se, že iis, ASP.NET a WCF jsou správně nainstalovány a registrovány

WCF, IIS a ASP.NET musí být nainstalovány pro služby WCF hostované službou IIS, aby fungovaly správně. Postupy pro instalaci WCF (jako součást rozhraní .NET Framework), ASP.NET a Služby IIS se liší v závislosti na operačním systému. Další informace o instalaci wcf a rozhraní .NET Framework naleznete [v tématu Instalace rozhraní .NET Framework pro vývojáře](../../install/guide-for-developers.md). Chcete-li službu IIS nainstalovat do systému Windows 10, otevřete ovládací **panel** **Programy a funkce** a vyberte možnost **Zapnout nebo vypnout funkce systému Windows**. V **programu Funkce systému Windows**vyberte Možnost **Internetová informační služba** a pak zvolte **OK**.

![Funkce systému Windows se zvýrazněnou službou IIS](./media/windows-features-iis.png)

Pokyny pro instalaci služby IIS do jiných operačních systémů naleznete na [webu Instalace služby IIS v systémech Windows Vista a Windows 7](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) a Instalace [služby IIS 8.5 v systému Windows Server 2012 R2](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2).

Proces instalace rozhraní .NET Framework automaticky zaregistruje wcf se službou IIS, pokud je služby IIS již v počítači k dispozici. Pokud je iis nainstalována po rozhraní .NET Framework, je nutný další krok k registraci wcf s iis a ASP.NET. V závislosti na operačním systému to lze provést následujícím způsobem:

- Windows 7 a Windows Server 2003: Pomocí nástroje [ServiceModel Registration Tool (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) zaregistrujte wcf se službou IIS. Chcete-li použít tento nástroj, zadejte do [příkazového řádku pro vývojáře pro sadu Visual Studio](../../tools/developer-command-prompt-for-vs.md)zadejte příkaz **ServiceModelReg.exe /i /x** .

- Windows 7: Nakonec je nutné ověřit, že ASP.NET je nakonfigurován pro použití rozhraní .NET Framework verze 4 nebo novější. To provést spuštěním nástroje ASPNET_Regiis `–i` s možností. Další informace naleznete [v tématu ASP.NET Nástroj pro registraci iis](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)).

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Vytvoření nové aplikace služby IIS nebo opětovné použití existující ASP.NET aplikace

Služby WCF hostované službou IIS musí být umístěny uvnitř aplikace služby IIS. Můžete vytvořit novou aplikaci služby IIS pro výhradní hostování služeb WCF. Případně můžete nasadit službu WCF do existující aplikace, která je již hostitelem obsahu ASP.NET 2.0 (například stránky ASPX a ASP.NET webových služeb [ASMX]). Další informace o těchto možnostech naleznete v části "Hostování WCF side-by-Side with ASP.NET" a "Hosting WCF Services in ASP.NET Compatibility Mode" v [wcf služby a ASP.NET](wcf-services-and-aspnet.md).

Všimněte si, že iIS 6.0 a novější verze pravidelně restartují izolované objektově orientované programovací aplikace. Výchozí hodnota je 1740 minut. Maximální podporovaná hodnota je 71 582 minut. Toto restartování lze zakázat. Další informace o této vlastnosti naleznete v tématu [PeriodARestartTime](https://docs.microsoft.com/previous-versions/iis/6.0-sdk/ms525914(v=vs.90)).

## <a name="create-an-svc-file-for-the-wcf-service"></a>Vytvoření souboru SVC pro službu WCF

Služby WCF hostované ve službě IIS jsou v aplikaci služby IIS reprezentovány jako speciální soubory obsahu (soubory svc). Tento model je podobný způsobu, jakým jsou stránky ASMX reprezentovány uvnitř aplikace služby IIS jako soubory ASMX. Soubor .svc obsahuje direktivu zpracování specifické pro WCF[\@(ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)), která umožňuje hostitelské infrastruktuře WCF aktivovat hostované služby v reakci na příchozí zprávy. Nejběžnější syntaxe souboru .svc je v následujícím příkazu.

`<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>`

Skládá se ze směrnice [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) a `Service`jednoho atributu . Hodnota atributu `Service` je název typu clr (CLR) společného jazyka (CLR). Použití této směrnice je v podstatě ekvivalentní k vytvoření hostitele služby pomocí následujícího kódu.

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

Další hostování konfigurace, jako je například vytvoření seznamu základních adres pro službu lze také provést. Můžete také použít <xref:System.ServiceModel.Activation.ServiceHostFactory> vlastní rozšířit směrnice pro použití s vlastní hosting řešení. Aplikace služby IIS, které jsou hostiteli služeb WCF, nejsou odpovědné za správu vytváření a životnosti <xref:System.ServiceModel.ServiceHost> instancí. Spravovaná hostitelská infrastruktura WCF vytvoří potřebnou <xref:System.ServiceModel.ServiceHost> instanci dynamicky při přijetí prvního požadavku pro soubor .svc. Instance není uvolněna, dokud není explicitně uzavřena kódem nebo když je aplikace recyklována.

Další informace o syntaxi souborů .svc naleznete v tématu [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Nasazení implementace služby do aplikace služby IIS

Služby WCF hostované ve službě IIS používají stejný model dynamické kompilace jako ASP.NET 2.0. Stejně jako u ASP.NET můžete nasadit kód implementace pro služby WCF hostované službou IIS několika způsoby na různých místech, a to následujícím způsobem:

- Jako předkompilovaný soubor DLL umístěný v globální mezipaměti sestavení (GAC) nebo v adresáři \bin aplikace. Předkompilované binární soubory nejsou aktualizovány, dokud není nasazena nová verze knihovny tříd.

- Jako nezkompilované zdrojové soubory umístěné v adresáři \App_Code aplikace. Zdrojové soubory umístěné v tomto adresáři jsou dynamicky vyžadovány při zpracování prvního požadavku aplikace. Jakékoli změny souborů v adresáři \App_Code způsobí, že celá aplikace bude recyklována a znovu zkompilován při přijetí dalšího požadavku.

- Jako nezkompilovaný kód umístěný přímo do souboru .svc. Kód implementace může být také umístěn v řádku v souboru \@.svc služby po servicehost směrnice. Všechny změny vsazeného kódu způsobí, že aplikace bude recyklována a znovu zkompilována při přijetí dalšího požadavku.

Další informace o modelu kompilace ASP.NET 2.0 naleznete [v tématu ASP.NET Přehled kompilace](https://docs.microsoft.com/previous-versions/aspnet/ms178466(v=vs.100)).

## <a name="configure-the-wcf-service"></a>Konfigurace služby WCF

Služby WCF hostované službou IIS ukládají svou konfiguraci do souboru Web.config aplikací. Služby hostované službou IIS používají stejné konfigurační prvky a syntaxi jako služby WCF hostované mimo službu IIS. Následující omezení jsou však jedinečná pro hostitelské prostředí služby IIS:

- Základní adresy pro služby hostované službou IIS.

- Aplikace hostující služby WCF mimo službu IIS mohou řídit základní adresu služeb, které <xref:System.ServiceModel.ServiceHost> hostují, předáním sady identifikátorů URI základní adresy konstruktoru nebo poskytnutím [ \<prvku hostitelského>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) v konfiguraci služby. Služby hostované ve službě IIS nemají možnost kontrolovat svou základní adresu. základní adresa služby hostované službou IIS je adresa souboru SVC.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresy koncových bodů pro služby Hosted iIS

Při hostování ve službě IIS jsou adresy koncového bodu vždy považovány za relativní vzhledem k adrese souboru SVC, který představuje službu. Například pokud je základní adresa služby `http://localhost/Application1/MyService.svc` WCF s následující konfigurací koncového bodu:

```xml
<endpoint address="anotherEndpoint" />
```

To poskytuje koncový bod, který `http://localhost/Application1/MyService.svc/anotherEndpoint`lze dosáhnout na adrese .

Podobně prvek konfigurace koncového bodu, který používá prázdný řetězec jako relativní `http://localhost/Application1/MyService.svc`adresu poskytuje koncový bod dosažitelný na , což je základní adresa.

```xml
<endpoint address="" />
```

Pro koncové body služby Hostované službou IIS je vždy nutné používat relativní adresy koncových bodů. Zadání plně kvalifikované adresy koncového bodu `http://localhost/MyService.svc`(například) může vést k chybám v nasazení služby, pokud adresa koncového bodu neukazuje na aplikaci služby IIS, která je hostitelem služby, která vystavuje koncový bod. Použití relativní adresy koncového bodu pro hostované služby se těmto potenciálním konfliktům vyhne.

### <a name="available-transports"></a>Dostupné přenosy

Služby WCF hostované ve službě IIS 5.1 a IIS 6.0 jsou omezeny na použití komunikace založené na protokolu HTTP. Na těchto platformách služby IIS má konfigurace hostované služby pro použití vazby bez protokolu HTTP za následek chybu během aktivace služby. Pro iis 7.0 podporované přenosy zahrnují HTTP, Net.TCP, Net.Pipe, Net.MSMQ a msmq.formatname pro zpětnou kompatibilitu s existujícími aplikacemi msmq.

### <a name="http-transport-security"></a>Zabezpečení přenosu HTTP

Služby WCF hostované službou IIS mohou využívat zabezpečení přenosu protokolu HTTP (například schémata ověřování protokolu HTTPS a HTTP, například Základní, Digest a Integrované ověřování systému Windows), pokud virtuální adresář služby IIS, který tuto službu obsahuje, tato nastavení podporuje. Nastavení zabezpečení přenosu PROTOKOLU HTTP na vazbě hostovaného koncového bodu se musí shodovat s nastavením zabezpečení přenosu ve virtuálním adresáři služby IIS, který jej obsahuje.

Koncový bod WCF nakonfigurovaný pro použití ověřování algoritmem HTTP digest se například musí nasytit ve virtuálním adresáři služby IIS, který je také nakonfigurován tak, aby umožňoval ověřování algoritmem HTTP digest. Neodpovídající kombinace nastavení služby IIS a nastavení koncového bodu WCF mají za následek chybu během aktivace služby.

## <a name="see-also"></a>Viz také

- [Hostování v Internetové informační službě](hosting-in-internet-information-services.md)
- [Doporučené postupy hostování Internetové informační služby](internet-information-services-hosting-best-practices.md)
- [Funkce hostování prostředků pro aplikace systému Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
