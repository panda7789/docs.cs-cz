---
title: Vlastní zachycování zpráv
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 61f9bae24f5edb70430f4f3eaa16e42da221a7b4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978301"
---
# <a name="custom-message-interceptor"></a>Vlastní zachycování zpráv
Tato ukázka demonstruje použití modelu rozšiřitelnosti kanálu. Konkrétně ukazuje, jak implementovat vlastní prvek vazby, který vytváří objekty pro vytváření kanálů a naslouchací procesy kanálu pro zachycení všech příchozích a odchozích zpráv v určitém bodě v zásobníku běhu. Ukázka zahrnuje také klienta a server, který předvádí použití těchto vlastních továrn.  
  
 V této ukázce jsou klientem i služba konzolové programy (. exe). Klient a služba obě využívají společnou knihovnu (. dll), která obsahuje vlastní prvek vazby a příslušné objekty modulu runtime.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 Ukázka popisuje doporučený postup pro vytvoření vlastního vrstveného kanálu v Windows Communication Foundation (WCF) pomocí architektury kanálů a následujících osvědčených postupů pro WCF. Postup vytvoření vlastního vrstveného kanálu je následující:  
  
1. Rozhodněte, které z obrazců kanálů bude podporovat objekt pro vytváření kanálů a naslouchací proces kanálu.  
  
2. Vytvořte objekt pro vytváření kanálů a naslouchací proces kanálu, který podporuje obrazce kanálu.  
  
3. Přidejte prvek vazby, který přidá vlastní vrstvený kanál do zásobníku kanálů.  
  
4. Přidejte část rozšíření elementu vazby, která zpřístupňuje nový prvek vazby na konfigurační systém.  
  
## <a name="channel-shapes"></a>Obrazce kanálu  
 Prvním krokem při psaní vlastního vrstveného kanálu je rozhodování o tom, které obrazce jsou pro kanál vyžadovány. Pro náš inspektor zpráv podporujeme jakýkoliv tvar, který podporuje vrstva níže (například pokud je možné, že vrstva níže může sestavovat <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, a také zveřejňuje <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Továrna kanálu a továrna naslouchacího procesu  
 Dalším krokem při psaní vlastního vrstveného kanálu je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro klientské kanály a <xref:System.ServiceModel.Channels.IChannelListener> pro kanály služby.  
  
 Tyto třídy přebírají interní továrnu a naslouchací proces a deleguje všechny kromě `OnCreateChannel` a `OnAcceptChannel` volání interní továrny a naslouchacího procesu.  
  
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
  
## <a name="adding-a-binding-element"></a>Přidání elementu vazby  
 Ukázka definuje vlastní element vazby: `InterceptingBindingElement`. `InterceptingBindingElement` přebírá `ChannelMessageInterceptor` jako vstup a používá tento `ChannelMessageInterceptor` k manipulaci se zprávami, které projde. Toto je jediná třída, která musí být veřejná. Továrny, naslouchací proces a kanály můžou být interními implementacemi pro veřejná rozhraní za běhu.  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 Pro integraci s konfigurací vazby knihovna definuje obslužnou rutinu konfiguračního oddílu jako rozšíření elementu vazby. Konfigurační soubory klienta a serveru musí registrovat rozšíření elementu vazby s konfiguračním systémem. Implementátori, kteří chtějí zveřejnit svůj element vazby do konfiguračního systému, lze odvodit z této třídy.  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement 
{ 
    //... 
}
```  
  
## <a name="adding-policy"></a>Přidávání zásad  
 Pro integraci s naším systémem zásad `InterceptingBindingElement` implementuje IPolicyExportExtension k signalizaci, že by se měl zúčastnit generování zásad. Pro podporu importu zásad na vygenerovaného klienta může uživatel zaregistrovat odvozenou třídu `InterceptingBindingElementImporter` a přepsat `CreateMessageInterceptor`() pro vygenerování své třídy `ChannelMessageInterceptor` s povolenými zásadami.  
  
## <a name="example-droppable-message-inspector"></a>Příklad: Droppable Message Inspector  
 Součástí ukázky je příklad implementace `ChannelMessageInspector`, která vyřazuje zprávy.  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 K němu můžete přistupovat z konfigurace následujícím způsobem:  
  
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
  
 Klient a server používají tento nově vytvořený konfigurační oddíl k vložení vlastních továren do nejnižší úrovně jejich zásobníků kanálů za běhu (nad úroveň transportu).  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 Klient nástroje používá knihovnu `MessageInterceptor` k přidání vlastní hlavičky k sudému číslování zpráv. Služba na druhé straně používá knihovnu `MessageInterceptor` k vyřazení všech zpráv, které nemají toto speciální hlavičku.  
  
 Po spuštění služby a poté klientovi by se měl zobrazit následující výstup klienta.  
  
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
  
 Klient oznamuje službě 10 různých rychlostí větru, ale pouze ty, které jsou ve stejném záhlaví, pouze se speciální hlavičkou.  
  
 Ve službě by se měl zobrazit následující výstup:  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Nejprve spusťte Service. exe a spusťte soubor Client. exe a Sledujte výstup okna konzoly.  
