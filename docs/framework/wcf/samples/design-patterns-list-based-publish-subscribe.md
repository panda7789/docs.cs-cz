---
title: 'Vzory návrhu: publikování a odběr založený na seznamu'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 831e6947c0919e8112627ff0a0697592f598561b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716344"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="e1f71-102">Vzory návrhu: publikování a odběr založený na seznamu</span><span class="sxs-lookup"><span data-stu-id="e1f71-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="e1f71-103">Tato ukázka znázorňuje vzor pro publikování a odběr založený na seznamu, který je implementovaný jako program Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e1f71-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1f71-104">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e1f71-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e1f71-105">Vzor návrhu pro publikování a odběr založený na seznamu je popsaný v tématu publikace Microsoft Patterns & Practices – [vzory pro integraci](https://go.microsoft.com/fwlink/?LinkId=95894).</span><span class="sxs-lookup"><span data-stu-id="e1f71-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://go.microsoft.com/fwlink/?LinkId=95894).</span></span> <span data-ttu-id="e1f71-106">Vzor publikování a odběru předává informace do kolekce příjemců, kteří se přihlásili k odběru informačního tématu.</span><span class="sxs-lookup"><span data-stu-id="e1f71-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="e1f71-107">Publikování na základě seznamu – odběr uchovává seznam předplatitelů.</span><span class="sxs-lookup"><span data-stu-id="e1f71-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="e1f71-108">Pokud jsou k dispozici informace, které je potřeba sdílet, pošle se každému odběrateli v seznamu kopie.</span><span class="sxs-lookup"><span data-stu-id="e1f71-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="e1f71-109">Tato ukázka předvádí dynamický vzor pro publikování a odběr založený na seznamu, ve kterém se klienti můžou přihlásit k odběru nebo odhlásit, jak často potřebujete.</span><span class="sxs-lookup"><span data-stu-id="e1f71-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="e1f71-110">Ukázka publikovat a odběr založený na seznamu se skládá z klienta, služby a programu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="e1f71-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="e1f71-111">Může existovat více než jeden klient a je spuštěn více než jeden program zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="e1f71-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="e1f71-112">Klienti se přihlásí k odběru služby, dostanou oznámení a zruší odběr.</span><span class="sxs-lookup"><span data-stu-id="e1f71-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="e1f71-113">Programy zdroje dat odesílají informace službě, aby se sdílely se všemi aktuálními předplatiteli.</span><span class="sxs-lookup"><span data-stu-id="e1f71-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="e1f71-114">V této ukázce klient a zdroj dat jsou programy konzoly (soubory. exe) a služba je knihovna (. dll) hostovaná ve službě Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="e1f71-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="e1f71-115">Aktivita klient a zdroj dat se zobrazuje na ploše.</span><span class="sxs-lookup"><span data-stu-id="e1f71-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="e1f71-116">Služba používá duplexní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="e1f71-116">The service uses duplex communication.</span></span> <span data-ttu-id="e1f71-117">Kontrakt služby `ISampleContract` se spáruje se smlouvou zpětného volání `ISampleClientCallback`.</span><span class="sxs-lookup"><span data-stu-id="e1f71-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="e1f71-118">Služba implementuje operace odběru a zrušení odběru služby, které klienti používají pro připojení k seznamu předplatitelů nebo jejich opuštění.</span><span class="sxs-lookup"><span data-stu-id="e1f71-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="e1f71-119">Služba také implementuje operaci `PublishPriceChange` služby, kterou program zdroje dat volá k poskytnutí služby novým informacím.</span><span class="sxs-lookup"><span data-stu-id="e1f71-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="e1f71-120">Klientský program implementuje operaci `PriceChange` služby, kterou služba volá, aby upozornila všechny předplatitele změny ceny.</span><span class="sxs-lookup"><span data-stu-id="e1f71-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
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
  
 <span data-ttu-id="e1f71-121">Služba používá událost .NET Framework jako mechanismus pro informování všech předplatitelů o nových informacích.</span><span class="sxs-lookup"><span data-stu-id="e1f71-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="e1f71-122">Když klient připojí službu voláním odběru, poskytne obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="e1f71-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="e1f71-123">Když klient opustí, zruší odběr své obslužné rutiny události od události.</span><span class="sxs-lookup"><span data-stu-id="e1f71-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="e1f71-124">Když zdroj dat volá službu, aby nahlásila změnu ceny, služba událost vyvolá.</span><span class="sxs-lookup"><span data-stu-id="e1f71-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="e1f71-125">Tato akce volá každou instanci služby, jednu pro každého klienta, který má předplatné, a způsobí, že se obslužné rutiny událostí spustí.</span><span class="sxs-lookup"><span data-stu-id="e1f71-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="e1f71-126">Každá obslužná rutina události do svého klienta předává informace prostřednictvím funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e1f71-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
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
  
 <span data-ttu-id="e1f71-127">Po spuštění ukázky spusťte několik klientů.</span><span class="sxs-lookup"><span data-stu-id="e1f71-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="e1f71-128">Klienti se přihlásí k odběru služby.</span><span class="sxs-lookup"><span data-stu-id="e1f71-128">The clients subscribe to the service.</span></span> <span data-ttu-id="e1f71-129">Pak spusťte program zdroje dat, který odesílá informace službě.</span><span class="sxs-lookup"><span data-stu-id="e1f71-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="e1f71-130">Služba předá tyto informace všem předplatitelům.</span><span class="sxs-lookup"><span data-stu-id="e1f71-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="e1f71-131">V každé konzole klienta můžete zobrazit aktivitu s potvrzením, že informace byly přijaty.</span><span class="sxs-lookup"><span data-stu-id="e1f71-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="e1f71-132">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="e1f71-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="e1f71-133">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="e1f71-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="e1f71-134">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1f71-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e1f71-135">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1f71-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="e1f71-136">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="e1f71-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="e1f71-137">Otestujte, zda ke službě můžete přistupovat pomocí prohlížeče zadáním následující adresy: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="e1f71-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="e1f71-138">V odpovědi by se měla zobrazit Stránka s potvrzením.</span><span class="sxs-lookup"><span data-stu-id="e1f71-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="e1f71-139">Spusťte soubor Client. exe z \client\bin\\ze složky pro konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="e1f71-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="e1f71-140">Aktivita klienta se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="e1f71-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="e1f71-141">Spusťte několik klientů.</span><span class="sxs-lookup"><span data-stu-id="e1f71-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="e1f71-142">Spusťte DataSource. exe z \datasource\bin\\ze složky pro konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="e1f71-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="e1f71-143">Aktivita zdroj dat se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e1f71-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="e1f71-144">Jakmile zdroj dat odešle službě informace, měla by být předána každému klientovi.</span><span class="sxs-lookup"><span data-stu-id="e1f71-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="e1f71-145">Pokud klient, zdroj dat a programy nemůžou komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e1f71-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="e1f71-146">Spuštění ukázky napříč počítači</span><span class="sxs-lookup"><span data-stu-id="e1f71-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="e1f71-147">Nastavte počítač služby:</span><span class="sxs-lookup"><span data-stu-id="e1f71-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="e1f71-148">Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="e1f71-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="e1f71-149">Dávkový soubor Setupvroot. bat se dá použít k vytvoření adresáře disku a virtuálního adresáře z [procesu jednorázového nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) .</span><span class="sxs-lookup"><span data-stu-id="e1f71-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="e1f71-150">Zkopírujte programové soubory služby z%SystemDrive%\Inetpub\wwwroot\servicemodelsamples do virtuálního adresáře ServiceModelSamples na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="e1f71-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="e1f71-151">Nezapomeňte zahrnout soubory do adresáře \Bin.</span><span class="sxs-lookup"><span data-stu-id="e1f71-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="e1f71-152">Otestujte, zda ke službě můžete přistupovat z klientského počítače pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="e1f71-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="e1f71-153">Nastavení klientských počítačů:</span><span class="sxs-lookup"><span data-stu-id="e1f71-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="e1f71-154">Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce pro konkrétní jazyk do klientských počítačů.</span><span class="sxs-lookup"><span data-stu-id="e1f71-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="e1f71-155">V každém konfiguračním souboru klienta změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="e1f71-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="e1f71-156">Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="e1f71-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="e1f71-157">Nastavte počítač zdroje dat:</span><span class="sxs-lookup"><span data-stu-id="e1f71-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="e1f71-158">Zkopírujte soubory programu zdroje dat ze složky \datasource\bin\ ve složce specifické pro daný jazyk do počítače zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="e1f71-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="e1f71-159">V konfiguračním souboru zdroje dat změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="e1f71-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="e1f71-160">Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="e1f71-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="e1f71-161">Na klientských počítačích spusťte soubor Client. exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e1f71-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="e1f71-162">Na počítači zdroje dat spusťte soubor DataSource. exe z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e1f71-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e1f71-163">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="e1f71-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e1f71-164">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="e1f71-164">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e1f71-165">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="e1f71-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1f71-166">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e1f71-166">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
