---
title: Nasazení služby WCF hostované Internetovou informační službou
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: b02c69e00aacafd928c59f06e0e7c050a2ca6509
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856119"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Nasazení služby WCF hostované Internetovou informační službou

Vývoj a nasazení služby Windows Communication Foundation (WCF), která je hostovaná v Internetová informační služba (IIS), se skládá z následujících úloh:

- Ujistěte se, že služba IIS, ASP.NET, WCF a aktivační komponenta WCF jsou správně nainstalované a registrované.

- Vytvořte novou aplikaci služby IIS nebo znovu použijte existující aplikaci ASP.NET.

- Vytvořte soubor. svc pro službu WCF.

- Nasaďte implementaci služby do aplikace IIS.

- Nakonfigurujte službu WCF.

Podrobný návod k vytváření služby WCF hostované službou IIS najdete v tématu [How to: Hostování služby WCF ve službě IIS](how-to-host-a-wcf-service-in-iis.md).

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Zkontrolujte, jestli jsou správně nainstalovaná a registrovaná služba IIS, ASP.NET a WCF.

Aby služby WCF hostované službou IIS fungovaly správně, musí být nainstalované WCF, IIS a ASP.NET. Postupy pro instalaci WCF (jako součást .NET Framework), ASP.NET a IIS se liší v závislosti na vašem operačním systému. Další informace o instalaci WCF a .NET Framework najdete v tématu [instalace .NET Framework pro vývojáře](../../install/guide-for-developers.md). Chcete-li nainstalovat službu IIS v systému Windows 10, otevřete **Ovládací panely** **programy a funkce** a potom vyberte možnost **zapnout nebo vypnout funkce systému Windows**. V **funkcích Windows**vyberte **Internetová informační služba** a pak zvolte **OK**.

![Funkce Windows se zvýrazněnou službou IIS](media/windows-features-iis.png)

Pokyny k instalaci služby IIS do jiných operačních systémů najdete v tématu [instalace služby IIS v systému Windows Vista a Windows 7](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) a [Instalace IIS 8,5 na Windows Server 2012 R2](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2).

Proces instalace pro .NET Framework automaticky registruje WCF ve službě IIS, pokud je služba IIS na tomto počítači již nainstalována. Pokud je služba IIS nainstalovaná po .NET Framework, vyžaduje se k registraci WCF se službou IIS a ASP.NET další krok. To můžete provést následujícím způsobem v závislosti na vašem operačním systému:

