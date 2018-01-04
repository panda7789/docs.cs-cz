---
title: "Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12df9e3760774b4dc8d4e8f73a09df5e79c2453e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation
Toto téma popisuje kroky potřebné k nastavení aktivační služba procesů systému Windows (WAS) v [!INCLUDE[wv](../../../../includes/wv-md.md)] hostitele [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby, které není komunikaci pomocí protokolu HTTP síťových protokolů. Následující oddíly popisují kroky pro tuto konfiguraci:  
  
-   Nainstalovat (nebo potvrďte instalace) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] požadované součásti aktivace.  
  
-   Vytvořit web WAS s vazeb síťových protokolů, které chcete použít, nebo přidat novou vazbu protokolu na existující web.  
  
-   Vytvořte aplikaci pro hostování vaší služeb a povolte tuto aplikaci používat požadovaných síťových protokolů.  
  
-   Sestavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, která zveřejňuje koncový bod jiným protokolem než HTTP.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Konfigurace sítě s jiným protokolem než HTTP vazby  
 Pokud chcete použít vazbu jiným protokolem než HTTP službou WAS, musí konfigurace WAS přidat vazby webu. Konfigurace úložiště pro WAS je soubor applicationHost.config umístěný v adresáři %windir%\system32\inetsrv\config. Toto úložiště konfigurace sdílí WAS a IIS 7.0.  
  
 applicationHost.config je textový soubor s XML, který lze otevřít v libovolném standardního textového editoru (například Poznámkový blok). Ale [!INCLUDE[iisver](../../../../includes/iisver-md.md)] nástroje příkazového řádku konfigurace (appcmd.exe) je upřednostňovaný způsob, jak přidat vazby webu jiným protokolem než HTTP.  
  
 Následující příkaz přidá vazbu net.tcp lokality na výchozí web pomocí appcmd.exe (Tento příkaz je zadán jako jeden řádek).  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Tento příkaz přidá novou vazbu net.tcp výchozí web přidáním řádku níže uvedeného v souboru applicationHost.config.  
  
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
 Můžete povolit nebo zakázat jednotlivým síťovým protocolsat na úrovni aplikace. Následující příkaz ukazuje, jak povolit protokoly HTTP i net.tcp pro aplikaci, která běží v `Default Web Site`.  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Seznam Povolené protokoly lze nastavit i v \<applicationDefaults > elementu XML konfigurace lokality uložené v souboru ApplicationHost.config.  
  
 Následující kód XML ze souboru applicationHost.config znázorňuje lokality vázána na protokolu HTTP a jiných protokolů než HTTP. Další konfigurace vyžadovaná pro podporu jiných protokolů než HTTP se nazývá s komentáři.  
  
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
  
 Pokud se pokusíte aktivovat službu pomocí WAS Aktivace jiným protokolem než HTTP a ještě nainstalován a nakonfigurován WAS mohou se zobrazit chybová zpráva:  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Pokud se zobrazí tato chyba, zkontrolujte WAS pro aktivace jiným protokolem než HTTP je nainstalován a nakonfigurován správně. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Vytváření WCF služby, používá se pro aktivace jiným protokolem než HTTP  
 Po provedení kroků k instalaci a konfiguraci služby WAS (najdete v části [postupy: instalace a konfigurace aktivačních komponent WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), konfigurace služby k použití WAS pro aktivace je podobná konfigurace služby, který je hostován ve službě IIS.  
  
 Podrobné pokyny o vytváření WAS aktivované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] najdete v tématu [postupy: hostování služby WCF ve WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Viz také  
 [Hostování v Aktivační službě procesů systému Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
