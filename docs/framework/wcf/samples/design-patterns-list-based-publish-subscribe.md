---
title: 'Vzory návrhu: Vzor publikování–odběr založený na seznamu'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 1b99908c1b83bb0d75e295b7a12e8c5933fe86a1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650123"
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Vzory návrhu: Vzor publikování–odběr založený na seznamu
Tento příklad znázorňuje vzor založený na seznamu publikování a odběru implementovaná jako program Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Návrhový vzor založený na seznamu publikování a odběru je popsán v publikaci Microsoft Patterns a postupy [vzory integrace](https://go.microsoft.com/fwlink/?LinkId=95894). Model publikování a odběru předává informace do kolekce příjemců, kteří se přihlásili k odběru tématu informace. Na základě seznamu publikování a odběru udržuje seznam předplatitelů. Po informace sdílet kopii posílá každému odběrateli v seznamu. V této ukázce dynamické na základě seznamu vzorec, kde můžou klienti přihlášení k odběru nebo odběr tak často, podle potřeby publikování a odběru.  
  
 Ukázka založený na seznamu publikování a odběru se skládá z klienta, služby a data zdrojového programu. Může existovat více než jednoho klienta a s více než jeden data zdrojového programu. Klienti předplatné ke službě, dostávat oznámení a odhlášení odběru. Programy pro zdroj dat odeslat informace o službě a sdílené s všichni aktuální předplatitelé.  
  
 V tomto zdroji ukázka, klient a data jsou programy konzoly (soubory .exe) a služba je knihovna (.dll) hostované v Internetové informační služby (IIS). Zdrojová aktivita klienta a data jsou viditelné v klientských počítačích.  
  
 Služba používá duplexní komunikaci. `ISampleContract` Kontrakt služby s oblastí `ISampleClientCallback` kontrakt zpětného volání. Služba implementuje přihlásit k odběru a zrušení odběru operace služby, které klienti používají k připojení nebo ponechte seznam předplatitelů. Služba také implementuje `PublishPriceChange` operace služby, která volá program zdroje dat k poskytování služby novými informacemi. Implementuje klientskou aplikaci `PriceChange` operace služby, která volá službu oznámit všichni předplatitelé změna ceny.  
  
```  
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
  
 Služba události rozhraní .NET Framework používá jako mechanismus k informování všichni předplatitelé o nové informace. Když se klient připojuje služby podle volání přihlásit k odběru, poskytuje obslužné rutiny události. Když klient opustí, zrušení odběru své obslužné rutině události z události. Když zdroji dat volá Služba hlášení změna ceny, službu vyvolává událost. Volá se každá instance služby, jednu pro každého klienta, která se připojila a způsobí, že jejich obslužných rutin událostí k provedení. Každá obslužná rutina události předá informace o jeho klienta pomocí funkce zpětného volání.  
  
```  
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
  
 Při spuštění ukázku spusťte několik klientů. Klienti přihlásit ke službě. Spusťte program zdroje dat, který odesílá informace do služby. Služba předá informace všichni předplatitelé. Zobrazit aktivitu na každého klienta konzoly potvrzení, přijímání informace. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
### <a name="to-set-up-and-build-the-sample"></a>K nastavení a sestavit ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky ve stejném počítači  
  
1. Test, můžete přístup ke službě pomocí prohlížeče zadáním následující adresy: `http://localhost/servicemodelsamples/service.svc`. Stránka s potvrzením má být zobrazena v odpovědi.  
  
2. Spustit Client.exe z \client\bin\\, ze složky specifické pro jazyk. Činnost klienta se zobrazí v okně konzoly klienta. Spuštění několika klienty.  
  
3. Spustit Datasource.exe z \datasource\bin\\, ze složky specifické pro jazyk. Aktivita zdroje dat se zobrazí v okně konzoly. Jakmile se zdroje dat se odesílá informace do služby, jeho by měly být předány každého klienta.  
  
4. Pokud klient, zdroj dat a aplikací služby nejsou schopné komunikovat, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Ke spuštění ukázky v počítačích  
  
1. Nastavení služby počítače:  
  
    1. Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples. Soubor Setupvroot.bat ze služby batch [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) je možné vytvořit na disku a virtuální adresář.  
  
    2. Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do ServiceModelSamples virtuálního adresáře na počítači služby. Nezapomeňte zahrnout soubory v adresáři \bin.  
  
    3. Testovací službě můžete dostat z klientského počítače pomocí prohlížeče.  
  
2. Nastavte klientské počítače:  
  
    1. Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientských počítačů.  
  
    2. V konfiguračním souboru každý klient změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adresu služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
3. Nastavte počítač pro zdroj dat:  
  
    1. Zkopírujte soubory programu zdroje dat ze složky \datasource\bin\ v rámci složky specifické pro jazyk, na počítač pro datové zdroje.  
  
    2. V souboru konfigurace zdroje dat změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adresu služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
4. Na klientské počítače spusťte z příkazového řádku Client.exe.  
  
5. Na zdrojovém počítači data spusťte z příkazového řádku Datasource.exe.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
