---
title: 'Vzory návrhu: Na základě seznamu publikování a odběru'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a4f36c7231146811e4eb033cfb6a3433a58dbb2
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="9a52b-102">Vzory návrhu: Na základě seznamu publikování a odběru</span><span class="sxs-lookup"><span data-stu-id="9a52b-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="9a52b-103">Tato ukázka znázorňuje implementovaný jako vzor na základě seznamu publikování a odběru [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="9a52b-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a52b-104">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9a52b-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9a52b-105">Návrhový vzor na základě seznamu publikování a odběru je popsaný v publikaci postupy společnosti Microsoft Patterns [integrace vzory](http://go.microsoft.com/fwlink/?LinkId=95894).</span><span class="sxs-lookup"><span data-stu-id="9a52b-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](http://go.microsoft.com/fwlink/?LinkId=95894).</span></span> <span data-ttu-id="9a52b-106">Vzor publikování a odběru předává informace na kolekci uživatelů, kteří odebírají tématu informace.</span><span class="sxs-lookup"><span data-stu-id="9a52b-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="9a52b-107">Na základě seznamu publikování a odběru udržuje seznam odběratele.</span><span class="sxs-lookup"><span data-stu-id="9a52b-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="9a52b-108">Když je sdílet informace, kopie posílá odběratel v seznamu.</span><span class="sxs-lookup"><span data-stu-id="9a52b-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="9a52b-109">Tento příklad znázorňuje dynamický na základě seznamu publikování a odběru vzor, kde mohou klienti přihlášení k odběru nebo odhlášení podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="9a52b-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="9a52b-110">Ukázka na základě seznamu publikování a odběru se skládá z klienta, služby a zdrojový program data.</span><span class="sxs-lookup"><span data-stu-id="9a52b-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="9a52b-111">Může být více než jednoho klienta a víc dat zdrojový program spuštěn.</span><span class="sxs-lookup"><span data-stu-id="9a52b-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="9a52b-112">Klienti objednat předplatné služby, dostávat oznámení a odhlášení.</span><span class="sxs-lookup"><span data-stu-id="9a52b-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="9a52b-113">Data zdrojové programy poslat informace o službu, kterou chcete sdílet s všechny aktuální odběratele.</span><span class="sxs-lookup"><span data-stu-id="9a52b-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="9a52b-114">V tomto zdroji ukázka, klient a data jsou programy konzoly (soubory .exe) a služba je knihovna (DLL) hostované v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="9a52b-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="9a52b-115">Zdrojová aktivita klienta a data jsou viditelné na ploše.</span><span class="sxs-lookup"><span data-stu-id="9a52b-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="9a52b-116">Služba používá duplexní komunikace.</span><span class="sxs-lookup"><span data-stu-id="9a52b-116">The service uses duplex communication.</span></span> <span data-ttu-id="9a52b-117">`ISampleContract` Kontrakt služby je spárován s `ISampleClientCallback` kontrakt zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9a52b-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="9a52b-118">Služba se implementuje přihlásit k odběru a Unsubscribe operacemi služby, které klienti používají k připojení nebo nechte seznamu odběratelů.</span><span class="sxs-lookup"><span data-stu-id="9a52b-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="9a52b-119">Služba také implementuje `PublishPriceChange` operace služby, které data zdrojový program zavolá poskytnout službu se novými informacemi.</span><span class="sxs-lookup"><span data-stu-id="9a52b-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="9a52b-120">Implementuje klientskou aplikaci `PriceChange` operace služby, které služba zavolá upozornit všechny odběratele změna ceny.</span><span class="sxs-lookup"><span data-stu-id="9a52b-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
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
  
 <span data-ttu-id="9a52b-121">Služba používá rozhraní .NET Framework událostí jako mechanismus k informování o nové informace o všech odběratelů.</span><span class="sxs-lookup"><span data-stu-id="9a52b-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="9a52b-122">Když se klient připojuje pomocí volání přihlásit k odběru služby, poskytuje obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="9a52b-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="9a52b-123">Když klient opustí, odhlášení odběrů její obslužnou rutinu události z události.</span><span class="sxs-lookup"><span data-stu-id="9a52b-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="9a52b-124">Pokud zdroj dat zavolá službu nahlásit změnu ceny, služba vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="9a52b-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="9a52b-125">Volá každá instance služby, jednu pro každého klienta, který se připojila a způsobí, že jejich obslužné rutiny událostí k provedení.</span><span class="sxs-lookup"><span data-stu-id="9a52b-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="9a52b-126">Každý obslužná rutina události předává informace svého klienta přes jeho funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9a52b-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
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
  
 <span data-ttu-id="9a52b-127">Když spustíte ukázku, spusťte několik klientů.</span><span class="sxs-lookup"><span data-stu-id="9a52b-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="9a52b-128">Klienti objednat předplatné služby.</span><span class="sxs-lookup"><span data-stu-id="9a52b-128">The clients subscribe to the service.</span></span> <span data-ttu-id="9a52b-129">Spusťte program zdroje dat, který odesílá informace do služby.</span><span class="sxs-lookup"><span data-stu-id="9a52b-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="9a52b-130">Služba předává na informacích všechny odběratele.</span><span class="sxs-lookup"><span data-stu-id="9a52b-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="9a52b-131">Můžete zobrazit činnosti na každého klienta konzoly potvrzení, přijímání informace.</span><span class="sxs-lookup"><span data-stu-id="9a52b-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="9a52b-132">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="9a52b-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="9a52b-133">Jak nastavit a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="9a52b-133">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="9a52b-134">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9a52b-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9a52b-135">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9a52b-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="9a52b-136">Ke spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="9a52b-136">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="9a52b-137">Test, že mají přístup ke službě pomocí prohlížeče tak, že zadáte tuto adresu: http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="9a52b-137">Test that you can access the service using a browser by entering the following address: http://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="9a52b-138">Potvrzovací stránku má být zobrazena v odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9a52b-138">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="9a52b-139">Spusťte Client.exe z \client\bin\\, získáte složky pro konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="9a52b-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="9a52b-140">Činnost klienta se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="9a52b-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="9a52b-141">Spusťte několik klientů.</span><span class="sxs-lookup"><span data-stu-id="9a52b-141">Launch several clients.</span></span>  
  
3.  <span data-ttu-id="9a52b-142">Spusťte Datasource.exe z \datasource\bin\\, získáte složky pro konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="9a52b-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="9a52b-143">Data zdrojové aktivity se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="9a52b-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="9a52b-144">Jakmile zdroj dat odesílá informace o službě, je by měla být předána každého klienta.</span><span class="sxs-lookup"><span data-stu-id="9a52b-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4.  <span data-ttu-id="9a52b-145">Pokud klient, zdroj dat a programy služby nejsou komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="9a52b-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="9a52b-146">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="9a52b-146">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="9a52b-147">Nastavte počítač služby:</span><span class="sxs-lookup"><span data-stu-id="9a52b-147">Set up the service machine:</span></span>  
  
    1.  <span data-ttu-id="9a52b-148">Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="9a52b-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="9a52b-149">Dávkového souboru Setupvroot.bat z [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) slouží k vytvoření adresáře disk a virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9a52b-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2.  <span data-ttu-id="9a52b-150">Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do ServiceModelSamples virtuálního adresáře na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="9a52b-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="9a52b-151">Nezapomeňte zahrnout soubory v adresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="9a52b-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3.  <span data-ttu-id="9a52b-152">Test službě můžete dostat z klientského počítače pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="9a52b-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2.  <span data-ttu-id="9a52b-153">Nastavte klientské počítače:</span><span class="sxs-lookup"><span data-stu-id="9a52b-153">Set up the client machines:</span></span>  
  
    1.  <span data-ttu-id="9a52b-154">Zkopírujte soubory programu klienta ve složce \client\bin\ ve složce pro specifický jazyk, pro klientské počítače.</span><span class="sxs-lookup"><span data-stu-id="9a52b-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2.  <span data-ttu-id="9a52b-155">V konfiguračním souboru každého klienta změňte hodnotu adresu definice koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="9a52b-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="9a52b-156">Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="9a52b-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3.  <span data-ttu-id="9a52b-157">Nastavte počítač zdroje dat:</span><span class="sxs-lookup"><span data-stu-id="9a52b-157">Set up the data source machine:</span></span>  
  
    1.  <span data-ttu-id="9a52b-158">Zkopírujte soubory programu zdroje dat ve složce \datasource\bin\ ve složce pro specifický jazyk ke zdrojovému počítači data.</span><span class="sxs-lookup"><span data-stu-id="9a52b-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2.  <span data-ttu-id="9a52b-159">V souboru konfigurace zdroje dat změňte hodnotu adresu definice koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="9a52b-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="9a52b-160">Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="9a52b-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4.  <span data-ttu-id="9a52b-161">Na klientské počítače spusťte z příkazového řádku Client.exe.</span><span class="sxs-lookup"><span data-stu-id="9a52b-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="9a52b-162">Na zdrojovém počítači dat spusťte z příkazového řádku Datasource.exe.</span><span class="sxs-lookup"><span data-stu-id="9a52b-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9a52b-163">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="9a52b-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9a52b-164">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9a52b-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9a52b-165">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9a52b-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9a52b-166">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9a52b-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
  
## <a name="see-also"></a><span data-ttu-id="9a52b-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a52b-167">See Also</span></span>
