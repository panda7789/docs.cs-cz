---
title: "Trvanlivý duplexní přenos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 014604262952d3aef3676318042ae3c96dc07c89
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="durable-duplex"></a><span data-ttu-id="68660-102">Trvanlivý duplexní přenos</span><span class="sxs-lookup"><span data-stu-id="68660-102">Durable Duplex</span></span>
<span data-ttu-id="68660-103">Tento příklad ukazuje, jak připravit a nakonfigurovat systém exchange trvanlivý duplexní zpráv pomocí zasílání zpráv aktivity v [!INCLUDE[wf](../../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="68660-103">This sample demonstrates how to set up and configure durable duplex message exchange using the messaging activities in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span> <span data-ttu-id="68660-104">Trvanlivý duplexní zpráva exchange je obousměrný zpráva systému exchange, který probíhá po dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="68660-104">A durable duplex message exchange is a two-way message exchange that takes place over a long period of time.</span></span> <span data-ttu-id="68660-105">Doba platnosti výměny zpráv může být delší než komunikační kanál životnost a doba platnosti v paměti instancí služby.</span><span class="sxs-lookup"><span data-stu-id="68660-105">The lifetime of the message exchange may be longer than the lifetime of the communication channel and the in-memory lifetime of the service instances.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="68660-106">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="68660-106">Sample Details</span></span>  
 <span data-ttu-id="68660-107">V této ukázce dvě [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby je implementovaná sadou [!INCLUDE[wf2](../../../../includes/wf2-md.md)] jsou nakonfigurovány tak, aby měl exchange trvanlivý duplexní zprávy.</span><span class="sxs-lookup"><span data-stu-id="68660-107">In this sample, two [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services implemented using [!INCLUDE[wf2](../../../../includes/wf2-md.md)] are configured to have a durable duplex message exchange.</span></span> <span data-ttu-id="68660-108">Trvanlivý duplexní zpráva exchange se skládá ze dvou jednosměrný zprávy přes služby MSMQ a korelační pomocí [.NET kontextová výměna](http://go.microsoft.com/fwlink/?LinkID=166059).</span><span class="sxs-lookup"><span data-stu-id="68660-108">The durable duplex message exchange is composed from two one-way messages sent over MSMQ and correlated using [.NET Context Exchange](http://go.microsoft.com/fwlink/?LinkID=166059).</span></span> <span data-ttu-id="68660-109">Odeslání zpráv pomocí <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> aktivity zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="68660-109">The messages are sent using the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.Receive> messaging activities.</span></span> <span data-ttu-id="68660-110">Kontextová výměna .NET je slouží k určení adresu zpětné volání na odeslané zprávy.</span><span class="sxs-lookup"><span data-stu-id="68660-110">.NET Context Exchange is use to specify the callback address on the sent messages.</span></span> <span data-ttu-id="68660-111">Obě služby jsou hostované pomocí služby Aktivace procesů systému Windows (WAS) a jsou nakonfigurovány pro zapnout stálost instancí služby.</span><span class="sxs-lookup"><span data-stu-id="68660-111">Both services are hosted using Windows Process Activation Services (WAS) and are configured to enable persistence of the services instances.</span></span>  
  
 <span data-ttu-id="68660-112">První službě (Service1.xamlx) odešle požadavek na službu odeslání (Service2.xamlx) nějakou práci.</span><span class="sxs-lookup"><span data-stu-id="68660-112">The first service (Service1.xamlx) sends a request to the send service (Service2.xamlx) to do some work.</span></span> <span data-ttu-id="68660-113">Po dokončení práce Service2.xamlx odešle oznámení zpátky do Service1.xamlx indikující, že práce na byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="68660-113">Once the work is completed, Service2.xamlx sends a notification back to Service1.xamlx to indicate that the work has been completed.</span></span> <span data-ttu-id="68660-114">Konzolové aplikace pracovního postupu nastaví fronty, které služby jsou naslouchá na a odešle zprávu počáteční počáteční aktivovat Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="68660-114">A workflow console application sets up the queues that the services are listening on and sends the initial Start message to activate Service1.xamlx.</span></span> <span data-ttu-id="68660-115">Jakmile Service1.xamlx obdrží oznámení z Service2.xamlx dokončí požadovanou pracovní, Service1.xamlx výsledek uloží do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="68660-115">Once Service1.xamlx receives the notification from Service2.xamlx that the requested work has been completed, Service1.xamlx saves the result to an XML file.</span></span> <span data-ttu-id="68660-116">Při čekání na zprávu zpětného volání, Service1.xamlx potrvají jeho stav instance pomocí výchozího <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span><span class="sxs-lookup"><span data-stu-id="68660-116">While waiting for the callback message, Service1.xamlx persists its instance state using the default <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span></span> <span data-ttu-id="68660-117">Service2.xamlx trvá jeho stav instance jako součást dokončení práce požadoval Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="68660-117">Service2.xamlx persists its instance state as part of completing the work requested by Service1.xamlx.</span></span>  
  
 <span data-ttu-id="68660-118">Ke konfiguraci služby na používání rozhraní .NET kontextová výměna přes služby MSMQ, obě služby jsou nakonfigurovány pro použití vlastní vazby, která se skládá z <xref:System.ServiceModel.Channels.ContextBindingElement> a <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="68660-118">To configure the services to use .NET Context Exchange over MSMQ, both services are configured to use a custom binding that consists of the <xref:System.ServiceModel.Channels.ContextBindingElement> and the <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span></span> <span data-ttu-id="68660-119">Je zadaný adresu zpětné volání <xref:System.ServiceModel.Channels.ContextBindingElement> a je součástí všech zpráv odeslaných použití vlastní vazby v hlavičce kontext zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="68660-119">A callback address is specified with the <xref:System.ServiceModel.Channels.ContextBindingElement> and is included in a callback context header with all messages sent using a custom binding.</span></span> <span data-ttu-id="68660-120">Následující příklad kódu definuje vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="68660-120">The following code example defines the custom binding.</span></span>  
  
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
>  <span data-ttu-id="68660-121">Vazba používá tato ukázka není zabezpečený.</span><span class="sxs-lookup"><span data-stu-id="68660-121">The binding used by this sample is not secure.</span></span> <span data-ttu-id="68660-122">Při nasazování aplikace byste měli nakonfigurovat vaše vazby v závislosti na požadavcích zabezpečení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="68660-122">When deploying your application you should configure your binding based on the security requirements of your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68660-123">Fronty použít v této ukázce nejsou transakcí.</span><span class="sxs-lookup"><span data-stu-id="68660-123">The queues used in this sample are not transactional.</span></span> <span data-ttu-id="68660-124">Příklad, který ukazuje, jak nastavit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] výměnu pomocí transakce front zpráv najdete v tématu [aktivace MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="68660-124">For a sample that shows how to set up [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] message exchanges using transaction queues, see the [MSMQ Activation](../../../../docs/framework/wcf/samples/msmq-activation.md) sample.</span></span>  
  
 <span data-ttu-id="68660-125">Zpráva odeslaná Service1.xamlx Service2.xamlx odeslána, koncový bod klienta nakonfigurovanou adresu Service2.xamlx a vlastní vazby pomocí definována dříve.</span><span class="sxs-lookup"><span data-stu-id="68660-125">The message sent by Service1.xamlx to Service2.xamlx is sent using a client endpoint configured with the address of Service2.xamlx and the custom binding defined previously.</span></span> <span data-ttu-id="68660-126">Zpětné volání z Service2.xamlx Service1.xamlx je odeslána pomocí koncový bod klienta s žádnou explicitně nakonfigurovanou adresu, protože adresa je převzat ze zpětného volání kontextu poslal Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="68660-126">The callback from Service2.xamlx to Service1.xamlx is sent using a client endpoint with no explicitly configured address because the address is taken from the callback context sent by Service1.xamlx.</span></span> <span data-ttu-id="68660-127">Následující příklad kódu definuje koncové body klientů.</span><span class="sxs-lookup"><span data-stu-id="68660-127">The following code example defines the client endpoints.</span></span>  
  
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
  
 <span data-ttu-id="68660-128">Následující příklad kódu zpřístupní koncové body pomocí tento vlastní vazby změnou výchozí mapování protokolu pro základní adresy net.msmq používat tento vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="68660-128">The following code example exposes endpoints using this custom binding by changing the default protocol mapping for net.msmq base addresses to use this custom binding.</span></span>  
  
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
  
 <span data-ttu-id="68660-129">Následující příklad kódu povolí trvalost pro obě služby přidáním <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování služby a zadat připojovací řetězec pro databázi trvalost.</span><span class="sxs-lookup"><span data-stu-id="68660-129">The following code example enables persistence for both services by adding the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior to both services and specifying the connection string for the persistence database.</span></span>  
  
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
  
## <a name="system-requirements"></a><span data-ttu-id="68660-130">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="68660-130">System Requirements</span></span>  
 <span data-ttu-id="68660-131">Tato ukázka vyžaduje následující součásti.</span><span class="sxs-lookup"><span data-stu-id="68660-131">This sample requires the following components.</span></span>  
  
1.  <span data-ttu-id="68660-132">Internetová informační služba.</span><span class="sxs-lookup"><span data-stu-id="68660-132">Internet Information Services.</span></span>  
  
2.  <span data-ttu-id="68660-133">Internetová informační služba -> Kompatibilita správy služby IIS 6.0 -> Konfigurace Kompatibilita metabáze služby IIS a služby IIS 6.0.</span><span class="sxs-lookup"><span data-stu-id="68660-133">Internet Information Services -> IIS 6.0 Management Compatibility -> IIS Metabase and IIS 6.0 configuration compatibility.</span></span>  
  
3.  <span data-ttu-id="68660-134">Webové služby -> vývoj aplikací funkce -> technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="68660-134">World Wide Web Services -> Application Development Features -> ASP.NET.</span></span>  
  
4.  <span data-ttu-id="68660-135">Server Microsoft zprávu fronty (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="68660-135">Microsoft Message Queues (MSMQ) Server.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="68660-136">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="68660-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="68660-137">Nastavte databázi trvalosti a adresáři výsledky.</span><span class="sxs-lookup"><span data-stu-id="68660-137">Set up the persistence database and the results directory.</span></span>  
  
    1.  <span data-ttu-id="68660-138">Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="68660-138">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="68660-139">Přejděte do složky, aby tato ukázka a spusťte Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="68660-139">Navigate to the folder for this sample and run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="68660-140">Nastavte virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="68660-140">Set up the virtual application.</span></span>  
  
    1.  <span data-ttu-id="68660-141">Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazový řádek, zaregistrovat ASP.NET tak, že spustíte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="68660-141">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by running the following command.</span></span>  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  <span data-ttu-id="68660-142">Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] s oprávněními správce kliknutím pravým tlačítkem na [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a výběrem **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="68660-142">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator permissions by right-clicking [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and selecting **Run as administrator**.</span></span>  
  
    3.  <span data-ttu-id="68660-143">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor DurableDuplex.sln.</span><span class="sxs-lookup"><span data-stu-id="68660-143">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DurableDuplex.sln file.</span></span>  
  
3.  <span data-ttu-id="68660-144">Nastavení fronty služby service.</span><span class="sxs-lookup"><span data-stu-id="68660-144">Set up the service queues.</span></span>  
  
    1.  <span data-ttu-id="68660-145">Spuštění klienta DurableDuplex, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="68660-145">To run the DurableDuplex client, press F5.</span></span>  
  
    2.  <span data-ttu-id="68660-146">Otevřete **Správa počítače** konzoly spuštěním `Compmgmt.msc` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="68660-146">Open the **Computer Management** console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    3.  <span data-ttu-id="68660-147">Rozbalte položku **služby a aplikace**, **služby Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="68660-147">Expand **Service and Applications**, **Message Queuing**.</span></span> <span data-ttu-id="68660-148">**Soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="68660-148">**Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="68660-149">Klikněte pravým tlačítkem na durableduplex/service1.xamlx a durableduplex/service2.xamlx front a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="68660-149">Right-click the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues and select **Properties**.</span></span>  
  
    5.  <span data-ttu-id="68660-150">Vyberte **zabezpečení** kartě a povolit **Everyone přijímat zprávy**, **prohlížet zprávy** a **odeslat zprávu** oprávnění pro obě fronty.</span><span class="sxs-lookup"><span data-stu-id="68660-150">Select the **Security** tab and allow **Everyone Receive Message**, **Peek Message** and **Send Message** permissions for both queues.</span></span>  
  
    6.  <span data-ttu-id="68660-151">Otevřete Správce Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="68660-151">Open Internet Information Services (IIS) Manager.</span></span>  
  
    7.  <span data-ttu-id="68660-152">Přejděte do **Server**, **lokality**, **výchozí web**, **privátní**, **trvanlivý duplexní** a vyberte **Rozšířené možnosti**.</span><span class="sxs-lookup"><span data-stu-id="68660-152">Browse to **Server**, **Sites**, **Default Web site**, **private**, **Durable Duplex** and select **Advanced Options**.</span></span>  
  
    8.  <span data-ttu-id="68660-153">Změna **povolené protokoly** k **http,net.msmq**.</span><span class="sxs-lookup"><span data-stu-id="68660-153">Change the **Enabled Protocols** to **http,net.msmq**.</span></span>  
  
4.  <span data-ttu-id="68660-154">Spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="68660-154">Run the sample.</span></span>  
  
    1.  <span data-ttu-id="68660-155">Přejděte do http://localhost/private/durableduplex/service1.xamlx a http://localhost/private/durableduplex/service2.xamlx zajistit, že jsou obě služby spuštěny.</span><span class="sxs-lookup"><span data-stu-id="68660-155">Browse to http://localhost/private/durableduplex/service1.xamlx and http://localhost/private/durableduplex/service2.xamlx to ensure that both services are running.</span></span>  
  
    2.  <span data-ttu-id="68660-156">Stisknutím klávesy F5 spusťte DurableDuplexClient.</span><span class="sxs-lookup"><span data-stu-id="68660-156">Press F5 to run DurableDuplexClient.</span></span>  
  
         <span data-ttu-id="68660-157">Po dokončení exchange trvanlivý duplexní zpráva result.xml soubor je uložen ve složce C:\Inbox a obsahuje výsledek zprávy exchange.</span><span class="sxs-lookup"><span data-stu-id="68660-157">When the durable duplex message exchange completes a result.xml file is saved to the C:\Inbox folder and contains the result of the message exchange.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="68660-158">Pro čištění (volitelné)</span><span class="sxs-lookup"><span data-stu-id="68660-158">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="68660-159">Spusťte Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="68660-159">Run Cleanup.cmd.</span></span>  
  
    1.  <span data-ttu-id="68660-160">Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="68660-160">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="68660-161">Přejděte do složky, aby tato ukázka a spusťte Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="68660-161">Navigate to the folder for this sample and run Cleanup.cmd.</span></span>  
  
2.  <span data-ttu-id="68660-162">Odeberte virtuální aplikace pro služby.</span><span class="sxs-lookup"><span data-stu-id="68660-162">Remove the virtual application for the services.</span></span>  
  
    1.  <span data-ttu-id="68660-163">Otevřete Správce Internetové informační služby (IIS) spuštěním `Inetmgr.exe` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="68660-163">Open the Internet Information Services (IIS) Manager by running `Inetmgr.exe` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="68660-164">Přejděte na výchozí web a odebrat **privátní** virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="68660-164">Browse to the default Web site and remove the **private** virtual directory.</span></span>  
  
3.  <span data-ttu-id="68660-165">Odeberte nastavení pro tato ukázka fronty.</span><span class="sxs-lookup"><span data-stu-id="68660-165">Remove the queues set up for this sample.</span></span>  
  
    1.  <span data-ttu-id="68660-166">Otevřete konzolu pro správu počítače spuštěním `Compmgmt.msc` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="68660-166">Open the Computer Management console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="68660-167">Rozbalte položku **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="68660-167">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    3.  <span data-ttu-id="68660-168">Odstraňte durableduplex/service1.xamlx a durableduplex/service2.xamlx fronty.</span><span class="sxs-lookup"><span data-stu-id="68660-168">Delete the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues.</span></span>  
  
4.  <span data-ttu-id="68660-169">Odeberte adresář C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="68660-169">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68660-170">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="68660-170">The samples may already be installed on your machine.</span></span> <span data-ttu-id="68660-171">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="68660-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="68660-172">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="68660-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="68660-173">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="68660-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`