- Windows 7 a Windows Server 2003: Pomocí nástroje pro [registraci ServiceModel (ServiceModelReg. exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) zaregistrujete WCF se službou IIS. Chcete-li použít tento nástroj, zadejte **ServiceModelReg. exe/i/x** v [Developer Command Prompt pro Visual Studio](../../tools/developer-command-prompt-for-vs.md).

- Windows 7: Nakonec musíte ověřit, že je ASP.NET nakonfigurovaný tak, aby používal .NET Framework verzi 4 nebo novější. Provedete to tak, že spustíte nástroj Aspnet_regiis `–i` s možností. Další informace najdete v tématu [Nástroj pro registraci služby IIS ASP.NET](https://go.microsoft.com/fwlink/?LinkId=201186).

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Vytvoření nové aplikace služby IIS nebo opětovného použití existující aplikace ASP.NET

Služby WCF hostované službou IIS se musí nacházet v rámci aplikace IIS. Můžete vytvořit novou aplikaci služby IIS, která bude hostovat služby WCF výhradně. Případně můžete nasadit službu WCF do existující aplikace, která je již hostitelem obsahu ASP.NET 2,0 (například stránky ASPX a ASP.NET webové služby [ASMX]). Další informace o těchto možnostech najdete v částech "hostování WCF s ASP.NET" a "hostování služeb WCF v režimu kompatibility ASP.NET" v oddílech [WCF Services a ASP.NET](wcf-services-and-aspnet.md).

Upozorňujeme, že služba IIS 6,0 a novější verze pravidelně restartuje izolované objektově orientované programovací aplikace. Výchozí hodnota je 1740 minut. Maximální podporovaná hodnota je 71 582 minut. Tento restart je možné zakázat. Další informace o této vlastnosti naleznete v tématu [PeriodicRestartTime](https://go.microsoft.com/fwlink/?LinkId=109968).

## <a name="create-an-svc-file-for-the-wcf-service"></a>Vytvoření souboru. svc pro službu WCF

Služby WCF hostované ve službě IIS jsou v rámci aplikace IIS reprezentovány jako speciální soubory obsahu (soubory. svc). Tento model je podobný způsobu, jakým jsou stránky ASMX zastoupeny v aplikaci služby IIS jako soubory. asmx. Soubor. svc obsahuje direktivu zpracování specifickou pro WCF ([\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)), která umožňuje hostující infrastruktuře WCF aktivovat hostované služby v reakci na příchozí zprávy. Nejběžnější syntaxí souboru. svc je následující příkaz.

```svc
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>
```

Skládá se z [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy ServiceHost a jediného atributu `Service`. Hodnota `Service` atributu je název typu modulu CLR (Common Language Runtime) pro implementaci služby. Použití této směrnice je v podstatě ekvivalentem vytvoření hostitele služby pomocí následujícího kódu.

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

Je možné provést i další konfiguraci hostování, například vytvoření seznamu základních adres pro službu. Můžete také použít vlastní <xref:System.ServiceModel.Activation.ServiceHostFactory> pro rozšiřování direktivy pro použití s vlastními řešeními hostování. Aplikace služby IIS, které hostují služby WCF, nejsou zodpovědné za správu vytváření a životnosti <xref:System.ServiceModel.ServiceHost> instancí. Spravovaná infrastruktura hostingu WCF vytváří instanci potřebnou <xref:System.ServiceModel.ServiceHost> dynamicky při přijetí prvního požadavku pro soubor. svc. Instance není uvolněna, dokud není explicitně zavřena kódem nebo při recyklování aplikace.

Další informace o syntaxi souborů. svc naleznete v tématu [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Nasazení implementace služby do aplikace služby IIS

Služby WCF hostované v IIS používají stejný model dynamické kompilace jako ASP.NET 2,0. Stejně jako u ASP.NET můžete nasadit implementační kód pro služby WCF hostované službou IIS několika způsoby v různých umístěních, a to následujícím způsobem:

- Jako předkompilovaný soubor dll umístěný v globální mezipaměti sestavení (GAC) nebo v adresáři \Bin aplikace. Předkompilované binární soubory nejsou aktualizovány, dokud není nasazena nová verze knihovny tříd.

- Jako nezkompilované zdrojové soubory nacházející se v adresáři \App_Code aplikace. Zdrojové soubory, které se nacházejí v tomto adresáři, se dynamicky vyžadují při zpracování prvního požadavku aplikace. Jakékoli změny souborů v adresáři \App_Code způsobí, že celá aplikace bude recyklována a znovu zkompilována po přijetí další žádosti.

- Jako nekompilovaný kód umístěný přímo v souboru. svc. Implementační kód může být také umístěn v souboru. svc služby po \@direktivě ServiceHost. Jakékoli změny vloženého kódu způsobí, že se aplikace recykluje a znovu zkompiluje při přijetí další žádosti.

Další informace o modelu kompilace ASP.NET 2,0 naleznete v tématu [Přehled kompilace ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94773).

## <a name="configure-the-wcf-service"></a>Konfigurace služby WCF

Služby WCF hostované službou IIS ukládají svou konfiguraci do souboru Web. config aplikace. Služby hostované službou IIS používají stejné konfigurační prvky a syntaxi jako služby WCF hostované mimo službu IIS. Následující omezení jsou však pro hostování prostředí IIS jedinečná:

- Základní adresy pro služby hostované službou IIS.

- Aplikace hostující služby WCF mimo službu IIS mohou řídit základní adresu služeb, které hostují, předáním sady identifikátorů URI základních adres do <xref:System.ServiceModel.ServiceHost> konstruktoru nebo [ \<poskytnutím > elementu hosta](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) v této službě. rozšířeného. Služby hostované ve službě IIS nemají možnost řídit svou základní adresu. základní adresa služby hostované službou IIS je adresa svého souboru. svc.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresy koncových bodů pro služby hostované službou IIS

Pokud je služba IIS hostovaná ve službě IIS, adresy koncových bodů se vždycky považují za relativní k adrese souboru. svc, který představuje službu. Například pokud základní adresa služby WCF je `http://localhost/Application1/MyService.svc` s následující konfigurací koncového bodu:

```xml
<endpoint address="anotherEndpoint" .../>
```

To poskytuje koncový bod, na `http://localhost/Application1/MyService.svc/anotherEndpoint`který lze získat přístup.

Podobně, element konfigurace koncového bodu, který používá prázdný řetězec jako relativní adresa, poskytuje koncový bod dostupný v `http://localhost/Application1/MyService.svc`, což je základní adresa.

```xml
<endpoint address="" ... />
```

Pro koncové body služby hostované službou IIS musíte vždy použít relativní adresy koncových bodů. Poskytnutí plně kvalifikované adresy koncového bodu (například `http://localhost/MyService.svc`) může vést k chybám v nasazení služby, pokud adresa koncového bodu neodkazuje na aplikaci služby IIS, která hostuje službu, která tento koncový bod vystavuje. Používání relativních koncových bodů pro hostované služby zabraňuje těmto potenciálním konfliktům.

### <a name="available-transports"></a>Dostupné přenosy

Služby WCF hostované ve službě IIS 5,1 a IIS 6,0 jsou omezené na použití komunikace založené na protokolu HTTP. V těchto platformách IIS konfigurace hostované služby na použití vazby jiného typu než HTTP způsobí při aktivaci služby chybu. V případě služby IIS 7,0 podporuje přenos podporovaný protokolem HTTP, NET. TCP, NET. pipe, NET. MSMQ a MSMQ. FormatName pro zpětnou kompatibilitu se stávajícími aplikacemi služby MSMQ.

### <a name="http-transport-security"></a>Zabezpečení přenosu HTTP

Služby WCF hostované službou IIS mohou využívat zabezpečení přenosu HTTP (například schémata ověřování pomocí protokolu HTTPS a protokolu HTTP, jako je například Basic, Digest a integrované ověřování systému Windows), pokud virtuální adresář služby IIS, který obsahuje službu, podporuje tyto možnost. Nastavení zabezpečení přenosu HTTP u vazby hostovaného koncového bodu se musí shodovat s nastavením zabezpečení přenosu ve virtuálním adresáři služby IIS, který ho obsahuje.

Například koncový bod WCF nakonfigurovaný k použití ověřování pomocí protokolu HTTP Digest se musí nacházet ve virtuálním adresáři IIS, který je taky nakonfigurovaný tak, aby povoloval ověřování HTTP Digest. Nespárované kombinace nastavení služby IIS a nastavení koncového bodu WCF mají za následek chybu během aktivace služby.

## <a name="see-also"></a>Viz také:

- [Hostování v Internetové informační službě](hosting-in-internet-information-services.md)
- [Osvědčené postupy hostování Internetové informační služby](internet-information-services-hosting-best-practices.md)
- [Funkce hostování technologie Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
