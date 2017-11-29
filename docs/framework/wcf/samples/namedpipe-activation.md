---
title: "Aktivace pojmenovaného kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55594e1505e60ede8d7c6abcbd8a9cf9a1f739bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="namedpipe-activation"></a><span data-ttu-id="8a004-102">Aktivace pojmenovaného kanálu</span><span class="sxs-lookup"><span data-stu-id="8a004-102">NamedPipe Activation</span></span>
<span data-ttu-id="8a004-103">Tento příklad znázorňuje hostování služby, která využívá služba aktivace procesů systému Windows (WAS) k aktivaci služby, který komunikuje přes názvy kanály.</span><span class="sxs-lookup"><span data-stu-id="8a004-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="8a004-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a vyžaduje [!INCLUDE[wv](../../../../includes/wv-md.md)] ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="8a004-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and requires [!INCLUDE[wv](../../../../includes/wv-md.md)] to run.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a004-105">Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8a004-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8a004-106">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="8a004-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8a004-107">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8a004-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8a004-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8a004-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a004-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8a004-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="8a004-110">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8a004-110">Sample Details</span></span>  
 <span data-ttu-id="8a004-111">Ukázka se skládá z konzoly programu klienta (.exe) a služby knihovny (DLL) hostované v pracovním procesu aktivovat pomocí proces aktivace služby WAS (Windows).</span><span class="sxs-lookup"><span data-stu-id="8a004-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="8a004-112">Činnost klienta je viditelný v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="8a004-112">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="8a004-113">Služba se implementuje kontrakt, který definuje komunikační vzor požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8a004-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="8a004-114">Kontrakt je definována `ICalculator` rozhraní, která zpřístupňuje matematické operace (přidat, odečíst, násobení a dělení), jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="8a004-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="8a004-115">Klient zadává synchronní požadavků pro danou matematické operace a implementaci služby vypočítá a vrátí odpovídající výsledek.</span><span class="sxs-lookup"><span data-stu-id="8a004-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>  
  
