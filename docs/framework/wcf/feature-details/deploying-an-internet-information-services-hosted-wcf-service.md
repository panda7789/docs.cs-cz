---
title: Nasazení služby WCF hostované Internetovou informační službou
ms.date: 03/30/2017
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
ms.openlocfilehash: 59f18d8487deb52f5ecb5b5c814ec9bdbc74e2cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Nasazení služby WCF hostované Internetovou informační službou
Vývoj a nasazení služby Windows Communication Foundation (WCF), který je hostován v Internetové informační služby (IIS) se skládá z následujících úloh:  
  
-   Zajistěte, aby služby IIS, ASP.NET, WCF a aktivace součásti WCF jsou správně nainstalovaný a zaregistrovaný.  
  
-   Vytvoření nové aplikace služby IIS, nebo znovu použijte existující [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.  
  
-   Vytvořte soubor .svc pro službu WCF.  
  
-   Implementace služby nasaďte do aplikace služby IIS.  
  
-   Konfigurace služby WCF.  
  
 Podrobný návod k vytvoření služby WCF hostované IIS, naleznete v části [postupy: hostování služby WCF ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Zajistěte, aby služba IIS, ASP.NET a WCF správně nainstalovaný a registrovaný  
 Pro správné fungování služby WCF hostované IIS musí být nainstalováno WCF, IIS a ASP.NET. Postupy pro instalaci WCF (jako součást [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]), ASP.NET a IIS lišit v závislosti na verzi operačního systému používá. Další informace o instalaci WCF a [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], najdete v části [instalačního programu webové rozhraní Microsoft .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=201185). Pokyny k instalaci služby IIS najdete na [instalace služby IIS](http://go.microsoft.com/fwlink/?LinkId=201188).  
  
 Proces instalace [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] automaticky zaregistruje WCF pomocí služby IIS, pokud služba IIS již na tomto počítači. Pokud po instalaci služby IIS [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], další krok je potřeba zaregistrovat WCF pomocí služby IIS a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Můžete to udělat takto, v závislosti na operačním systému:  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], Windows 7, a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]: použijte [nástroj ServiceModel Registration (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) nástroj pro službu IIS zaregistrovat WCF: Chcete-li tento nástroj používat, zadejte **ServiceModelReg.exe /i /x** v sadě Visual Studio příkazový řádek. Můžete otevřít tento příkaz řádku pomocí kliknutím na tlačítko start, výběr **všechny programy**, **sadu Microsoft Visual Studio 2012**, **nástroje sady Visual Studio**, a  **Visual Studio – příkazový řádek**  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]: Nainstalujte součásti systému Windows Communication Foundation aktivace podsoučásti z [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]. Chcete-li to provést, v Ovládacích panelech, klikněte na tlačítko **přidat nebo odebrat programy** a potom **přidat\/odebrat součásti systému Windows**. Tím dojde k aktivaci **Průvodce součástmi systému Windows**.  
  
-   Windows 7:  
  
 Nakonec je třeba ověřit, že technologie ASP.NET je nakonfigurovaný na použití rozhraní .NET Framework verze 4. To uděláte tak, že spustíte nástroj ASPNET_Regiis s – i možnost. Další informace najdete v tématu [ASP.NET IIS Registration Tool](http://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Vytvoření nové aplikace služby IIS nebo znovu použijte stávající aplikaci ASP.NET  
 Služby WCF hostované IIS se musí nacházet v rámci aplikace služby IIS. Můžete vytvořit novou aplikaci služby IIS pro hostování služeb WCF výhradně. Alternativně můžete nasazení služby WCF do existující aplikace, která již hostuje [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] obsahu (například stránky .aspx a webových služeb ASP.NET [ASMX]). Další informace o těchto možnostech najdete v článku "hostitelský WCF-souběžného s technologií ASP.NET" a "Hostitelských služeb WCF v režimu kompatibility ASP.NET" v částech [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
 Všimněte si, že [!INCLUDE[iis601](../../../../includes/iis601-md.md)] a novějších verzích pravidelně restartovala izolované objektově orientované programování aplikace. Výchozí hodnota je 1740 minut. Maximální podporovaná hodnota je 71,582 minut. Tento restart můžete zakázat. Další informace o této vlastnosti najdete v tématu [PeriodicRestartTime](http://go.microsoft.com/fwlink/?LinkId=109968).  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>Vytvořte soubor .svc služby WCF  
 Služby WCF hostované ve službě IIS, jsou reprezentovány jako speciální soubory obsahu (souborů .svc) uvnitř aplikace služby IIS. Tento model je podobná způsob, jakým jsou v rámci aplikace IIS jako souborů .asmx reprezentované ASMX stránky. Soubor .svc obsahuje direktivu zpracování specifické WCF ([@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)), který umožňuje WCF hostování infrastruktury aktivovat hostované služby v reakci na příchozí zprávy. Nejběžnější syntaxe pro soubor .svc je v následujícím příkazu.  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 Skládá se z [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice a jeden atribut, `Service`. Hodnota `Service` atribut je běžný název typu language runtime (CLR) implementace služby. Pomocí tato direktiva je v podstatě ekvivalentní vytvoření hostitele služby pomocí následujícího kódu.  
  
```  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 Můžete také provést další konfiguraci hostování, jako je například vytváření seznam základní adresy pro službu. Můžete také použít vlastní <xref:System.ServiceModel.Activation.ServiceHostFactory> rozšířit směrnice pro použití s vlastní řešení hostování. Aplikace služby IIS, které jsou hostiteli služby WCF nejsou zodpovědní za správu vytváření a dobu života <xref:System.ServiceModel.ServiceHost> instance. Spravované WCF hostování infrastruktury vytvoří nezbytné <xref:System.ServiceModel.ServiceHost> instance dynamicky při prvním požadavku je pro soubor .svc. Instance není vydala, dokud buď je uzavřený explicitně pomocí kódu nebo pokud je aplikace recykluje.  
  
 Další informace o syntaxi souborů .svc najdete v tématu [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Nasazení implementace služby do aplikace služby IIS  
 Služby WCF hostované ve službě IIS použít stejný model dynamická kompilace jako [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]. Jenom jako s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], kód implementace pro služby WCF hostované IIS několika způsoby v různých umístěních, můžete nasadit takto:  
  
-   Jako soubor s příponou DLL předkompilovaných nachází v globální mezipaměti sestavení (GAC) nebo v adresáři \bin aplikace. Předkompilované binární soubory nejsou aktualizovány, dokud je nasadit novou verzi knihovny tříd.  
  
-   Jako zrušení kompilované zdrojové soubory umístěné v adresáři \App_Code aplikace. Zdrojové soubory, které jsou umístěné v tomto adresáři se dynamicky vyžadují při zpracování aplikace první žádosti. Všechny změny souborů v adresáři \App_Code způsobit celá aplikace recyklované a překompilovat, při příští žádosti o přijetí.  
  
-   Jak přímo v souboru .svc umístit zrušení zkompilovaný kód. Implementace kód může být také součástí textu v souboru .svc služby po @ServiceHost – direktiva. Všechny změny vloženého kódu způsobit, že aplikace recyklované a překompilovat, při příští žádosti o přijetí.  
  
 Další informace o [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] kompilace modelu, najdete v části [kompilace ASP.NET: Přehled](http://go.microsoft.com/fwlink/?LinkId=94773).  
  
## <a name="configure-the-wcf-service"></a>Konfigurace služby WCF  
 Služby WCF hostované IIS ukládat své konfigurace v souboru Web.config aplikace. Služba IIS hostované služby pomocí stejné konfigurace – elementy a syntaxe jako služby WCF hostované mimo služby IIS. Nicméně jsou jedinečné pro hostitelské prostředí služby IIS následující omezení:  
  
-   Základní adresy pro služby hostované službou IIS.  
  
-   Aplikace hostování služby WCF mimo službu IIS můžete řídit základní adresa služby hostují předáním sadu základní adresa identifikátory URI k <xref:System.ServiceModel.ServiceHost> konstruktor nebo tím, že poskytuje [ \<hostitele >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) element v Konfigurace služby. Služby hostované ve službě IIS nemají možnost řídit jejich základní adresa; Základní adresa služby hostované službou IIS je adresa jeho .svc souboru.  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresy koncových bodů pro služby hostované službou IIS  
 Když jsou hostované v IIS, adresy koncových bodů se vždy považují za relativní k adrese .svc soubor, který představuje službu. Například, pokud je základní adresa služby WCF http://localhost/Application1/MyService.svc s následující konfigurací koncového bodu.  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 To poskytuje koncový bod, který lze dosáhnout za "http://localhost/Application1/MyService.svc/anotherEndpoint".  
  
 Podobně konfigurace elementu koncový bod, který používá prázdný řetězec jako relativní adresu poskytuje koncový bod dostupný v http://localhost/Application1/MyService.svc, což je základní adresa.  
  
```xml  
<endpoint address="" ... />  
```  
  
 Musíte vždycky použít relativní koncový bod adresy pro koncové body služby hostované službou IIS. Poskytuje úplný koncový bod adresu (například http://localhost/MyService.svc) může vést k chybám v nasazení služby, pokud adresa koncového bodu neukazuje na IIS – aplikace, který je hostitelem služby vystavení koncový bod. Použitím relativní koncový bod adresy pro hostované služby se vyhnete tyto potenciální konflikty.  
  
### <a name="available-transports"></a>K dispozici přenosy  
 Služby WCF hostované ve službě IIS 5.1 a [!INCLUDE[iis601](../../../../includes/iis601-md.md)] jsou omezeny na pomocí komunikace na základě protokolu HTTP. Na těchto platformách IIS konfigurace hostované služby pro použití vazby jiným protokolem než HTTP vede k chybě během aktivace služby. Pro [!INCLUDE[iisver](../../../../includes/iisver-md.md)], podporovaných přenosů zahrnují HTTP, Net.TCP, Net.Pipe, Net.MSMQ a msmq.formatname pro zpětné kompatibilitě se stávajícími aplikacemi služby MSMQ.  
  
### <a name="http-transport-security"></a>Zabezpečení přenosu HTTP  
 Služby WCF hostované IIS může využívat HTTP virtuálního adresáře služby IIS, který obsahuje službu podporuje ty přenosu zabezpečení (například schémata HTTPS a HTTP ověřování například Basic, ověřování algoritmem Digest a integrované ověřování systému Windows) nastavení. Nastavení zabezpečení přenosu HTTP na hostovaný koncový bod vazby musí odpovídat nastavení zabezpečení přenosu na virtuální adresář služby IIS, který jej obsahuje.  
  
 Například koncový bod WCF, který je nakonfigurovaný na použití ověřování algoritmem digest HTTP se musí nacházet v virtuální adresář služby IIS, který je také nakonfigurovaný na použití ověřování algoritmem digest HTTP. Neodpovídající kombinace nastavení služby IIS a nastavení pro koncový bod WCF za následek chybu během aktivace služby.  
  
## <a name="see-also"></a>Viz také  
 [Hostování v Internetové informační službě](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Osvědčené postupy hostování Internetové informační služby](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
