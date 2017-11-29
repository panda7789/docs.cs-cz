---
title: "Aktivace pojmenovaného kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55594e1505e60ede8d7c6abcbd8a9cf9a1f739bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="namedpipe-activation"></a>Aktivace pojmenovaného kanálu
Tento příklad znázorňuje hostování služby, která využívá služba aktivace procesů systému Windows (WAS) k aktivaci služby, který komunikuje přes názvy kanály. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a vyžaduje [!INCLUDE[wv](../../../../includes/wv-md.md)] ke spuštění.  
  
> [!NOTE]
>  Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Ukázka se skládá z konzoly programu klienta (.exe) a služby knihovny (DLL) hostované v pracovním procesu aktivovat pomocí proces aktivace služby WAS (Windows). Činnost klienta je viditelný v okně konzoly.  
  
 Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi. Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (přidat, odečíst, násobení a dělení), jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 Klient zadává synchronní požadavků pro danou matematické operace a implementaci služby vypočítá a vrátí odpovídající výsledek.  
  
```  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 Příklad používá upravené `netNamedPipeBinding` vazba se zabezpečení. Vazba je zadána v konfiguračních souborech pro klienta a služby. Typ vazby služby je zadaný v elementu koncový bod `binding` atributu, jak je znázorněno v následující ukázka konfigurace.  
  
 Pokud chcete použít vazbu zabezpečené pojmenovaný kanál, změňte režim zabezpečení serveru nastavení požadované zabezpečení a znovu spusťte svcutil.exe na klientovi se získat konfigurační soubor aktualizovaného klienta.  
  
```xml  
<system.serviceModel>  
        <services>  
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
  
        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->  
        <endpoint address=""   
                  binding="netNamedPipeBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexNamedPipeBinding"  
                  contract="IMetadataExchange" />  
      </service>  
        </services>      
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="Binding1" >  
                    <security mode = "None">  
                    </security>  
                </binding >  
            </netNamedPipeBinding>  
        </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 Informace o koncovém klienta je nakonfigurován, jak je znázorněno v následujícím ukázkovém kódu.  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <endpoint name=""  
                          address="net.pipe://localhost/servicemodelsamples/service.svc"   
                          binding="netNamedPipeBinding"   
                          bindingConfiguration="Binding1"   
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
    <bindings>  
  
      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.  
            Each property is configured with the default value.   -->  
  
      <netNamedPipeBinding>  
        <binding name="Binding1"   
                         maxBufferSize="65536"  
                         maxConnections="10">  
          <security mode = "None">  
          </security>  
        </binding >  
  
      </netNamedPipeBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že [!INCLUDE[iisver](../../../../includes/iisver-md.md)] je nainstalovaná. [!INCLUDE[iisver](../../../../includes/iisver-md.md)]je vyžadována pro aktivace WAS.  
  
2.  Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
     Kromě toho je nutné nainstalovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Aktivace jiným protokolem než HTTP součásti:  
  
    1.  Z **spustit** nabídce zvolte **ovládací panely**.  
  
    2.  Vyberte **programy a funkce**.  
  
    3.  Klikněte na tlačítko **součásti systému Windows vypnutí a zapnutí**.  
  
    4.  Rozbalte **rozhraní Microsoft .NET Framework 3.0** uzlu a kontroly **Aktivace jiným protokolem než HTTP Windows Communication Foundation** funkce.  
  
3.  Konfigurace proces aktivace služby WAS (Windows) pro podporu aktivace pojmenovaného kanálu.  
  
     Pro potřeby následující dva kroky jsou implementované v dávkovém souboru názvem AddNetPipeSiteBinding.cmd umístěný v adresáři ukázka.  
  
    1.  Kvůli podpoře aktivace net.pipe, musí být nejprve vázána výchozí web na protokol net.pipe. To lze provést pomocí appcmd.exe, která se instaluje s sady nástrojů pro správu služby IIS 7.0. Z příkazového řádku s oprávněními zvýšenými na úroveň (správce) spusťte následující příkaz.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je na jednom řádku textu.  
  
         Tento příkaz přidá net.pipe vazba webu default Web site.  
  
    2.  Přestože všechny aplikace v rámci lokality sdílejí společné net.pipe vazbu, každá aplikace můžete povolit podporu net.pipe jednotlivě. Pokud chcete povolit net.pipe /servicemodelsamples aplikace, spusťte následující příkaz z příkazového řádku se zvýšenými oprávněními.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe  
        ```  
  
        > [!NOTE]
        >  Tento příkaz je na jednom řádku textu.  
  
         Tento příkaz umožňuje získat přístup pomocí http://localhost/servicemodelsamples a net.tcp://localhost/servicemodelsamples /servicemodelsamples aplikaci.  
  
4.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Odeberte net.pipe vazby webu, který jste přidali Tato ukázka.  
  
     Pro potřeby následující dva kroky jsou implementované v dávkovém souboru názvem RemoveNetPipeSiteBinding.cmd umístěný v adresáři ukázka:  
  
    1.  Odeberte net.tcp ze seznamu povolených protokolů spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Tento příkaz musí být zadán jako jeden řádek textu.  
  
    2.  Odeberte vazbu webu net.tcp spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  Tento příkaz musí být zadán v jako jeden řádek textu.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
