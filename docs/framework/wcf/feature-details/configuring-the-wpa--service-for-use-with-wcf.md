---
title: Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 86e50b80d84479ca32b3d4d1fe3f205983640c76
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464173"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation
Toto téma popisuje kroky potřebné k nastavení služby aktivace procesů systému Windows (označované také jako WAS) v systému Windows Vista pro hostování služeb WCF (Windows Communication Foundation), které nekomunikují prostřednictvím síťových protokolů HTTP. Následující části popisují kroky pro tuto konfiguraci:  
  
- Nainstalujte (nebo potvrďte instalaci) požadovaných aktivačních komponent WCF.  
  
- Vytvořte lokalitu WAS s vazbami síťového protokolu, které chcete použít, nebo přidejte novou vazbu protokolu do existující lokality.  
  
- Vytvořte aplikaci pro hostování vašich služeb a povolte jí používat požadované síťové protokoly.  
  
- Vytvořte službu WCF, která zveřejňuje koncový bod bez protokolu HTTP.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Konfigurace webu pomocí vazeb, které nejsou http  
 Chcete-li použít nehttp vazbu s WAS, musí být vazba lokality přidána do konfigurace WAS. Úložiště konfigurace služby WAS je soubor applicationHost.config umístěný v adresáři %windir%\system32\inetsrv\config. Toto úložiště konfigurace je sdíleno službou WAS i službou IIS 7.0.  
  
 applicationHost.config je textový soubor XML, který lze otevřít pomocí libovolného standardního textového editoru (například Poznámkový blok). Konfigurační nástroj příkazového řádku služby IIS 7.0 (appcmd.exe) je však upřednostňovaným způsobem přidání vazeb webu bez protokolu HTTP.  
  
 Následující příkaz přidá vazbu webu net.tcp na výchozí web pomocí programu appcmd.exe (tento příkaz je zadán jako jeden řádek).  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Tento příkaz přidá novou vazbu net.tcp na výchozí web přidáním řádku uvedeného níže do souboru applicationHost.config.  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Povolení aplikace používat protokoly bez protokolu HTTP  
 Můžete povolit nebo zakázat jednotlivé síťové protokoly na úrovni aplikace. Následující příkaz ukazuje, jak povolit protokoly HTTP i net.tcp pro `Default Web Site`aplikaci spuštěnou v rozhraní .  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Seznam povolených protokolů lze také \<nastavit v applicationDefaults> prvek konfigurace XML webu uložený v souboru ApplicationHost.config.  
  
 Následující kód XML z applicationHost.config ilustruje web vázaný na protokoly HTTP i non-HTTP. Další konfigurace potřebná pro podporu protokolů bez protokolu HTTP je volána s komentáři.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
      <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
      </application>  
      <bindings>  
            <!-- The following two lines are added by the command. -->
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
      <!-- The following line is inserted by the command. -->
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 Pokud se pokusíte aktivovat službu pomocí služby WAS pro aktivaci bez protokolu HTTP a nenainstalovali jste a nenakonfigurovali službu WAS, může se zobrazit následující chyba:  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Pokud se zobrazí tato chyba, ujistěte se, že was pro aktivaci bez protokolu HTTP je nainstalován a správně nakonfigurován. Další informace naleznete v [tématu How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Vytváření služby WCF, která používá službu WAS pro aktivaci bez protokolu HTTP  
 Jakmile provedete kroky k instalaci a konfiguraci služby WAS (viz [Postup: Instalace a konfigurace součástí aktivace WCF),](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)konfigurace služby pro použití služby WAS pro aktivaci je podobná konfiguraci služby hostované ve službě IIS.  
  
 Podrobné pokyny k vytváření služby WCF aktivované službou WAS naleznete v tématu [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Viz také

- [Hostování v Aktivační službě procesů systému Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- [Funkce hostování prostředků pro aplikace systému Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
