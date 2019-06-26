---
title: Nasazení služby WCF hostované Internetovou informační službou
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 4c46a7ac0482e0f9c969505b87558d240bb1391e
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402302"
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Nasazení služby WCF hostované Internetovou informační službou

Vývoj a nasazení služby Windows Communication Foundation (WCF), které je hostované v Internetové informační služby (IIS) se skládá z následujících úloh:

- Ujistěte se, že služby IIS, ASP.NET, WCF a součásti aktivace WCF jsou správně nainstalován a zaregistrován.

- Vytvoření nové aplikace služby IIS, nebo znovu použít stávající aplikaci ASP.NET.

- Vytvoření souboru .svc pro službu WCF.

- Nasazení implementace služby do aplikace služby IIS.

- Konfigurace služby WCF.

Podrobný návod k vytvoření služby WCF hostované v IIS, naleznete v tématu [jak: Hostování služby WCF v IIS](how-to-host-a-wcf-service-in-iis.md).

## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Zajistěte, aby služba IIS, ASP.NET a WCF byly správně nainstalován a registrován

WCF, IIS a ASP.NET musí nainstalovat služby WCF hostované v IIS správně fungovat. Postupy pro instalaci WCF (jako součást rozhraní .NET Framework), technologie ASP.NET a IIS se liší v závislosti na operačním systému. Další informace o instalaci WCF a .NET Framework najdete v tématu [nainstalovat rozhraní .NET Framework pro vývojáře](../../install/guide-for-developers.md). Chcete-li nainstalovat službu IIS na Windows 10, otevřete **programy a funkce** v **ovládací panely** a pak vyberte **Windows zapnout nebo vypnout funkce**. V **funkce Windows**vyberte **Internetová informační služba** a klikněte na tlačítko **OK**.

![Funkce Windows se zvýrazněnou službou IIS](media/windows-features-iis.png)

Pokyny k instalaci služby IIS na jiných operačních systémech najdete na [instalace služby IIS na systémech Windows Vista a Windows 7](/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7) a [nainstalujte IIS 8.5 v systému Windows Server 2012 R2](/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2).

Proces instalace rozhraní .NET Framework automaticky zaregistruje WCF se službou IIS, pokud služba IIS již existuje v počítači. Pokud po rozhraní .NET Framework je nainstalována služba IIS, další krok se vyžaduje k registraci ve službě IIS a ASP.NET WCF. Provedete to následujícím způsobem, v závislosti na váš operační systém:

