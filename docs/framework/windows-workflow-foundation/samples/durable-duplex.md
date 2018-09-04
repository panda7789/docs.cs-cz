---
title: Trvanlivý duplexní přenos
ms.date: 03/30/2017
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
ms.openlocfilehash: 107c617fa4a8ee0279dcaa07e495587c617b866e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513350"
---
# <a name="durable-duplex"></a><span data-ttu-id="d230e-102">Trvanlivý duplexní přenos</span><span class="sxs-lookup"><span data-stu-id="d230e-102">Durable Duplex</span></span>
<span data-ttu-id="d230e-103">Tento příklad ukazuje, jak vytvořit a nakonfigurovat exchange zpráv trvalý duplexní pomocí aktivit zasílání zpráv ve Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="d230e-103">This sample demonstrates how to set up and configure durable duplex message exchange using the messaging activities in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="d230e-104">Výměna zpráv trvalý duplexní je obousměrný zprávy serveru exchange, která probíhá přes dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="d230e-104">A durable duplex message exchange is a two-way message exchange that takes place over a long period of time.</span></span> <span data-ttu-id="d230e-105">Doba života výměny zpráv může být delší než životnost komunikační kanál a v paměti dobu životnosti instance služby.</span><span class="sxs-lookup"><span data-stu-id="d230e-105">The lifetime of the message exchange may be longer than the lifetime of the communication channel and the in-memory lifetime of the service instances.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="d230e-106">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d230e-106">Sample Details</span></span>  
 <span data-ttu-id="d230e-107">V této ukázce jsou nakonfigurovány dvě služby Windows Communication Foundation (WCF), které jsou implementované pomocí programovacího modelu Windows Workflow Foundation na trvalý duplexní zprávy exchange.</span><span class="sxs-lookup"><span data-stu-id="d230e-107">In this sample, two Windows Communication Foundation (WCF) services implemented using Windows Workflow Foundation are configured to have a durable duplex message exchange.</span></span> <span data-ttu-id="d230e-108">Výměna zpráv trvalý duplexní se skládá ze dvou jednosměrné zprávy zaslaného prostřednictvím služby MSMQ a korelační pomocí [.NET kontextová výměna](https://go.microsoft.com/fwlink/?LinkID=166059).</span><span class="sxs-lookup"><span data-stu-id="d230e-108">The durable duplex message exchange is composed from two one-way messages sent over MSMQ and correlated using [.NET Context Exchange](https://go.microsoft.com/fwlink/?LinkID=166059).</span></span> <span data-ttu-id="d230e-109">Zprávy jsou odeslány pomocí <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> zasílání zpráv aktivity.</span><span class="sxs-lookup"><span data-stu-id="d230e-109">The messages are sent using the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.Receive> messaging activities.</span></span> <span data-ttu-id="d230e-110">Kontextová výměna .NET se používá k určení adresa zpětného volání pro odeslané zprávy.</span><span class="sxs-lookup"><span data-stu-id="d230e-110">.NET Context Exchange is use to specify the callback address on the sent messages.</span></span> <span data-ttu-id="d230e-111">Obě služby jsou hostované pomocí služby aktivační procesů Windows (WAS) a jsou nakonfigurované tak, aby stálost instance služby.</span><span class="sxs-lookup"><span data-stu-id="d230e-111">Both services are hosted using Windows Process Activation Services (WAS) and are configured to enable persistence of the services instances.</span></span>  
  
 <span data-ttu-id="d230e-112">První služby (Service1.xamlx) odešle požadavek službě odeslat (Service2.xamlx) nějakou práci.</span><span class="sxs-lookup"><span data-stu-id="d230e-112">The first service (Service1.xamlx) sends a request to the send service (Service2.xamlx) to do some work.</span></span> <span data-ttu-id="d230e-113">Po dokončení práce Service2.xamlx oznámení odešle zpět do Service1.xamlx k označení, že práce byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="d230e-113">Once the work is completed, Service2.xamlx sends a notification back to Service1.xamlx to indicate that the work has been completed.</span></span> <span data-ttu-id="d230e-114">Konzolová aplikace pracovního postupu nastaví fronty, které služby naslouchají na a odesílá počáteční zpráva spuštění k aktivaci Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="d230e-114">A workflow console application sets up the queues that the services are listening on and sends the initial Start message to activate Service1.xamlx.</span></span> <span data-ttu-id="d230e-115">Jakmile Service1.xamlx obdrží oznámení z Service2.xamlx dokončení požadované pracovní, Service1.xamlx uloží výsledek do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="d230e-115">Once Service1.xamlx receives the notification from Service2.xamlx that the requested work has been completed, Service1.xamlx saves the result to an XML file.</span></span> <span data-ttu-id="d230e-116">Při čekání na zpětné volání zprávy, Service1.xamlx nevyřeší jeho stav instance pomocí výchozího <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span><span class="sxs-lookup"><span data-stu-id="d230e-116">While waiting for the callback message, Service1.xamlx persists its instance state using the default <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span></span> <span data-ttu-id="d230e-117">Service2.xamlx udržuje svůj stav instance jako součást dokončení práce požadoval Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="d230e-117">Service2.xamlx persists its instance state as part of completing the work requested by Service1.xamlx.</span></span>  
  
 <span data-ttu-id="d230e-118">Ke konfiguraci služby na používání .NET kontextová výměna přes služby MSMQ, obě služby jsou nakonfigurovány pro použití vlastní vazby, který se skládá z <xref:System.ServiceModel.Channels.ContextBindingElement> a <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d230e-118">To configure the services to use .NET Context Exchange over MSMQ, both services are configured to use a custom binding that consists of the <xref:System.ServiceModel.Channels.ContextBindingElement> and the <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span></span> <span data-ttu-id="d230e-119">Adresa zpětného volání je zadán s <xref:System.ServiceModel.Channels.ContextBindingElement> a je součástí hlavičku kontextu zpětného volání s všechny zprávy odeslané prostřednictvím vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d230e-119">A callback address is specified with the <xref:System.ServiceModel.Channels.ContextBindingElement> and is included in a callback context header with all messages sent using a custom binding.</span></span> <span data-ttu-id="d230e-120">Následující příklad kódu definuje vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d230e-120">The following code example defines the custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="d230e-121">Vazba použitá v tomto příkladu není zabezpečený.</span><span class="sxs-lookup"><span data-stu-id="d230e-121">The binding used by this sample is not secure.</span></span> <span data-ttu-id="d230e-122">Při nasazení vaší aplikace byste měli nakonfigurovat vaše vazby na základě požadavků zabezpečení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="d230e-122">When deploying your application you should configure your binding based on the security requirements of your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d230e-123">Fronty používané v tomto příkladu nejsou transakční.</span><span class="sxs-lookup"><span data-stu-id="d230e-123">The queues used in this sample are not transactional.</span></span> <span data-ttu-id="d230e-124">Příklad, který ukazuje, jak nastavit výměny zpráv WCF pomocí fronty transakcí, najdete v článku [aktivace služby MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="d230e-124">For a sample that shows how to set up WCF message exchanges using transaction queues, see the [MSMQ Activation](../../../../docs/framework/wcf/samples/msmq-activation.md) sample.</span></span>  
  
 <span data-ttu-id="d230e-125">Zpráva odeslaná Service1.xamlx Service2.xamlx přijde, že koncový bod klienta nakonfigurovanou adresu Service2.xamlx a vlastní vazby pomocí dříve definovali.</span><span class="sxs-lookup"><span data-stu-id="d230e-125">The message sent by Service1.xamlx to Service2.xamlx is sent using a client endpoint configured with the address of Service2.xamlx and the custom binding defined previously.</span></span> <span data-ttu-id="d230e-126">Zpětné volání z Service2.xamlx Service1.xamlx se odešle pomocí koncový bod klienta s žádnou explicitně nakonfigurovanou adresu, protože adresa je převzata z kontextu zpětného volání odesílaných Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="d230e-126">The callback from Service2.xamlx to Service1.xamlx is sent using a client endpoint with no explicitly configured address because the address is taken from the callback context sent by Service1.xamlx.</span></span> <span data-ttu-id="d230e-127">Následující příklad kódu definuje koncové body klienta.</span><span class="sxs-lookup"><span data-stu-id="d230e-127">The following code example defines the client endpoints.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="d230e-128">Následující příklad kódu zveřejňuje koncové body, které používá tuto vlastní vazbu tak, že změníte výchozí mapování protokolů pro základní adresy net.msmq používat tento vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d230e-128">The following code example exposes endpoints using this custom binding by changing the default protocol mapping for net.msmq base addresses to use this custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="d230e-129">Následující příklad kódu povolí trvalost pro obě služby tak, že přidáte <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování služby a zadávání připojovacího řetězce databáze trvalosti.</span><span class="sxs-lookup"><span data-stu-id="d230e-129">The following code example enables persistence for both services by adding the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior to both services and specifying the connection string for the persistence database.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a><span data-ttu-id="d230e-130">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="d230e-130">System Requirements</span></span>  
 <span data-ttu-id="d230e-131">Tato ukázka vyžaduje následující součásti.</span><span class="sxs-lookup"><span data-stu-id="d230e-131">This sample requires the following components.</span></span>  
  
1.  <span data-ttu-id="d230e-132">Internetová informační služba.</span><span class="sxs-lookup"><span data-stu-id="d230e-132">Internet Information Services.</span></span>  
  
2.  <span data-ttu-id="d230e-133">Internetová informační služba -> Kompatibilita správy služby IIS 6.0 -> Konfigurace kompatibility metabáze služby IIS a služby IIS 6.0.</span><span class="sxs-lookup"><span data-stu-id="d230e-133">Internet Information Services -> IIS 6.0 Management Compatibility -> IIS Metabase and IIS 6.0 configuration compatibility.</span></span>  
  
3.  <span data-ttu-id="d230e-134">Webová služba -> vývoj aplikace ASP.NET-funkce >.</span><span class="sxs-lookup"><span data-stu-id="d230e-134">World Wide Web Services -> Application Development Features -> ASP.NET.</span></span>  
  
4.  <span data-ttu-id="d230e-135">Server Microsoft zpráv fronty (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="d230e-135">Microsoft Message Queues (MSMQ) Server.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d230e-136">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="d230e-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="d230e-137">Nastavení databáze trvalosti a složka výsledků.</span><span class="sxs-lookup"><span data-stu-id="d230e-137">Set up the persistence database and the results directory.</span></span>  
  
    1.  <span data-ttu-id="d230e-138">Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d230e-138">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="d230e-139">Přejděte do složky pro tuto ukázku a spustit Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="d230e-139">Navigate to the folder for this sample and run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="d230e-140">Nastavte virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="d230e-140">Set up the virtual application.</span></span>  
  
    1.  <span data-ttu-id="d230e-141">Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku, spuštěním následujícího příkazu registrace technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d230e-141">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by running the following command.</span></span>  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  <span data-ttu-id="d230e-142">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] s oprávněními správce kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a vyberete **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="d230e-142">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator permissions by right-clicking [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and selecting **Run as administrator**.</span></span>  
  
    3.  <span data-ttu-id="d230e-143">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor DurableDuplex.sln.</span><span class="sxs-lookup"><span data-stu-id="d230e-143">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DurableDuplex.sln file.</span></span>  
  
3.  <span data-ttu-id="d230e-144">Nastavení služby front.</span><span class="sxs-lookup"><span data-stu-id="d230e-144">Set up the service queues.</span></span>  
  
    1.  <span data-ttu-id="d230e-145">Pokud chcete spustit klienta DurableDuplex, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="d230e-145">To run the DurableDuplex client, press F5.</span></span>  
  
    2.  <span data-ttu-id="d230e-146">Otevřít **Správa počítače** konzoly spuštěním `Compmgmt.msc` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d230e-146">Open the **Computer Management** console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    3.  <span data-ttu-id="d230e-147">Rozbalte **služby a aplikace**, **služby Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="d230e-147">Expand **Service and Applications**, **Message Queuing**.</span></span> <span data-ttu-id="d230e-148">**Soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="d230e-148">**Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="d230e-149">Klikněte pravým tlačítkem na durableduplex/service1.xamlx a durableduplex/service2.xamlx front a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d230e-149">Right-click the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues and select **Properties**.</span></span>  
  
    5.  <span data-ttu-id="d230e-150">Vyberte **zabezpečení** kartu a povolit **přijímat zprávy všem**, **prohlížet zprávy** a **poslat zprávu** oprávnění pro oba front.</span><span class="sxs-lookup"><span data-stu-id="d230e-150">Select the **Security** tab and allow **Everyone Receive Message**, **Peek Message** and **Send Message** permissions for both queues.</span></span>  
  
    6.  <span data-ttu-id="d230e-151">Otevřete Správce Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="d230e-151">Open Internet Information Services (IIS) Manager.</span></span>  
  
    7.  <span data-ttu-id="d230e-152">Přejděte do **Server**, **lokality**, **výchozí webová stránka**, **privátní**, **trvalý duplexní** a vyberte **Pokročilé možnosti**.</span><span class="sxs-lookup"><span data-stu-id="d230e-152">Browse to **Server**, **Sites**, **Default Web site**, **private**, **Durable Duplex** and select **Advanced Options**.</span></span>  
  
    8.  <span data-ttu-id="d230e-153">Změnit **povolené protokoly** k **http,net.msmq**.</span><span class="sxs-lookup"><span data-stu-id="d230e-153">Change the **Enabled Protocols** to **http,net.msmq**.</span></span>  
  
4.  <span data-ttu-id="d230e-154">Spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="d230e-154">Run the sample.</span></span>  
  
    1.  <span data-ttu-id="d230e-155">Přejděte do http://localhost/private/durableduplex/service1.xamlx a http://localhost/private/durableduplex/service2.xamlx zajistit, že obě služby jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="d230e-155">Browse to http://localhost/private/durableduplex/service1.xamlx and http://localhost/private/durableduplex/service2.xamlx to ensure that both services are running.</span></span>  
  
    2.  <span data-ttu-id="d230e-156">Stisknutím klávesy F5 spusťte DurableDuplexClient.</span><span class="sxs-lookup"><span data-stu-id="d230e-156">Press F5 to run DurableDuplexClient.</span></span>  
  
         <span data-ttu-id="d230e-157">Po dokončení výměnu zpráv trvalý duplexní result.xml soubor se uloží do složky C:\Inbox a obsahuje výsledek výměně zpráv.</span><span class="sxs-lookup"><span data-stu-id="d230e-157">When the durable duplex message exchange completes a result.xml file is saved to the C:\Inbox folder and contains the result of the message exchange.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="d230e-158">Vyčistit (volitelné)</span><span class="sxs-lookup"><span data-stu-id="d230e-158">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="d230e-159">Spusťte Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="d230e-159">Run Cleanup.cmd.</span></span>  
  
    1.  <span data-ttu-id="d230e-160">Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d230e-160">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="d230e-161">Přejděte do složky pro tuto ukázku a spusťte Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="d230e-161">Navigate to the folder for this sample and run Cleanup.cmd.</span></span>  
  
2.  <span data-ttu-id="d230e-162">Odeberte virtuální aplikace pro služby.</span><span class="sxs-lookup"><span data-stu-id="d230e-162">Remove the virtual application for the services.</span></span>  
  
    1.  <span data-ttu-id="d230e-163">Otevřete Správce Internetové informační služby (IIS), že spustíte `Inetmgr.exe` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d230e-163">Open the Internet Information Services (IIS) Manager by running `Inetmgr.exe` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="d230e-164">Přejděte na výchozí web a odebrat **privátní** virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="d230e-164">Browse to the default Web site and remove the **private** virtual directory.</span></span>  
  
3.  <span data-ttu-id="d230e-165">Odeberte nastavení pro tuto ukázku fronty.</span><span class="sxs-lookup"><span data-stu-id="d230e-165">Remove the queues set up for this sample.</span></span>  
  
    1.  <span data-ttu-id="d230e-166">Otevřete konzolu pro správu počítače spuštěním `Compmgmt.msc` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d230e-166">Open the Computer Management console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="d230e-167">Rozbalte **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="d230e-167">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    3.  <span data-ttu-id="d230e-168">Odstraňte durableduplex/service1.xamlx a durableduplex/service2.xamlx fronty.</span><span class="sxs-lookup"><span data-stu-id="d230e-168">Delete the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues.</span></span>  
  
4.  <span data-ttu-id="d230e-169">Odeberte adresář C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="d230e-169">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d230e-170">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="d230e-170">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d230e-171">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d230e-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d230e-172">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d230e-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d230e-173">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d230e-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`