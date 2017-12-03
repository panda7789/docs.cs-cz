---
title: "Nasazení služby WCF hostované Internetovou informační službou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04ebd329-3fbd-44c3-b3ab-1de3517e27d7
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9b19e111e11097cbb4b4af60ae0b28956a4a381
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-an-internet-information-services-hosted-wcf-service"></a>Nasazení služby WCF hostované Internetovou informační službou
Vývoj a nasazení [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby, který je hostován v Internetové informační služby (IIS) se skládá z následujících úloh:  
  
-   Ujistěte se, zda služba IIS, ASP.NET, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aktivace součásti jsou správně nainstalováno a zaregistrován.  
  
-   Vytvoření nové aplikace služby IIS, nebo znovu použijte existující [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.  
  
-   Vytvořte soubor .svc pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
-   Implementace služby nasaďte do aplikace služby IIS.  
  
-   Konfigurace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
 Podrobný návod hostované službou IIS vytváření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] najdete v tématu [postupy: hostování služby WCF ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="ensure-that-iis-aspnet-and-wcf-are-correctly-installed-and-registered"></a>Zajistěte, aby služba IIS, ASP.NET a WCF správně nainstalovaný a registrovaný  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], Musí být nainstalována služba IIS a ASP.NET hostované službou IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, aby správně fungoval. Postupy pro instalaci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (jako součást [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]), ASP.NET a IIS lišit v závislosti na verzi operačního systému používá. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]instalace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], najdete v části [instalačního programu webové rozhraní Microsoft .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=201185). Pokyny k instalaci služby IIS najdete na [instalace služby IIS](http://go.microsoft.com/fwlink/?LinkId=201188).  
  
 Proces instalace [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] zaregistruje automaticky [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službou IIS, pokud služba IIS již na tomto počítači. Pokud po instalaci služby IIS [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], další krok je nutný k registraci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službou IIS a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Můžete to udělat takto, v závislosti na operačním systému:  
  
-   [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], Windows 7, a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]: použijte [nástroj ServiceModel Registration (ServiceModelReg.exe)](../../../../docs/framework/wcf/servicemodelreg-exe.md) nástroj pro registraci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí služby IIS: Chcete-li tento nástroj používat, zadejte **ServiceModelReg.exe /i /x** v příkazového řádku Visual Studia. Můžete otevřít tento příkaz řádku pomocí kliknutím na tlačítko start, výběr **všechny programy**, **sadu Microsoft Visual Studio 2012**, **nástroje sady Visual Studio**, a  **Visual Studio – příkazový řádek**  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)]: Nainstalujte součásti systému Windows Communication Foundation aktivace podsoučásti z [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]. Chcete-li to provést, v Ovládacích panelech, klikněte na tlačítko **přidat nebo odebrat programy** a potom **přidat\/odebrat součásti systému Windows**. Tím dojde k aktivaci **Průvodce součástmi systému Windows**.  
  
