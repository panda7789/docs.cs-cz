---
title: 'Vzory návrhu: publikování–odběr založený na seznamu'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 7342b3702338d5cd1fcc27d80e4e70cee019cc22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144757"
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Vzory návrhu: publikování–odběr založený na seznamu
Tato ukázka ilustruje vzor publikování a odběru založený na seznamu implementovaný jako program WCF (Windows Communication Foundation).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Vzor návrhu publikování a odběru založený na seznamu je popsán v publikaci Microsoft Patterns & Practices, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)). Vzor Publikování a přihlášení k odběru předá informace kolekci příjemců, kteří se přihlásili k odběru informačního tématu. Odběr publikování na základě seznamu udržuje seznam odběratelů. Pokud jsou k dispozici informace ke sdílení, je kopie odeslána každému odběrateli v seznamu. Tato ukázka ukazuje dynamický seznam na základě publikování a odběru vzor, kde klienti mohou přihlásit nebo odhlásit tak často, jak je požadováno.  
  
 Ukázka publikování a odběru na základě seznamu se skládá z klienta, služby a programu zdroje dat. Může být spuštěno více než jeden klient a více než jeden program zdroje dat. Klienti se přihlásí ke službě, obdrží oznámení a odhlásí se z odběru. Programy pro zdroje dat odesílají informace do služby, která má být sdílena se všemi aktuálními odběrateli.  
  
 V této ukázce jsou klientem a zdrojem dat konzolové programy (soubory.exe) a služba je knihovna (.dll) hostovaná v Internetové informační službě (IIS). Aktivita klienta a zdroje dat jsou viditelné na ploše.  
  
 Služba používá duplexní komunikaci. Servisní `ISampleContract` smlouva je spárována `ISampleClientCallback` se smlouvou o zpětném volání. Služba implementuje operace služby Subscribe a Unsubscribe, které klienti používají k připojení nebo opuštění seznamu odběratelů. Služba také implementuje `PublishPriceChange` operaci služby, kterou program zdroje dat volá, aby službu poskytl nové informace. Klientský program implementuje `PriceChange` operaci služby, kterou služba volá, aby upozornila všechny předplatitele na změnu ceny.  
  
```csharp  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 Služba používá .NET Framework událost jako mechanismus informovat všechny předplatitele o nové informace. Když se klient připojí ke službě voláním Subscribe, poskytuje obslužnou rutinu události. Když klient opustí, odhlásí jeho obslužnou rutinu události z události. Když zdroj dat volá službu k hlášení změny ceny, služba vyvolá událost. To volá každou instanci služby, jeden pro každého klienta, který se přihlásil k odběru a způsobí, že jejich obslužné rutiny událostí ke spuštění. Každá obslužná rutina události předá informace svému klientovi prostřednictvím funkce zpětného volání.  
  
```csharp
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 Při spuštění ukázky spusťte několik klientů. Klienti se přihlásí ke službě. Potom spusťte program zdroje dat, který odesílá informace službě. Služba předává informace všem odběratelům. Na každé klientské konzole můžete zobrazit aktivitu potvrzující, že informace byly přijaty. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky ve stejném počítači  
  
1. Otestujte, zda máte přístup ke službě pomocí `http://localhost/servicemodelsamples/service.svc`prohlížeče zadáním následující adresy: . V reakci na to by měla být zobrazena stránka s potvrzením.  
  
2. Spusťte soubor Client.exe\\z \client\bin z pod složky specifické pro daný jazyk. Aktivita klienta se zobrazí v okně klientské konzole. Spusťte několik klientů.  
  
3. Spusťte soubor Datasource.exe\\z \datasource\bin z pod složky specifické pro daný jazyk. Aktivita zdroje dat se zobrazí v okně konzoly. Jakmile zdroj dat odešle informace do služby, by měly být předány každému klientovi.  
  
4. Pokud klient, zdroj dat a programy služeb nejsou schopny komunikovat, naleznete [v tématu Tipy pro řešení potíží s ukázkami WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Spuštění ukázky napříč počítači  
  
1. Nastavte servisní stroj:  
  
    1. Na servisním počítači vytvořte virtuální adresář s názvem ServiceModelSamples. Dávkový soubor Setupvroot.bat z [jednorázového postupu instalace ukázek služby Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) lze použít k vytvoření adresáře disku a virtuálního adresáře.  
  
    2. Zkopírujte soubory programů služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do virtuálního adresáře ServiceModelSamples v servisním počítači. Nezapomeňte zahrnout soubory do adresáře \bin.  
  
    3. Otestujte, že ke službě máte přístup z klientského počítače pomocí prohlížeče.  
  
2. Nastavení klientských počítačů:  
  
    1. Zkopírujte soubory klientských programů ze složky \client\bin\ ve složce specifické pro daný jazyk do klientských počítačů.  
  
    2. V každém konfiguračním souboru klienta změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.  
  
3. Nastavte počítač se zdrojem dat:  
  
    1. Zkopírujte soubory programů zdroje dat ze složky \datasource\bin\ ve složce specifické pro daný jazyk do počítače se zdrojem dat.  
  
    2. V konfiguračním souboru zdroje dat změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.  
  
4. Na klientských počítačích spusťte soubor Client.exe z příkazového řádku.  
  
5. V počítači se zdrojem dat spusťte datasource.exe z příkazového řádku.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
