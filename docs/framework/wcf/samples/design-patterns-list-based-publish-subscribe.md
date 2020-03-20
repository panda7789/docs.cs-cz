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
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="fd96f-102">Vzory návrhu: publikování–odběr založený na seznamu</span><span class="sxs-lookup"><span data-stu-id="fd96f-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="fd96f-103">Tato ukázka ilustruje vzor publikování a odběru založený na seznamu implementovaný jako program WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="fd96f-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd96f-104">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="fd96f-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fd96f-105">Vzor návrhu publikování a odběru založený na seznamu je popsán v publikaci Microsoft Patterns & Practices, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="fd96f-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="fd96f-106">Vzor Publikování a přihlášení k odběru předá informace kolekci příjemců, kteří se přihlásili k odběru informačního tématu.</span><span class="sxs-lookup"><span data-stu-id="fd96f-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="fd96f-107">Odběr publikování na základě seznamu udržuje seznam odběratelů.</span><span class="sxs-lookup"><span data-stu-id="fd96f-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="fd96f-108">Pokud jsou k dispozici informace ke sdílení, je kopie odeslána každému odběrateli v seznamu.</span><span class="sxs-lookup"><span data-stu-id="fd96f-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="fd96f-109">Tato ukázka ukazuje dynamický seznam na základě publikování a odběru vzor, kde klienti mohou přihlásit nebo odhlásit tak často, jak je požadováno.</span><span class="sxs-lookup"><span data-stu-id="fd96f-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="fd96f-110">Ukázka publikování a odběru na základě seznamu se skládá z klienta, služby a programu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="fd96f-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="fd96f-111">Může být spuštěno více než jeden klient a více než jeden program zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="fd96f-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="fd96f-112">Klienti se přihlásí ke službě, obdrží oznámení a odhlásí se z odběru.</span><span class="sxs-lookup"><span data-stu-id="fd96f-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="fd96f-113">Programy pro zdroje dat odesílají informace do služby, která má být sdílena se všemi aktuálními odběrateli.</span><span class="sxs-lookup"><span data-stu-id="fd96f-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="fd96f-114">V této ukázce jsou klientem a zdrojem dat konzolové programy (soubory.exe) a služba je knihovna (.dll) hostovaná v Internetové informační službě (IIS).</span><span class="sxs-lookup"><span data-stu-id="fd96f-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="fd96f-115">Aktivita klienta a zdroje dat jsou viditelné na ploše.</span><span class="sxs-lookup"><span data-stu-id="fd96f-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="fd96f-116">Služba používá duplexní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="fd96f-116">The service uses duplex communication.</span></span> <span data-ttu-id="fd96f-117">Servisní `ISampleContract` smlouva je spárována `ISampleClientCallback` se smlouvou o zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="fd96f-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="fd96f-118">Služba implementuje operace služby Subscribe a Unsubscribe, které klienti používají k připojení nebo opuštění seznamu odběratelů.</span><span class="sxs-lookup"><span data-stu-id="fd96f-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="fd96f-119">Služba také implementuje `PublishPriceChange` operaci služby, kterou program zdroje dat volá, aby službu poskytl nové informace.</span><span class="sxs-lookup"><span data-stu-id="fd96f-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="fd96f-120">Klientský program implementuje `PriceChange` operaci služby, kterou služba volá, aby upozornila všechny předplatitele na změnu ceny.</span><span class="sxs-lookup"><span data-stu-id="fd96f-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
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
  
 <span data-ttu-id="fd96f-121">Služba používá .NET Framework událost jako mechanismus informovat všechny předplatitele o nové informace.</span><span class="sxs-lookup"><span data-stu-id="fd96f-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="fd96f-122">Když se klient připojí ke službě voláním Subscribe, poskytuje obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="fd96f-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="fd96f-123">Když klient opustí, odhlásí jeho obslužnou rutinu události z události.</span><span class="sxs-lookup"><span data-stu-id="fd96f-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="fd96f-124">Když zdroj dat volá službu k hlášení změny ceny, služba vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="fd96f-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="fd96f-125">To volá každou instanci služby, jeden pro každého klienta, který se přihlásil k odběru a způsobí, že jejich obslužné rutiny událostí ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="fd96f-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="fd96f-126">Každá obslužná rutina události předá informace svému klientovi prostřednictvím funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="fd96f-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
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
  
 <span data-ttu-id="fd96f-127">Při spuštění ukázky spusťte několik klientů.</span><span class="sxs-lookup"><span data-stu-id="fd96f-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="fd96f-128">Klienti se přihlásí ke službě.</span><span class="sxs-lookup"><span data-stu-id="fd96f-128">The clients subscribe to the service.</span></span> <span data-ttu-id="fd96f-129">Potom spusťte program zdroje dat, který odesílá informace službě.</span><span class="sxs-lookup"><span data-stu-id="fd96f-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="fd96f-130">Služba předává informace všem odběratelům.</span><span class="sxs-lookup"><span data-stu-id="fd96f-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="fd96f-131">Na každé klientské konzole můžete zobrazit aktivitu potvrzující, že informace byly přijaty.</span><span class="sxs-lookup"><span data-stu-id="fd96f-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="fd96f-132">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="fd96f-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="fd96f-133">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="fd96f-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="fd96f-134">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fd96f-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fd96f-135">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fd96f-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="fd96f-136">Spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="fd96f-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="fd96f-137">Otestujte, zda máte přístup ke službě pomocí `http://localhost/servicemodelsamples/service.svc`prohlížeče zadáním následující adresy: .</span><span class="sxs-lookup"><span data-stu-id="fd96f-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="fd96f-138">V reakci na to by měla být zobrazena stránka s potvrzením.</span><span class="sxs-lookup"><span data-stu-id="fd96f-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="fd96f-139">Spusťte soubor Client.exe\\z \client\bin z pod složky specifické pro daný jazyk.</span><span class="sxs-lookup"><span data-stu-id="fd96f-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="fd96f-140">Aktivita klienta se zobrazí v okně klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="fd96f-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="fd96f-141">Spusťte několik klientů.</span><span class="sxs-lookup"><span data-stu-id="fd96f-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="fd96f-142">Spusťte soubor Datasource.exe\\z \datasource\bin z pod složky specifické pro daný jazyk.</span><span class="sxs-lookup"><span data-stu-id="fd96f-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="fd96f-143">Aktivita zdroje dat se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="fd96f-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="fd96f-144">Jakmile zdroj dat odešle informace do služby, by měly být předány každému klientovi.</span><span class="sxs-lookup"><span data-stu-id="fd96f-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="fd96f-145">Pokud klient, zdroj dat a programy služeb nejsou schopny komunikovat, naleznete [v tématu Tipy pro řešení potíží s ukázkami WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="fd96f-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="fd96f-146">Spuštění ukázky napříč počítači</span><span class="sxs-lookup"><span data-stu-id="fd96f-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="fd96f-147">Nastavte servisní stroj:</span><span class="sxs-lookup"><span data-stu-id="fd96f-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="fd96f-148">Na servisním počítači vytvořte virtuální adresář s názvem ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="fd96f-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="fd96f-149">Dávkový soubor Setupvroot.bat z [jednorázového postupu instalace ukázek služby Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) lze použít k vytvoření adresáře disku a virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="fd96f-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="fd96f-150">Zkopírujte soubory programů služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do virtuálního adresáře ServiceModelSamples v servisním počítači.</span><span class="sxs-lookup"><span data-stu-id="fd96f-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="fd96f-151">Nezapomeňte zahrnout soubory do adresáře \bin.</span><span class="sxs-lookup"><span data-stu-id="fd96f-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="fd96f-152">Otestujte, že ke službě máte přístup z klientského počítače pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="fd96f-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="fd96f-153">Nastavení klientských počítačů:</span><span class="sxs-lookup"><span data-stu-id="fd96f-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="fd96f-154">Zkopírujte soubory klientských programů ze složky \client\bin\ ve složce specifické pro daný jazyk do klientských počítačů.</span><span class="sxs-lookup"><span data-stu-id="fd96f-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="fd96f-155">V každém konfiguračním souboru klienta změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="fd96f-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="fd96f-156">Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="fd96f-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="fd96f-157">Nastavte počítač se zdrojem dat:</span><span class="sxs-lookup"><span data-stu-id="fd96f-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="fd96f-158">Zkopírujte soubory programů zdroje dat ze složky \datasource\bin\ ve složce specifické pro daný jazyk do počítače se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="fd96f-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="fd96f-159">V konfiguračním souboru zdroje dat změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="fd96f-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="fd96f-160">Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="fd96f-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="fd96f-161">Na klientských počítačích spusťte soubor Client.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="fd96f-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="fd96f-162">V počítači se zdrojem dat spusťte datasource.exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="fd96f-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fd96f-163">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="fd96f-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fd96f-164">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="fd96f-164">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fd96f-165">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="fd96f-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fd96f-166">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="fd96f-166">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
