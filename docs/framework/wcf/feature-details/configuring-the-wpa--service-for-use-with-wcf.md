---
title: Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 6e74c81aa26ba7f8d093b8b3ec52f19eb3519905
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489783"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation
Toto téma popisuje kroky potřebné k nastavení služby Aktivace procesu Windows (WAS) v [!INCLUDE[wv](../../../../includes/wv-md.md)] k hostování Windows Communication Foundation (WCF) služby, které nekomunikují přes protokol HTTP síťových protokolů. Následující oddíly popisují kroky pro tuto konfiguraci:  
  
-   Nainstalovat (nebo potvrďte instalaci) aktivačních komponent WCF vyžaduje.  
  
-   Vytvoření webu WAS se vazeb síťových protokolů, které chcete použít, nebo přidat novou vazbu protokolu o stávající web.  
  
-   Vytvořte aplikaci pro hostování služeb a povolte tuto aplikaci používat požadované protokoly.  
  
-   Vytvoření služby WCF, který zpřístupňuje koncový bod jiným protokolem než HTTP.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Konfigurace sítě s vazbami jiným protokolem než HTTP  
 Pro použití vazby jiným protokolem než HTTP s WAS, musí přidat vazbu webu do konfigurace WAS. Konfigurace úložiště pro WAS je soubor applicationHost.config umístěný v adresáři %windir%\system32\inetsrv\config. Tato konfigurace úložiště je sdílen WAS a IIS 7.0.  
  
 soubor applicationHost.config je textový soubor XML, který lze otevřít v libovolném standardního textového editoru (například Poznámkový blok). Ale [!INCLUDE[iisver](../../../../includes/iisver-md.md)] preferovaný způsob, jak přidat vazby webu jiným protokolem než HTTP je nástroj příkazového řádku konfigurace (appcmd.exe).  
  
 Následující příkaz přidá vazbu webu net.tcp výchozí webový server pomocí appcmd.exe (Tento příkaz je zadat jako jeden řádek).  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Tento příkaz přidá novou vazbu net.tcp výchozí webový server tak, že přidáte řádku níže uvedeného souboru applicationHost.config.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Povolení aplikace pro použití jiných protokolů než HTTP  
 Můžete povolit nebo zakázat jednotlivým síťovým protocolsat na úrovni aplikace. Následující příkaz ukazuje, jak povolit protokoly HTTP i net.tcp pro aplikace, která běží v `Default Web Site`.  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Seznam Povolené protokoly je možné také nastavit v \<applicationDefaults > element konfigurace XML pro lokalitu uložené v souboru ApplicationHost.config.  
  
 Následující kód XML ze souboru applicationHost.config znázorňuje lokality vázána na HTTP a jiných protokolů než HTTP. Další konfigurace vyžadovaná pro podporu jiných protokolů než HTTP je vyznačeny pomocí komentářů.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
    <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
    </application>  
       <bindings>  
            //The following two lines are added by the command.  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile   
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging   
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults   
      applicationPool="DefaultAppPool"   
      //The following line is inserted by the command.  
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 Pokud při pokusu o aktivaci služby pomocí služby WAS Aktivace jiným protokolem než HTTP a ještě nainstalovaná a nakonfigurovaná služba WAS může se zobrazit následující chyba:  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Pokud se zobrazí tato chyba, zkontrolujte WAS pro aktivace jiným protokolem než HTTP je nainstalován a nakonfigurován správně. Další informace najdete v tématu [postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Vytváření WCF službě, používá se pro aktivace jiným protokolem než HTTP  
 Jakmile provedete kroky instalace a konfigurace služby WAS (naleznete v tématu [postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), konfigurace služby WAS použít aktivace je podobné konfigurace služby, která je hostovaná ve službě IIS.  
  
 Podrobné pokyny k vytvoření služby WCF aktivaci WAS, naleznete v tématu [postupy: hostování služby WCF ve WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Viz také  
 [Hostování v Aktivační službě procesů systému Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
