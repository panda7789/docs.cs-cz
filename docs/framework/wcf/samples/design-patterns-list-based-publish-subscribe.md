---
title: "Vzory návrhu: Na základě seznamu publikování a odběru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9f3f5b9f8b07083c46ad98ce6e8ab6b5d3242e05
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Vzory návrhu: Na základě seznamu publikování a odběru
Tato ukázka znázorňuje implementovaný jako vzor na základě seznamu publikování a odběru [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] program.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Návrhový vzor na základě seznamu publikování a odběru je popsaný v publikaci postupy společnosti Microsoft Patterns [integrace vzory](http://go.microsoft.com/fwlink/?LinkId=95894). Vzor publikování a odběru předává informace na kolekci uživatelů, kteří odebírají tématu informace. Na základě seznamu publikování a odběru udržuje seznam odběratele. Když je sdílet informace, kopie posílá odběratel v seznamu. Tento příklad znázorňuje dynamický na základě seznamu publikování a odběru vzor, kde mohou klienti přihlášení k odběru nebo odhlášení podle potřeby.  
  
 Ukázka na základě seznamu publikování a odběru se skládá z klienta, služby a zdrojový program data. Může být více než jednoho klienta a víc dat zdrojový program spuštěn. Klienti objednat předplatné služby, dostávat oznámení a odhlášení. Data zdrojové programy poslat informace o službu, kterou chcete sdílet s všechny aktuální odběratele.  
  
 V tomto zdroji ukázka, klient a data jsou programy konzoly (soubory .exe) a služba je knihovna (DLL) hostované v Internetové informační služby (IIS). Zdrojová aktivita klienta a data jsou viditelné na ploše.  
  
 Služba používá duplexní komunikace. `ISampleContract` Kontrakt služby je spárován s `ISampleClientCallback` kontrakt zpětného volání. Služba se implementuje přihlásit k odběru a Unsubscribe operacemi služby, které klienti používají k připojení nebo nechte seznamu odběratelů. Služba také implementuje `PublishPriceChange` operace služby, které data zdrojový program zavolá poskytnout službu se novými informacemi. Implementuje klientskou aplikaci `PriceChange` operace služby, které služba zavolá upozornit všechny odběratele změna ceny.  
  
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
  
 Služba používá rozhraní .NET Framework událostí jako mechanismus k informování o nové informace o všech odběratelů. Když se klient připojuje pomocí volání přihlásit k odběru služby, poskytuje obslužné rutiny události. Když klient opustí, odhlášení odběrů její obslužnou rutinu události z události. Pokud zdroj dat zavolá službu nahlásit změnu ceny, služba vyvolává událost. Volá každá instance služby, jednu pro každého klienta, který se připojila a způsobí, že jejich obslužné rutiny událostí k provedení. Každý obslužná rutina události předává informace svého klienta přes jeho funkce zpětného volání.  
  
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
        //The previous price change event handler is deregistered.  
  
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
  
 Když spustíte ukázku, spusťte několik klientů. Klienti objednat předplatné služby. Spusťte program zdroje dat, který odesílá informace do služby. Služba předává na informacích všechny odběratele. Můžete zobrazit činnosti na každého klienta konzoly potvrzení, přijímání informace. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
### <a name="to-set-up-and-build-the-sample"></a>Jak nastavit a sestavit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky na stejném počítači  
  
1.  Test, že mají přístup ke službě pomocí prohlížeče tak, že zadáte tuto adresu: http://localhost/servicemodelsamples/service.svc. Potvrzovací stránku má být zobrazena v odpovědi.  
  
2.  Spusťte Client.exe z \client\bin\\, získáte složky pro konkrétní jazyk. Činnost klienta se zobrazí v okně konzoly klienta. Spusťte několik klientů.  
  
3.  Spusťte Datasource.exe z \datasource\bin\\, získáte složky pro konkrétní jazyk. Data zdrojové aktivity se zobrazí v okně konzoly. Jakmile zdroj dat odesílá informace o službě, je by měla být předána každého klienta.  
  
4.  Pokud klient, zdroj dat a programy služby nejsou komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-machines"></a>Ke spuštění ukázky mezi počítači  
  
1.  Nastavte počítač služby:  
  
    1.  Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples. Dávkového souboru Setupvroot.bat z [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) slouží k vytvoření adresáře disk a virtuální adresář.  
  
    2.  Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do ServiceModelSamples virtuálního adresáře na počítači služby. Nezapomeňte zahrnout soubory v adresáři \bin.  
  
    3.  Test službě můžete dostat z klientského počítače pomocí prohlížeče.  
  
2.  Nastavte klientské počítače:  
  
    1.  Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce pro specifický jazyk, pro klientské počítače.  
  
    2.  V konfiguračním souboru každého klienta změňte hodnotu adresu definice koncového bodu tak, aby odpovídala nové adresy vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
3.  Nastavte počítač zdroje dat:  
  
    1.  Zkopírujte soubory programu zdroje dat ve složce \datasource\bin\ ve složce pro specifický jazyk ke zdrojovému počítači data.  
  
    2.  V souboru konfigurace zdroje dat změňte hodnotu adresu definice koncového bodu tak, aby odpovídala nové adresy vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
4.  Na klientské počítače spusťte z příkazového řádku Client.exe.  
  
5.  Na zdrojovém počítači dat spusťte z příkazového řádku Datasource.exe.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
  
## <a name="see-also"></a>Viz také
