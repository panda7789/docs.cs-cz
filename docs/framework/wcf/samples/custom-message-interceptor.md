---
title: Vlastní zachycování zpráv
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 433b14433a7e2dd6edad551a2732e9049a9861ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145083"
---
# <a name="custom-message-interceptor"></a>Vlastní zachycování zpráv
Tato ukázka ukazuje použití modelu rozšiřitelnosti kanálu. Zejména ukazuje, jak implementovat vlastní element vazby, který vytváří továrny kanálu a naslouchací procesy kanálu zachytit všechny příchozí a odchozí zprávy v určitém bodě v zásobníku za běhu. Ukázka také obsahuje klienta a server, které ukazují použití těchto vlastních továren.  
  
 V této ukázce jsou klient a služba konzolové programy (.exe). Klient i služba využívají společnou knihovnu (.dll), která obsahuje vlastní element vazby a jeho přidružené objekty run-time.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 Ukázka popisuje doporučený postup pro vytvoření vlastního vrstveného kanálu v systému Windows Communication Foundation (WCF), pomocí rozhraní kanálu a podle doporučených postupů WCF. Postup vytvoření vlastního vrstveného kanálu je následující:  
  
1. Rozhodněte, který z obrazců kanálu bude podporovat váš kanál a naslouchací proces kanálu.  
  
2. Vytvořte továrnu kanálu a naslouchací proces kanálu, které podporují obrazce kanálu.  
  
3. Přidejte element vazby, který přidá vlastní vrstvený kanál do zásobníku kanálu.  
  
4. Přidejte oddíl rozšíření elementu vazby, který zpřístupní nový element vazby do konfiguračního systému.  
  
## <a name="channel-shapes"></a>Obrazce kanálů  
 Prvním krokem při psaní vlastního vrstveného kanálu je rozhodnutí, které obrazce jsou pro kanál vyžadovány. Pro naše zprávy inspektor, podporujeme jakýkoli tvar, který vrstva pod námi <xref:System.ServiceModel.Channels.IOutputChannel> podporuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel>(například <xref:System.ServiceModel.Channels.IOutputChannel> v <xref:System.ServiceModel.Channels.IDuplexSessionChannel>případě, že vrstva pod námi může stavět a , pak jsme také vystavit a ).  
  
## <a name="channel-factory-and-listener-factory"></a>Továrna kanálu a naslouchací proces  
 Dalším krokem při psaní vlastního vrstveného kanálu <xref:System.ServiceModel.Channels.IChannelFactory> je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelListener> pro klientské kanály a pro kanály služeb.  
  
 Tyto třídy trvat vnitřní factory a `OnCreateChannel` naslouchací proces a delegovat všechny, ale a `OnAcceptChannel` volání vnitřní factory a naslouchací proces.  
  
```csharp
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{
    //...
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a>Přidání prvku vazby  
 Ukázka definuje vlastní prvek `InterceptingBindingElement`vazby: . `InterceptingBindingElement`bere `ChannelMessageInterceptor` jako vstup a používá `ChannelMessageInterceptor` jej k manipulaci se zprávami, které procházejí. Tohle je jediná třída, která musí být veřejná. Factory, naslouchací proces a kanály mohou být interní implementace veřejných rozhraní run-time.  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 Chcete-li integrovat s konfigurací vazby, knihovna definuje obslužnou rutinu oddílu konfigurace jako oddíl rozšíření prvku vazby. Konfigurační soubory klienta a serveru musí zaregistrovat příponu elementu vazby s konfiguračním systémem. Implementátory, které chtějí vystavit jejich element vazby konfiguračního systému můžete odvodit z této třídy.  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a>Přidání zásad  
 Chcete-li integrovat s `InterceptingBindingElement` naším systémem zásad, implementuje IPolicyExportExtension signál, že bychom se měli podílet na generování politiky. Pro podporu importu zásad na generovaném klientovi může uživatel `InterceptingBindingElementImporter` zaregistrovat `CreateMessageInterceptor`odvozenou třídu a `ChannelMessageInterceptor` přepsat () a vygenerovat třídu s povoleným zásadami.  
  
## <a name="example-droppable-message-inspector"></a>Příklad: Inspektor zasahovavých zpráv  
 Součástí ukázky je příklad `ChannelMessageInspector` implementace, která kapky zprávy.  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Můžete k němu přistupovat z konfigurace následujícím způsobem:  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 Klient i server používají tuto nově vytvořenou část konfigurace k vložení vlastních továren do nejnižší úrovně jejich zásobníků kanálu za běhu (nad úrovní přenosu).  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 Klient používá `MessageInterceptor` knihovnu k přidání vlastní hlavičky do sudých číslovaných zpráv. Služba na druhé straně `MessageInterceptor` používá knihovnu k přetažení všech zpráv, které nemají tuto speciální hlavičku.  
  
 Po spuštění služby a potom na straně klienta byste měli vidět následující výstup klienta.  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 Klient hlásí službě 10 různých rychlostí větru, ale polovinu z nich označí pouze speciální hlavičkou.  
  
 Ve službě byste měli vidět následující výstup:  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Nejprve spusťte soubor Service.exe, poté spusťte soubor Client.exe a sledujte výstup obou oken konzoly.  
