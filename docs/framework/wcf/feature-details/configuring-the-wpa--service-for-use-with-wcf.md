---
title: Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 06d3a7bd798913b06d342ac09d12e736fc436b3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597498"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Konfigurace služby aktivace procesu Windows pro použití s Windows Communication Foundation
Toto téma popisuje kroky potřebné k nastavení aktivační služby procesů systému Windows (označované také jako WAS) ve Windows Vista na hostování služeb Windows Communication Foundation (WCF), které nekomunikují přes síťové protokoly HTTP. Následující části popisují kroky pro tuto konfiguraci:  
  
- Nainstalujte (nebo potvrďte instalaci produktu) požadované komponenty aktivace WCF.  
  
- Vytvořte lokalitu s použitím vazeb síťových protokolů, které chcete použít, nebo přidejte novou vazbu protokolu k existující lokalitě.  
  
- Vytvořte aplikaci pro hostování služeb a povolte, aby tato aplikace používala požadované síťové protokoly.  
  
- Sestavte službu WCF, která zveřejňuje koncový bod jiného typu než HTTP.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Konfigurace lokality s vazbami jiného typu než HTTP  
 Chcete-li použít vazbu jiného typu než HTTP s nástrojem, musí být vazba webu přidána do konfigurace WAS. Úložiště konfigurace pro byl soubor applicationHost. config, který se nachází v adresáři%windir%\system32\inetsrv\config. Toto úložiště konfigurace sdílí i služba IIS 7,0.  
  
 applicationHost. config je textový soubor XML, který lze otevřít pomocí standardního textového editoru (například Poznámkový blok). Konfigurační nástroj příkazového řádku IIS 7,0 (Appcmd. exe) je ale upřednostňovaným způsobem, jak přidat vazby jiných než HTTP lokalit.  
  
 Následující příkaz přidá k výchozímu webovému serveru vazbu sítě NET. TCP pomocí nástroje Appcmd. exe (Tento příkaz je zadaný jako jeden řádek).  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Tento příkaz přidá novou vazbu NET. TCP na výchozí web přidáním řádku uvedeného níže do souboru applicationHost. config.  
  
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
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Povolení používání jiných protokolů než HTTP  
 Můžete povolit nebo zakázat jednotlivé sítě protocolsat na úrovni aplikace. Následující příkaz ukazuje, jak povolit protokoly HTTP i NET. TCP pro aplikaci, která běží v `Default Web Site` .  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Seznam povolených protokolů lze také nastavit v \<applicationDefaults> prvku konfigurace XML webu uloženého v souboru ApplicationHost. config.  
  
 Následující kód XML z souboru applicationHost. config ukazuje lokalitu, která je vázaná na protokoly HTTP i non-HTTP. Další konfigurace požadovaná pro podporu jiných protokolů než HTTP se nazývá s komentáři.  
  
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
  
 Pokud se pokusíte aktivovat službu pomocí nástroje pro aktivaci jiným způsobem než HTTP a nejste nainstalovali a nakonfigurovali jste, může se zobrazit následující chyba:  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Pokud se zobrazí tato chyba, zajistěte, aby byla správně nainstalovaná a nakonfigurovaná aktivace bez protokolu HTTP. Další informace najdete v tématu [Postupy: instalace a konfigurace aktivačních komponent WCF](how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Vytvoření služby WCF, která se používá pro aktivaci bez protokolu HTTP  
 Po provedení kroků k instalaci a nakonfigurování (viz [Postup: instalace a konfigurace aktivačních komponent WCF](how-to-install-and-configure-wcf-activation-components.md)) konfigurace služby, která se má použít pro aktivaci, je podobná konfiguraci služby hostované ve službě IIS.  
  
 Podrobné pokyny k vytvoření aktivované služby WCF najdete v tématu [How to: Host a služba WCF v](how-to-host-a-wcf-service-in-was.md)nástroji.  
  
## <a name="see-also"></a>Viz také

- [Hostování v Aktivační službě procesů systému Windows](hosting-in-windows-process-activation-service.md)
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