- Windows 7 a Windows Server 2003: Použití [nástroj ServiceModel Registration (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) nástroj k registraci ve službě IIS WCF. Chcete-li tento nástroj použít, zadejte **ServiceModelReg.exe /i /x** v [Developer Command Prompt pro sadu Visual Studio](../../tools/developer-command-prompt-for-vs.md).

- Windows 7: Nakonec musíte ověřit, že technologie ASP.NET je nakonfigurován na použití rozhraní .NET Framework verze 4 nebo novější. To provedete spuštěním ASPNET_Regiis nástroje s `–i` možnost. Další informace najdete v tématu [ASP.NET IIS Registration Tool](https://go.microsoft.com/fwlink/?LinkId=201186).

## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Vytvoření nové aplikace služby IIS nebo znovu použít stávající aplikaci ASP.NET

Služby WCF hostované v IIS se musí nacházet v rámci aplikace služby IIS. Můžete vytvořit novou aplikaci služby IIS pro hostování služeb WCF výhradně. Alternativně můžete nasazení služby WCF do existující aplikace, která je již hostování technologie ASP.NET 2.0 obsahu (jako jsou stránky ASPX a webových služeb ASP.NET s [ASMX]). Další informace o těchto možnostech najdete v článku "hostování WCF – souběžně s rozhraním ASP.NET" a "Hostování služby WCF v režim kompatibility ASP.NET" oddíly v [služby WCF a ASP.NET](wcf-services-and-aspnet.md).

Všimněte si, že služba IIS 6.0 a pozdějších verzí pravidelně restartovat izolovaných objektově orientované programování aplikací. Výchozí hodnota je 1740 minut. Maximální podporovaná hodnota je 71,582 minut. Toto restartování je zakázat. Další informace o této vlastnosti naleznete v tématu [PeriodicRestartTime](https://go.microsoft.com/fwlink/?LinkId=109968).

## <a name="create-an-svc-file-for-the-wcf-service"></a>Vytvoření souboru .svc pro služby WCF

Služby WCF hostované v IIS jsou reprezentovány jako speciální soubory obsahu (hledání souborů .svc) uvnitř aplikace služby IIS. Tento model je podobný způsob, jakým ASMX stránky jsou reprezentovány v rámci aplikace služby IIS jako souborů .asmx. .Svc soubor obsahuje direktivy zpracování specifické pro WCF ([\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)), která umožňuje WCF hostování infrastrukturu k aktivaci hostované služby v reakci na příchozí zprávy. Nejběžnější syntaxí pro soubor SVC je v následujícím příkazu.

```
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>
```

Skládá se z [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice a jeden atribut, `Service`. Hodnota `Service` atribut je běžný název modulu runtime (CLR) typ jazyka implementaci služby. Pomocí této direktivy je v podstatě ekvivalentní k vytváření hostitele služby pomocí následujícího kódu.

```csharp
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );
```

Je možné provést další konfiguraci hostování, jako je například vytváření seznam bázové adresy pro službu. Můžete použít také vlastní <xref:System.ServiceModel.Activation.ServiceHostFactory> rozšířit směrnice pro použití s vlastní řešení hostování. Aplikace služby IIS, které hostují služby WCF nejsou zodpovědného za správu vytváření a dobu života <xref:System.ServiceModel.ServiceHost> instancí. Spravovaná infrastruktura WCF hostování vytvoří nezbytné <xref:System.ServiceModel.ServiceHost> instance dynamicky při první žádosti o přijetí souboru .svc. Instance není všeobecně dostupné, dokud buď je uzavřený explicitně pomocí kódu nebo pokud aplikace recykluje.

Další informace o syntaxi hledání souborů .svc najdete v tématu [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).

## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Nasazení implementace služby do aplikace služby IIS

Služby WCF hostované ve službě IIS pomocí stejného modelu dynamická kompilace jako technologii ASP.NET 2.0. Stejně jako u technologie ASP.NET, můžete nasadit implementační kód služby WCF hostované v IIS několika způsoby na různých místech, následujícím způsobem:

- Jak předkompilované dll soubor umístěn v globální mezipaměti sestavení (GAC) nebo v adresáři \bin aplikace. Předkompilovaný binární soubory nejsou aktualizovány, dokud je nasadit novou verzi knihovny tříd.

- Jak nezkompilované zdrojové soubory umístěny v adresáři \App_Code aplikace. Při zpracování první žádosti jsou dynamicky vyžaduje zdrojové soubory v tomto adresáři. Všechny změny souborů v adresáři \App_Code způsobit celé aplikace recyklaci a znovu zkompilovat při příští žádosti o přijetí.

- Jak je umístěn nezkompilované kód přímo v souboru SVC. Implementace kódu může být také umístěny vložený v souboru SVC služby, po \@direktivě ServiceHost. Všechny změny vloženého kódu způsobit recyklaci a znovu zkompilovat při příští žádosti o přijetí.

Další informace o modelu kompilace ASP.NET 2.0 najdete v tématu [kompilace ASP.NET: Přehled](https://go.microsoft.com/fwlink/?LinkId=94773).

## <a name="configure-the-wcf-service"></a>Konfigurace služby WCF

Služby WCF hostované IIS uložení jejich konfigurace v souboru Web.config aplikace. Služby hostované v IIS použít stejný konfigurační prvky a syntaxe jako služby WCF hostované mimo službu IIS. Ale tato omezení jsou jedinečné pro hostitelské prostředí služby IIS:

- Bázové adresy pro služby hostované v IIS.

- Aplikacemi hostování služby WCF mimo službu IIS můžete řídit základní adresa služby hostují předáním sadu základní adresa URI pro <xref:System.ServiceModel.ServiceHost> konstruktor nebo tím, že poskytuje [ \<hostitele >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) prvek Konfigurace služby. Služby hostované ve službě IIS nemají možnost řídit jejich základní adresa; Základní adresa služby hostované v IIS je adresa jeho souboru SVC.

### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresy koncových bodů služby hostované v IIS

Když jsou hostované v IIS, adresy koncových bodů jsou vždy považovány za relativní vzhledem k adresu .svc souboru, který reprezentuje službu. Například, pokud je základní adresa služby WCF `http://localhost/Application1/MyService.svc` s následující konfigurací koncového bodu:

```xml
<endpoint address="anotherEndpoint" .../>
```

To poskytuje koncový bod, který může být dostupný na adrese `http://localhost/Application1/MyService.svc/anotherEndpoint`.

Podobně, konfigurace element koncového bodu, který používá prázdný řetězec jako relativní adresu poskytuje koncový bod dostupný v `http://localhost/Application1/MyService.svc`, což je základní adresa.

```xml
<endpoint address="" ... />
```

Musíte vždycky použít relativní koncového bodu adresy koncových bodů služby hostované v IIS. Poskytuje adresu plně kvalifikovaný koncového bodu (například `http://localhost/MyService.svc`) může vést k chybám v nasazení služby, pokud se adresa koncového bodu neukazuje na aplikace služby IIS, který je hostitelem služby vystavení koncového bodu. Pomocí adresy relativní koncových bodů pro hostované služby se vyhnete tyto možným konfliktům.

### <a name="available-transports"></a>K dispozici přenosy

Služby WCF hostované v IIS 5.1 a IIS 6.0 jsou omezeny na používání komunikace na základě protokolu HTTP. Na těchto platformách IIS konfigurace hostovanou službu, která používá vazbu jiným protokolem než HTTP způsobí chybu při aktivaci služby. Pro [!INCLUDE[iisver](../../../../includes/iisver-md.md)], podporovaných přenosů zahrnují HTTP, Net.TCP, Net.Pipe, Net.MSMQ a msmq.formatname pro zpětné kompatibilitě se stávajícími aplikacemi služby MSMQ.

### <a name="http-transport-security"></a>Zabezpečení přenosu HTTP

Služby WCF hostované IIS můžete využít službu HTTP tak dlouho, dokud virtuální adresář IIS, která obsahuje službu podporuje ty přenosu zabezpečení (například HTTPS a HTTP schémat ověřování např. Basic, Digest a integrované ověřování Windows) nastavení. Nastavení zabezpečení přenosu HTTP na hostovaný koncový bod vazby musí odpovídat nastavení zabezpečení přenosu na virtuální adresář IIS, který jej obsahuje.

Například koncový bod WCF, který je nakonfigurován pro použití ověřování algoritmem digest HTTP musí nacházet ve virtuální adresář IIS také nakonfigurována, aby umožňovala ověřování hodnotou hash protokolu HTTP. Bezkonkurenční kombinace nastavení služby IIS a nastavení koncových bodů WCF dojít k chybě při aktivaci služby.

## <a name="see-also"></a>Viz také:

- [Hostování v Internetové informační službě](hosting-in-internet-information-services.md)
- [Osvědčené postupy hostování Internetové informační služby](internet-information-services-hosting-best-practices.md)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
