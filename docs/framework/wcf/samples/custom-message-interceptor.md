---
title: Vlastní zachycování zpráv
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: d585e60c9b31e56873b0501425f55541bd647e02
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344270"
---
# <a name="custom-message-interceptor"></a>Vlastní zachycování zpráv
Tento příklad ukazuje použití model rozšiřitelnosti kanálu. Konkrétně se ukazuje, jak implementovat vlastní prvek vazby, která vytváří objekty pro vytváření kanálů a moduly pro naslouchání kanálů aby se zachytily všechny příchozí a odchozí zprávy v určitém místě v zásobníku za běhu. Ukázka zahrnuje také klienta a serveru, které ukazují použití tyto vlastní objekty pro vytváření.  
  
 V této ukázce jsou klient a služba konzoly programů (.exe). Klient a služba, ujistěte se, jak použít společné knihovny (DLL), který obsahuje element vlastní vazby a jejích přidružených objektů za běhu.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 Ukázka popisuje doporučený postup pro vytváření vlastních vrstev kanálu ve Windows Communication Foundation (WCF), pomocí architektura kanálů a osvědčených postupů WCF. Postup vytvoření vlastního kanálu vrstvami jsou následující:  
  
1. Rozhodněte, které z tvarů kanálu objekt pro vytváření kanálů a modul pro naslouchání kanálu se podporují.  
  
2. Vytvořte objekt pro vytváření kanálů a naslouchací proces kanálu, které podporují obrazcích kanálu.  
  
3. Přidejte prvek vazby, který přidá vlastní vrstvami kanál do zásobníku kanálu.  
  
4. Přidání sekce rozšíření elementu vazby vystavit nový element vazby na konfigurační systém.  
  
## <a name="channel-shapes"></a>Kanál obrazce  
 Prvním krokem při psaní vlastního kanálu vrstvami je rozhodnout, jaké tvary jsou požadovány pro kanál. Pro naše inspektoru zpráva podporujeme žádný obrazec, který podporuje vrstvy pod nám (například pokud vrstvy pod nám můžete vytvářet <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, pak také zveřejňujeme <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Objekt pro vytváření kanálů a Výroba naslouchací služby  
 Dalším krokem při psaní vlastního kanálu vrstvami je vytvořte implementaci třídy <xref:System.ServiceModel.Channels.IChannelFactory> pro kanály klientů a jejich <xref:System.ServiceModel.Channels.IChannelListener> pro kanály service.  
  
 Tyto třídy vnitřní objekt pro vytváření a naslouchací proces a delegovat vše kromě na `OnCreateChannel` a `OnAcceptChannel` volání vnitřní objekt pro vytváření a naslouchacího procesu.  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a>Přidání elementu vazby  
 Ukázka definuje vlastní prvek vazby: `InterceptingBindingElement`. `InterceptingBindingElement` přijímá `ChannelMessageInterceptor` jako vstup a využívá ji `ChannelMessageInterceptor` k manipulaci s zprávy předávané přes něj. Toto je pouze třídu, která musí být veřejné. Objekt pro vytváření, naslouchací proces a kanály můžou být interní implementace veřejné rozhraní za běhu.  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 K integraci s konfigurací vazby knihovny definuje obslužné rutiny konfiguračního oddílu jako část rozšíření elementu vazby. Konfiguračních souborů klienta a serveru musí registraci rozšíření elementu vazby v konfiguraci systému. Implementátory, které chcete je zveřejnit své element vazby na konfigurační systém lze odvodit z této třídy.  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a>Přidání zásad  
 Integrace s naší systému zásad `InterceptingBindingElement` implementuje IPolicyExportExtension signál, že jsme měli zúčastnit generování zásad. Podporu importu zásad na generovaného klienta, může uživatel zaregistrovat odvozenou třídu `InterceptingBindingElementImporter` a přepsat `CreateMessageInterceptor`() k vygenerování jejich zásady podporou `ChannelMessageInterceptor` třídy.  
  
## <a name="example-droppable-message-inspector"></a>Příklad: Inspektor droppable zprávy  
 Ukázka je příklad implementace `ChannelMessageInspector` které zahodí zprávy.  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 Můžete k němu přístup z konfigurace následujícím způsobem:  
  
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
  
 Klient a server použijte tento oddíl konfigurace nově vytvořený k vložení vlastní objekty Factory do svých zásobníků kanál za běhu (nad transportní) nejnižší úroveň.  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 Klient použije `MessageInterceptor` knihovny přidat vlastní hlavičku do i číslované zprávy. Služba používá na druhé straně `MessageInterceptor` knihovny vyřaďte všechny zprávy, které nemají toto zvláštní záhlaví.  
  
 Měli byste vidět následující výstup klienta po spuštění služby a potom klienta.  
  
```  
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
  
 Klient sestavy 10 rychlost větru jiné službě, ale pouze první z nich s hlavičkou speciální značek.  
  
 Ve službě byste měli vidět následující výstup:  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Nejprve spusťte Service.exe, pak spusťte Client.exe a podívejte se na obě okna konzoly pro výstup.  
