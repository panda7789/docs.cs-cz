---
title: Vlastní zachycování zpráv
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 0ed34823251dcc010fc438bda1e746549b97f0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="custom-message-interceptor"></a>Vlastní zachycování zpráv
Tento příklad znázorňuje použití model rozšiřitelnosti kanálu. Konkrétně ukazuje, jak implementovat vlastní vazby element, který vytváří objekty factory kanálu a naslouchací procesy kanál zachytávat všechny příchozí a odchozí zprávy na určitém místě v zásobníku spuštění. Ukázka zahrnuje také klienta a serveru, která ukazují použití tyto vlastní objekty pro vytváření.  
  
 V této ukázce klienta a služby jsou programy konzoly (.exe). Klient a služba i použití běžné knihovny (DLL.dll), která obsahuje element vlastní vazby a jejích přidružených objektů běhu.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 Ukázka popisuje doporučený postup pro vytvoření vlastní vrstveného kanál ve Windows Communication Foundation (WCF), pomocí rozhraní kanálu a následující [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] osvědčené postupy. Postup vytvoření vlastní vrstveného kanál jsou následující:  
  
1.  Rozhodnete, které tvarů kanál bude podporovat kanálu a naslouchací proces kanálu.  
  
2.  Vytvoření postupu kanálu a kanál naslouchací proces, který podporují obrazců kanálu.  
  
3.  Přidáte element vazby, který přidá do kanálu zásobníku vlastním vrstveného kanálu.  
  
4.  Přidáte oddíl rozšíření element vazby ke zveřejnění nového elementu vazby v konfiguraci systému.  
  
## <a name="channel-shapes"></a>Kanál tvarů  
 Prvním krokem při psaní vlastních vrstveného kanál je rozhodněte, které obrazce jsou nutné pro kanál. Pro naše inspector zpráva podporujeme jakýkoli tvar, který podporuje vrstvu pod nám (například v případě, že můžete vytvořit vrstvu pod nám <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, pak taky zveřejňujeme <xref:System.ServiceModel.Channels.IOutputChannel> a <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).  
  
## <a name="channel-factory-and-listener-factory"></a>Postup kanálu a objektu pro vytváření naslouchací proces  
 Dalším krokem při psaní vlastních vrstveného kanál je vytvoření implementace <xref:System.ServiceModel.Channels.IChannelFactory> pro kanály klienta a z <xref:System.ServiceModel.Channels.IChannelListener> pro kanály služby.  
  
 Tyto třídy vnitřní objekt pro vytváření a naslouchací proces a delegovat všechny ale na `OnCreateChannel` a `OnAcceptChannel` volání vnitřní objekt pro vytváření a naslouchací proces.  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a>Přidání prvku vazby  
 Ukázka definuje element vlastní vazby: `InterceptingBindingElement`. `InterceptingBindingElement` trvá `ChannelMessageInterceptor` jako vstup a to pomocí `ChannelMessageInterceptor` k manipulaci s zprávy, které předáte ji. Toto je jediná třída, která musí být veřejné. Objekt pro vytváření, naslouchací proces a kanály mohou být interních implementací veřejné rozhraní běhu.  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a>Přidání podpory konfigurace  
 K integraci s Konfigurace vazeb, knihovny definuje obslužnou rutinu oddílu konfigurace jako oddíl rozšíření element vazby. Konfigurační soubory, které klient a server musí registraci rozšíření elementu vazby v konfiguraci systému. Implementátory informačních technologií, které chcete zpřístupnit jejich prvku vazby do konfiguračního systému lze odvozovat z této třídy.  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a>Přidání zásady  
 K integraci s naše systému zásad `InterceptingBindingElement` implementuje IPolicyExportExtension signál, že jsme by se měly podílet generování zásad. Pro podporu Import zásady generovaného klienta, můžete uživatele zaregistrovat třídu odvozenou z `InterceptingBindingElementImporter` a přepsat `CreateMessageInterceptor`() k vygenerování jejich zásady povoleným `ChannelMessageInterceptor` třídy.  
  
## <a name="example-droppable-message-inspector"></a>Příklad: Droppable zpráva Inspector  
 Příklad implementace je zahrnuta v ukázce `ChannelMessageInspector` který zahodí zprávy.  
  
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
  
 Klient a server použít tento nově vytvořený konfigurační oddíl vložení vlastní objekty Factory do jejich spuštění kanálu zásobníky (nad transportní) nejnižší úroveň.  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 Klient použije `MessageInterceptor` knihovny a přidat vlastní hlavičku do i číslované zprávy. Služba na druhé straně používá `MessageInterceptor` knihovny vyřaďte všechny zprávy, které nemají speciální hlavičku.  
  
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
  
 Klient sestavy 10 rychlosti větru jiné službě, ale pouze polovinu je speciální hlavičky značky.  
  
 Ve službě byste měli vidět následující výstup:  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Nejprve spusťte Service.exe potom spustit Client.exe a podívejte se na obě okna konzoly pro výstup.  
  
## <a name="see-also"></a>Viz také