-   Windows 7:  
  
 Nakonec je třeba ověřit, že technologie ASP.NET je nakonfigurovaný na použití rozhraní .NET Framework verze 4. To uděláte tak, že spustíte nástroj ASPNET_Regiis s – i možnost. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ASP.NET IIS Registration Tool](http://go.microsoft.com/fwlink/?LinkId=201186)  
  
## <a name="create-a-new-iis-application-or-reuse-an-existing-aspnet-application"></a>Vytvoření nové aplikace služby IIS nebo znovu použijte stávající aplikaci ASP.NET  
 Hostované službou IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby se musí nacházet v rámci aplikace služby IIS. Můžete vytvořit novou aplikaci služby IIS na hostitele [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] výhradně služeb. Alternativně můžete nasadit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby do existující aplikace, která již hostuje [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] obsahu (například stránky .aspx a webových služeb ASP.NET [ASMX]). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tyto možnosti najdete v článku "hostitelský WCF-souběžného s technologií ASP.NET" a "Hostování WCF Services v ASP.NET režim kompatibility" části [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
 Všimněte si, že [!INCLUDE[iis601](../../../../includes/iis601-md.md)] a novějších verzích pravidelně restartovala izolované objektově orientované programování aplikace. Výchozí hodnota je 1740 minut. Maximální podporovaná hodnota je 71,582 minut. Tento restart můžete zakázat. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tato vlastnost, najdete v článku [PeriodicRestartTime](http://go.microsoft.com/fwlink/?LinkId=109968).  
  
## <a name="create-an-svc-file-for-the-wcf-service"></a>Vytvořte soubor .svc služby WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby hostované ve službě IIS, jsou reprezentovány jako speciální soubory obsahu (souborů .svc) uvnitř aplikace služby IIS. Tento model je podobná způsob, jakým jsou v rámci aplikace IIS jako souborů .asmx reprezentované ASMX stránky. Obsahuje soubor .svc [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]– direktivy konkrétní zpracování ([@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)), který umožňuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hostování infrastruktury aktivovat hostované služby v reakci na příchozí zprávy. Nejběžnější syntaxe pro soubor .svc je v následujícím příkazu.  
  
```  
<% @ServiceHost Service="MyNamespace.MyServiceImplementationTypeName" %>  
```  
  
 Skládá se z [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice a jeden atribut, `Service`. Hodnota `Service` atribut je běžný název typu language runtime (CLR) implementace služby. Pomocí tato direktiva je v podstatě ekvivalentní vytvoření hostitele služby pomocí následujícího kódu.  
  
```  
new ServiceHost( typeof( MyNamespace.MyServiceImplementationTypeName ) );  
```  
  
 Můžete také provést další konfiguraci hostování, jako je například vytváření seznam základní adresy pro službu. Můžete také použít vlastní <xref:System.ServiceModel.Activation.ServiceHostFactory> rozšířit směrnice pro použití s vlastní řešení hostování. Aplikace služby IIS, které jsou hostiteli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby nejsou zodpovědní za správu vytváření a dobu života <xref:System.ServiceModel.ServiceHost> instance. Spravovaný [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting infrastruktury vytvoří nezbytné <xref:System.ServiceModel.ServiceHost> instance dynamicky při prvním požadavku je pro soubor .svc. Instance není vydala, dokud buď je uzavřený explicitně pomocí kódu nebo pokud je aplikace recykluje.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Syntaxe souborů .svc, najdete v části [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md).  
  
## <a name="deploy-the-service-implementation-to-the-iis-application"></a>Nasazení implementace služby do aplikace služby IIS  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby hostované ve službě IIS použít stejný model dynamická kompilace jako [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)]. Jenom jako s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], můžete nasadit kód implementace pro hostované službou IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služeb několika způsoby v různých umístěních, následujícím způsobem:  
  
-   Jako soubor s příponou DLL předkompilovaných nachází v globální mezipaměti sestavení (GAC) nebo v adresáři \bin aplikace. Předkompilované binární soubory nejsou aktualizovány, dokud je nasadit novou verzi knihovny tříd.  
  
-   Jako zrušení kompilované zdrojové soubory umístěné v adresáři \App_Code aplikace. Zdrojové soubory, které jsou umístěné v tomto adresáři se dynamicky vyžadují při zpracování aplikace první žádosti. Všechny změny souborů v adresáři \App_Code způsobit celá aplikace recyklované a překompilovat, při příští žádosti o přijetí.  
  
-   Jak přímo v souboru .svc umístit zrušení zkompilovaný kód. Implementace kód může být také součástí textu v souboru .svc služby po @ServiceHost – direktiva. Všechny změny vloženého kódu způsobit, že aplikace recyklované a překompilovat, při příští žádosti o přijetí.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] kompilace modelu, najdete v části [kompilace ASP.NET: Přehled](http://go.microsoft.com/fwlink/?LinkId=94773).  
  
## <a name="configure-the-wcf-service"></a>Konfigurace služby WCF  
 Hostované službou IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby ukládat své konfigurace v souboru Web.config aplikace. Hostované službou IIS služby používat stejnou syntaxi jako a konfigurace – elementy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby hostované mimo služby IIS. Nicméně jsou jedinečné pro hostitelské prostředí služby IIS následující omezení:  
  
-   Základní adresy pro služby hostované službou IIS.  
  
-   Hostování aplikace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služeb mimo službu IIS můžete řídit základní adresa služby hostují předáním sadu základní adresa identifikátory URI k <xref:System.ServiceModel.ServiceHost> konstruktor nebo poskytováním [ \<hostitele >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) element v konfiguraci služby. Služby hostované ve službě IIS nemají možnost řídit jejich základní adresa; Základní adresa služby hostované službou IIS je adresa jeho .svc souboru.  
  
### <a name="endpoint-addresses-for-iis-hosted-services"></a>Adresy koncových bodů pro služby hostované službou IIS  
 Když jsou hostované v IIS, adresy koncových bodů se vždy považují za relativní k adrese .svc soubor, který představuje službu. Například pokud bázové adresy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby je http://localhost/Application1/MyService.svc s následující konfigurací koncového bodu.  
  
```xml  
<endpoint address="anotherEndpoint" .../>  
```  
  
 To poskytuje koncový bod, který lze dosáhnout za "http://localhost/Application1/MyService.svc/anotherEndpoint".  
  
 Podobně elementu konfigurace koncového bodu, který používá prázdný řetězec jako relativní adresa poskytuje koncový bod dostupný v http://localhost/Application1/MyService.svc, což je základní adresa.  
  
```xml  
<endpoint address="" ... />  
```  
  
 Musíte vždycky použít relativní koncový bod adresy pro koncové body služby hostované službou IIS. Poskytuje úplný koncový bod adresu (například http://localhost/MyService.svc) může vést k chyby v nasazení služby, pokud adresa koncového bodu neukazuje na IIS – aplikace, který je hostitelem služby vystavení koncový bod. Použitím relativní koncový bod adresy pro hostované služby se vyhnete tyto potenciální konflikty.  
  
### <a name="available-transports"></a>K dispozici přenosy  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby hostované v IIS 5.1 a [!INCLUDE[iis601](../../../../includes/iis601-md.md)] jsou omezeny na pomocí komunikace na základě protokolu HTTP. Na těchto platformách IIS konfigurace hostované služby pro použití vazby jiným protokolem než HTTP vede k chybě během aktivace služby. Pro [!INCLUDE[iisver](../../../../includes/iisver-md.md)], podporovaných přenosů zahrnují HTTP, Net.TCP, Net.Pipe, Net.MSMQ a msmq.formatname pro zpětné kompatibilitě se stávajícími aplikacemi služby MSMQ.  
  
### <a name="http-transport-security"></a>Zabezpečení přenosu HTTP  
 Hostované službou IIS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby může využívat HTTP podporuje virtuálního adresáře služby IIS, který obsahuje službu přenosu zabezpečení (například schémata HTTPS a HTTP ověřování například Basic, ověřování algoritmem Digest a integrované ověřování systému Windows) Tato nastavení. Nastavení zabezpečení přenosu HTTP na hostovaný koncový bod vazby musí odpovídat nastavení zabezpečení přenosu na virtuální adresář služby IIS, který jej obsahuje.  
  
 Například [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod nakonfigurovaný na použití ověřování algoritmem digest HTTP se musí nacházet ve virtuální adresář služby IIS, který je také nakonfigurovaný na použití ověřování algoritmem digest HTTP. Neodpovídající kombinace nastavení služby IIS a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod nastavení vést k chybě během aktivace služby.  
  
## <a name="see-also"></a>Viz také  
 [Hostování v Internetové informační službě](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Doporučené postupy hostování internetové informační služby](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
