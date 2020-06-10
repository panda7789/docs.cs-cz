---
title: 'Vzory návrhu: Vzor publikování–odběr založený na seznamu'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 5aaea5b0def544f8b3e963d71e269592b9b40784
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592343"
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Vzory návrhu: Vzor publikování–odběr založený na seznamu
Tato ukázka znázorňuje vzor pro publikování a odběr založený na seznamu, který je implementovaný jako program Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Vzor návrhu pro publikování a odběr založený na seznamu je popsaný v tématu publikace Microsoft Patterns & Practices – [vzory pro integraci](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)). Vzor publikování a odběru předává informace do kolekce příjemců, kteří se přihlásili k odběru informačního tématu. Publikování na základě seznamu – odběr uchovává seznam předplatitelů. Pokud jsou k dispozici informace, které je potřeba sdílet, pošle se každému odběrateli v seznamu kopie. Tato ukázka předvádí dynamický vzor pro publikování a odběr založený na seznamu, ve kterém se klienti můžou přihlásit k odběru nebo odhlásit, jak často potřebujete.  
  
 Ukázka publikovat a odběr založený na seznamu se skládá z klienta, služby a programu zdroje dat. Může existovat více než jeden klient a je spuštěn více než jeden program zdroje dat. Klienti se přihlásí k odběru služby, dostanou oznámení a zruší odběr. Programy zdroje dat odesílají informace službě, aby se sdílely se všemi aktuálními předplatiteli.  
  
 V této ukázce klient a zdroj dat jsou programy konzoly (soubory. exe) a služba je knihovna (. dll) hostovaná ve službě Internetová informační služba (IIS). Aktivita klient a zdroj dat se zobrazuje na ploše.  
  
 Služba používá duplexní komunikaci. `ISampleContract`Kontrakt služby se spáruje se `ISampleClientCallback` smlouvou zpětného volání. Služba implementuje operace odběru a zrušení odběru služby, které klienti používají pro připojení k seznamu předplatitelů nebo jejich opuštění. Služba také implementuje `PublishPriceChange` operaci služby, kterou program zdroje dat volá k poskytování služby novým informacím. Klientský program implementuje `PriceChange` operaci služby, kterou služba volá, aby upozornila všechny předplatitele změny ceny.  
  
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
  
 Služba používá událost .NET Framework jako mechanismus pro informování všech předplatitelů o nových informacích. Když klient připojí službu voláním odběru, poskytne obslužnou rutinu události. Když klient opustí, zruší odběr své obslužné rutiny události od události. Když zdroj dat volá službu, aby nahlásila změnu ceny, služba událost vyvolá. Tato akce volá každou instanci služby, jednu pro každého klienta, který má předplatné, a způsobí, že se obslužné rutiny událostí spustí. Každá obslužná rutina události do svého klienta předává informace prostřednictvím funkce zpětného volání.  
  
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
  
 Po spuštění ukázky spusťte několik klientů. Klienti se přihlásí k odběru služby. Pak spusťte program zdroje dat, který odesílá informace službě. Služba předá tyto informace všem předplatitelům. V každé konzole klienta můžete zobrazit aktivitu s potvrzením, že informace byly přijaty. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
### <a name="to-set-up-and-build-the-sample"></a>Nastavení a sestavení ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky na stejném počítači  
  
1. Otestujte, zda ke službě můžete přistupovat pomocí prohlížeče zadáním následující adresy: `http://localhost/servicemodelsamples/service.svc` . V odpovědi by se měla zobrazit Stránka s potvrzením.  
  
2. Spusťte soubor Client. exe z \client\bin \\ ze složky specifické pro jazyk. Aktivita klienta se zobrazí v okně konzoly klienta. Spusťte několik klientů.  
  
3. Spusťte DataSource. exe z \datasource\bin \\ ze složky specifické pro jazyk. Aktivita zdroj dat se zobrazí v okně konzoly. Jakmile zdroj dat odešle službě informace, měla by být předána každému klientovi.  
  
4. Pokud klient, zdroj dat a programy nemůžou komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Spuštění ukázky napříč počítači  
  
1. Nastavte počítač služby:  
  
    1. Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples. Dávkový soubor Setupvroot. bat se dá použít k vytvoření adresáře disku a virtuálního adresáře z [procesu jednorázového nastavení pro ukázky Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md) .  
  
    2. Zkopírujte programové soubory služby z%SystemDrive%\Inetpub\wwwroot\servicemodelsamples do virtuálního adresáře ServiceModelSamples na počítači služby. Nezapomeňte zahrnout soubory do adresáře \Bin.  
  
    3. Otestujte, zda ke službě můžete přistupovat z klientského počítače pomocí prohlížeče.  
  
2. Nastavení klientských počítačů:  
  
    1. Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce pro konkrétní jazyk do klientských počítačů.  
  
    2. V každém konfiguračním souboru klienta změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.  
  
3. Nastavte počítač zdroje dat:  
  
    1. Zkopírujte soubory programu zdroje dat ze složky \datasource\bin\ ve složce specifické pro daný jazyk do počítače zdroje dat.  
  
    2. V konfiguračním souboru zdroje dat změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.  
  
4. Na klientských počítačích spusťte soubor Client. exe z příkazového řádku.  
  
5. Na počítači zdroje dat spusťte soubor DataSource. exe z příkazového řádku.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