```  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 <span data-ttu-id="8a004-116">Příklad používá upravené `netNamedPipeBinding` vazba se zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8a004-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="8a004-117">Vazba je zadána v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="8a004-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="8a004-118">Typ vazby služby je zadaný v elementu koncový bod `binding` atributu, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8a004-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
 <span data-ttu-id="8a004-119">Pokud chcete použít vazbu zabezpečené pojmenovaný kanál, změňte režim zabezpečení serveru nastavení požadované zabezpečení a znovu spusťte svcutil.exe na klientovi se získat konfigurační soubor aktualizovaného klienta.</span><span class="sxs-lookup"><span data-stu-id="8a004-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
  
        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->  
        <endpoint address=""   
                  binding="netNamedPipeBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexNamedPipeBinding"  
                  contract="IMetadataExchange" />  
      </service>  
        </services>      
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="Binding1" >  
                    <security mode = "None">  
                    </security>  
                </binding >  
            </netNamedPipeBinding>  
        </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="8a004-120">Informace o koncovém klienta je nakonfigurován, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="8a004-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <endpoint name=""  
                          address="net.pipe://localhost/servicemodelsamples/service.svc"   
                          binding="netNamedPipeBinding"   
                          bindingConfiguration="Binding1"   
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
    <bindings>  
  
      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.  
            Each property is configured with the default value.   -->  
  
      <netNamedPipeBinding>  
        <binding name="Binding1"   
                         maxBufferSize="65536"  
                         maxConnections="10">  
          <security mode = "None">  
          </security>  
        </binding >  
  
      </netNamedPipeBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="8a004-121">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="8a004-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8a004-122">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="8a004-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8a004-123">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="8a004-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8a004-124">Ujistěte se, že [!INCLUDE[iisver](../../../../includes/iisver-md.md)] je nainstalovaná.</span><span class="sxs-lookup"><span data-stu-id="8a004-124">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> [!INCLUDE[iisver](../../../../includes/iisver-md.md)]<span data-ttu-id="8a004-125">je vyžadována pro aktivace WAS.</span><span class="sxs-lookup"><span data-stu-id="8a004-125"> is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="8a004-126">Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8a004-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
     <span data-ttu-id="8a004-127">Kromě toho je nutné nainstalovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Aktivace jiným protokolem než HTTP součásti:</span><span class="sxs-lookup"><span data-stu-id="8a004-127">In addition, you must install the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="8a004-128">Z **spustit** nabídce zvolte **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="8a004-128">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="8a004-129">Vyberte **programy a funkce**.</span><span class="sxs-lookup"><span data-stu-id="8a004-129">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="8a004-130">Klikněte na tlačítko **součásti systému Windows vypnutí a zapnutí**.</span><span class="sxs-lookup"><span data-stu-id="8a004-130">Click **Turn Windows Components on or Off**.</span></span>  
  
    4.  <span data-ttu-id="8a004-131">Rozbalte **rozhraní Microsoft .NET Framework 3.0** uzlu a kontroly **Aktivace jiným protokolem než HTTP Windows Communication Foundation** funkce.</span><span class="sxs-lookup"><span data-stu-id="8a004-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="8a004-132">Konfigurace proces aktivace služby WAS (Windows) pro podporu aktivace pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="8a004-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>  
  
     <span data-ttu-id="8a004-133">Pro potřeby následující dva kroky jsou implementované v dávkovém souboru názvem AddNetPipeSiteBinding.cmd umístěný v adresáři ukázka.</span><span class="sxs-lookup"><span data-stu-id="8a004-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="8a004-134">Kvůli podpoře aktivace net.pipe, musí být nejprve vázána výchozí web na protokol net.pipe.</span><span class="sxs-lookup"><span data-stu-id="8a004-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="8a004-135">To lze provést pomocí appcmd.exe, která se instaluje s sady nástrojů pro správu služby IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="8a004-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="8a004-136">Z příkazového řádku s oprávněními zvýšenými na úroveň (správce) spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="8a004-136">From an elevated (administrator) command prompt, run the following command.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="8a004-137">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="8a004-137">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="8a004-138">Tento příkaz přidá net.pipe vazba webu default Web site.</span><span class="sxs-lookup"><span data-stu-id="8a004-138">This command adds a net.pipe site binding to the default Web site.</span></span>  
  
    2.  <span data-ttu-id="8a004-139">Přestože všechny aplikace v rámci lokality sdílejí společné net.pipe vazbu, každá aplikace můžete povolit podporu net.pipe jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="8a004-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="8a004-140">Pokud chcete povolit net.pipe /servicemodelsamples aplikace, spusťte následující příkaz z příkazového řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="8a004-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="8a004-141">Tento příkaz je na jednom řádku textu.</span><span class="sxs-lookup"><span data-stu-id="8a004-141">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="8a004-142">Tento příkaz umožňuje získat přístup pomocí http://localhost/servicemodelsamples a net.tcp://localhost/servicemodelsamples /servicemodelsamples aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8a004-142">This command enables the /servicemodelsamples application to be accessed using both http://localhost/servicemodelsamples and net.tcp://localhost/servicemodelsamples.</span></span>  
  
4.  <span data-ttu-id="8a004-143">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8a004-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="8a004-144">Odeberte net.pipe vazby webu, který jste přidali Tato ukázka.</span><span class="sxs-lookup"><span data-stu-id="8a004-144">Remove the net.pipe site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="8a004-145">Pro potřeby následující dva kroky jsou implementované v dávkovém souboru názvem RemoveNetPipeSiteBinding.cmd umístěný v adresáři ukázka:</span><span class="sxs-lookup"><span data-stu-id="8a004-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>  
  
    1.  <span data-ttu-id="8a004-146">Odeberte net.tcp ze seznamu povolených protokolů spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="8a004-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="8a004-147">Tento příkaz musí být zadán jako jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="8a004-147">This command must be entered as a single line of text.</span></span>  
  
    2.  <span data-ttu-id="8a004-148">Odeberte vazbu webu net.tcp spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="8a004-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="8a004-149">Tento příkaz musí být zadán v jako jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="8a004-149">This command must be typed in as a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a004-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a004-150">See Also</span></span>  
 [<span data-ttu-id="8a004-151">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="8a004-151">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
