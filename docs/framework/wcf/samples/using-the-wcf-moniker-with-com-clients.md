---
title: "Použití monikeru služby WCF u klientů modelu COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dbda85f056d7e8a465127bff948dcaaaf41094d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="e1209-102">Použití monikeru služby WCF u klientů modelu COM</span><span class="sxs-lookup"><span data-stu-id="e1209-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="e1209-103">Tento příklad znázorňuje způsob použití [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] monikeru služby pro integraci webových služeb do založená na modelu COM vývojových prostředí, jako je například Microsoft Office Visual Basic pro aplikace (Office VBA) nebo Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="e1209-103">This sample demonstrates how to use the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="e1209-104">Tato ukázka se skládá z klienta Windows Script Host (.vbs), podporující klientské knihovny DLL (.dll) a služby knihovny (DLL) hostované Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="e1209-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="e1209-105">Služba je služba kalkulačky a klient COM volá matematické operace – přidat, odečíst, násobit a dělit – ve službě.</span><span class="sxs-lookup"><span data-stu-id="e1209-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="e1209-106">Činnost klienta je viditelný v systému windows pole zpráva.</span><span class="sxs-lookup"><span data-stu-id="e1209-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1209-107">Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e1209-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e1209-108">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="e1209-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e1209-109">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e1209-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e1209-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e1209-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1209-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e1209-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="e1209-112">Implementuje služby `ICalculator` kontrakt definovaný jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="e1209-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="e1209-113">Ukázka ukazuje tři alternativní přístupy k použití Přezdívka:</span><span class="sxs-lookup"><span data-stu-id="e1209-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
-   <span data-ttu-id="e1209-114">Typové kontrakt – kontrakt je registrován jako typ viditelné modelu COM v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="e1209-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
-   <span data-ttu-id="e1209-115">Kontrakt WSDL – kontrakt poskytuje ve formě dokumentu WSDL.</span><span class="sxs-lookup"><span data-stu-id="e1209-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="e1209-116">V době běhu z koncového bodu metadat Exchange (MEX) je načíst metadata Exchange kontrakt – kontrakt.</span><span class="sxs-lookup"><span data-stu-id="e1209-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="e1209-117">Typové kontraktu</span><span class="sxs-lookup"><span data-stu-id="e1209-117">Typed Contract</span></span>  
 <span data-ttu-id="e1209-118">Pokud chcete použít Přezdívka s použitím zadaných kontrakt, musí být správně s atributy typy pro kontrakt služby registrovaný pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e1209-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="e1209-119">Nejprve klienta musí být vytvořen pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e1209-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="e1209-120">Spusťte následující příkaz z příkazového řádku v adresáři klienta ke generování typem proxy.</span><span class="sxs-lookup"><span data-stu-id="e1209-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="e1209-121">Tato třída musí být součástí projekt a projekt by měl být nakonfigurovaný pro generování COM – viditelné, podepsané sestavení při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="e1209-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="e1209-122">Následující atribut by měl být součástí souboru AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="e1209-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```  
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="e1209-123">Po vytvoření projektu, zaregistrujte COM – viditelné typy pomocí `regasm` jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e1209-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="e1209-124">Sestavení, které se vytvoří musí být přidaní do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="e1209-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="e1209-125">I když není nezbytně nutné, tato funkce zjednodušuje proces modulu runtime vyhledání sestavení.</span><span class="sxs-lookup"><span data-stu-id="e1209-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="e1209-126">Následující příkaz přidá sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="e1209-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  <span data-ttu-id="e1209-127">Monikeru služby vyžaduje pouze registrace typu a nepoužívá ke komunikaci se službou proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="e1209-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="e1209-128">ComCalcClient.vbs klientská aplikace používá `GetObject` funkce sestavit proxy server pro službu pomocí syntaxe přezdívka služby zadáním adresy, vazby a smlouvy pro službu.</span><span class="sxs-lookup"><span data-stu-id="e1209-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```  
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="e1209-129">Zadejte parametry používané Přezdívka:</span><span class="sxs-lookup"><span data-stu-id="e1209-129">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="e1209-130">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="e1209-130">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="e1209-131">Vazba, který klient musí použít pro připojení k tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e1209-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="e1209-132">V takovém případě wsHttpBinding definované v systému se používá, když vlastní vazby lze definovat v konfiguračních souborech klienta.</span><span class="sxs-lookup"><span data-stu-id="e1209-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="e1209-133">Pro použití se službou Windows Script Host vlastní vazby je definována v souboru Cscript.exe.config ve stejném adresáři jako Cscript.exe.</span><span class="sxs-lookup"><span data-stu-id="e1209-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
-   <span data-ttu-id="e1209-134">Typ smlouvy, které je podporovaná v koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e1209-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="e1209-135">Jedná se o typ, která byla vygenerována a zaregistrován výše.</span><span class="sxs-lookup"><span data-stu-id="e1209-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="e1209-136">Vzhledem k tomu, že skript jazyka Visual Basic neposkytuje prostředí silného typu modelu COM, musí být zadán identifikátor pro kontrakt.</span><span class="sxs-lookup"><span data-stu-id="e1209-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="e1209-137">Tento identifikátor GUID je `interfaceID` z CalcProxy.tlb, které lze zobrazit pomocí nástrojů modelu COM, jako je například prohlížeč objektů OLE/COM (OleView.exe).</span><span class="sxs-lookup"><span data-stu-id="e1209-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="e1209-138">Silně typované prostředích, jako je Office VBA nebo Visual Basic 6.0 přidávání explicitní odkaz na typ knihovny a potom deklarující typ objektu proxy použít místo parametr kontrakt.</span><span class="sxs-lookup"><span data-stu-id="e1209-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="e1209-139">To také poskytuje podporu technologie IntelliSense během vývoje aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="e1209-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="e1209-140">S vytvořená instance proxy s monikeru služby, klientská aplikace můžete volat metody pro proxy server, což vede k volání odpovídající operací služby infrastruktury přezdívka služby.</span><span class="sxs-lookup"><span data-stu-id="e1209-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Při spuštění vzorového odpověď operace se zobrazí v okně Windows Script Host zprávy. Tento příklad ukazuje volání modelu COM pomocí zadaných Přezdívka ke komunikaci s klient COM [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. <span data-ttu-id="e1209-143">Bez ohledu na použití modelu COM v aplikaci klienta komunikace se službou se skládá jenom z volání webové služby.</span><span class="sxs-lookup"><span data-stu-id="e1209-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="e1209-144">Kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="e1209-144">WSDL Contract</span></span>  
 <span data-ttu-id="e1209-145">Používat Přezdívka kontraktu WSDL, není požadována žádná registrace knihovny klienta, ale WSDL kontrakt služby musí být načteny prostřednictvím mechanismus out-of-band například pomocí prohlížeče přístup WSDL koncový bod pro službu.</span><span class="sxs-lookup"><span data-stu-id="e1209-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="e1209-146">Přezdívka můžete poté přistoupit v době provádění tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e1209-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="e1209-147">Klientská aplikace ComCalcClient.vbs používá `FileSystemObject` pro přístup k souboru WSDL místně uložené a pak znovu použije `GetObject` funkce vytvořit proxy server pro službu.</span><span class="sxs-lookup"><span data-stu-id="e1209-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 <span data-ttu-id="e1209-148">Zadejte parametry používané Přezdívka:</span><span class="sxs-lookup"><span data-stu-id="e1209-148">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="e1209-149">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="e1209-149">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="e1209-150">Vazba, který klient musí použít pro připojení k tohoto koncového bodu a obor názvů, ve kterém je definovaný vazbou.</span><span class="sxs-lookup"><span data-stu-id="e1209-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="e1209-151">V takovém případě `wsHttpBinding_ICalculator` se používá.</span><span class="sxs-lookup"><span data-stu-id="e1209-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="e1209-152">WSDL, který definuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="e1209-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="e1209-153">V takovém případě je řetězec, který byl přečten ze souboru serviceWsdl.xml.</span><span class="sxs-lookup"><span data-stu-id="e1209-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
-   <span data-ttu-id="e1209-154">Název a obor názvů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e1209-154">The name and namespace of the contract.</span></span> <span data-ttu-id="e1209-155">Toto identifikační není nutná, protože schématu WSDL může obsahovat více než jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="e1209-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e1209-156">Ve výchozím nastavení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby generovat samostatné soubory WSDL pro každý obor názvů, použití.</span><span class="sxs-lookup"><span data-stu-id="e1209-156">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="e1209-157">Tyto jsou propojeny s použitím konstrukce import schématu WSDL.</span><span class="sxs-lookup"><span data-stu-id="e1209-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="e1209-158">Protože moniker se očekává jenom jednu definici WSDL, službu buď musíte použít jeden obor názvů, jak je předvedeno v této ukázce nebo samostatné soubory je potřeba ručně sloučit.</span><span class="sxs-lookup"><span data-stu-id="e1209-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="e1209-159">S vytvořená instance proxy s monikeru služby, klientská aplikace můžete volat metody pro proxy server, což vede k volání odpovídající operací služby infrastruktury přezdívka služby.</span><span class="sxs-lookup"><span data-stu-id="e1209-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Při spuštění vzorového odpověď operace se zobrazí v okně Windows Script Host zprávy. <span data-ttu-id="e1209-161">Tento příklad ukazuje volání modelu COM pomocí Přezdívka kontraktu WSDL ke komunikaci s klient COM [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="e1209-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="e1209-162">Metadata Exchange kontraktu</span><span class="sxs-lookup"><span data-stu-id="e1209-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="e1209-163">Pokud chcete používat Přezdívka s MEX kontraktu, stejně jako u kontraktů WSDL, není požadována žádná registrace klienta.</span><span class="sxs-lookup"><span data-stu-id="e1209-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="e1209-164">V době provedení prostřednictvím interní použití systému Metadata Exchange se načítají, kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="e1209-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="e1209-165">Klientská aplikace ComCalcClient.vbs znovu používá `GetObject` funkce vytvořit proxy server pro službu.</span><span class="sxs-lookup"><span data-stu-id="e1209-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="e1209-166">Zadejte parametry používané Přezdívka:</span><span class="sxs-lookup"><span data-stu-id="e1209-166">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="e1209-167">Adresa koncového bodu služby metadata exchange.</span><span class="sxs-lookup"><span data-stu-id="e1209-167">The address of the service metadata exchange endpoint.</span></span>  
  
-   <span data-ttu-id="e1209-168">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="e1209-168">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="e1209-169">Vazba, který klient musí použít pro připojení k tohoto koncového bodu a obor názvů, ve kterém je definovaný vazbou.</span><span class="sxs-lookup"><span data-stu-id="e1209-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="e1209-170">V takovém případě `wsHttpBinding_ICalculator` se používá.</span><span class="sxs-lookup"><span data-stu-id="e1209-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="e1209-171">Název a obor názvů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e1209-171">The name and namespace of the contract.</span></span> <span data-ttu-id="e1209-172">Toto identifikační není nutná, protože schématu WSDL může obsahovat více než jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="e1209-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="e1209-173">S vytvořená instance proxy s monikeru služby, klientská aplikace můžete volat metody pro proxy server, což vede k volání odpovídající operací služby infrastruktury přezdívka služby.</span><span class="sxs-lookup"><span data-stu-id="e1209-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Při spuštění vzorového odpověď operace se zobrazí v okně Windows Script Host zprávy. <span data-ttu-id="e1209-175">Tento příklad ukazuje volání modelu COM pomocí Přezdívka kontraktu MEX ke komunikaci s klient COM [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="e1209-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="e1209-176">Jak nastavit a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="e1209-176">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="e1209-177">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1209-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e1209-178">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e1209-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e1209-179">Z [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] příkazový řádek, otevřete složku \client\bin, ve složce konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="e1209-179">From a [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] command prompt, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e1209-180">Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 nebo Windows Server 2008 R2, ujistěte se, spuštění příkazového řádku s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="e1209-180">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="e1209-181">Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` Export knihovny dll tlb souboru.</span><span class="sxs-lookup"><span data-stu-id="e1209-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="e1209-182">"Typ upozornění – Exportér knihovny" je očekávána, ale není problém, protože obecného typu se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="e1209-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5.  <span data-ttu-id="e1209-183">Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` typy zaregistrovat u modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e1209-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="e1209-184">"Typ upozornění – Exportér knihovny" je očekávána, ale není problém, protože obecného typu se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="e1209-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6.  <span data-ttu-id="e1209-185">Zadejte `gacutil.exe /i client.dll` přidat sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="e1209-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="e1209-186">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="e1209-186">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="e1209-187">Test, který jste mají přístup ke službě pomocí prohlížeče zadáním v následující adrese: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="e1209-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="e1209-188">Potvrzovací stránku má být zobrazena v odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e1209-188">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="e1209-189">Spusťte ComCalcClient.vbs z \client získáte složky pro konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="e1209-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="e1209-190">Činnost klienta se zobrazí ve windows pole zpráva.</span><span class="sxs-lookup"><span data-stu-id="e1209-190">Client activity is displayed in message box windows.</span></span>  
  
3.  <span data-ttu-id="e1209-191">Pokud klient a služba není schopen komunikovat, najdete v části [tipy pro řešení potíží s](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="e1209-191">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="e1209-192">Ke spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="e1209-192">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="e1209-193">Na počítači se službou vytvořte virtuální adresář s názvem ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="e1209-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="e1209-194">Skript Setupvroot.bat součástí vzorku lze použít k vytvoření adresáře disk a virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="e1209-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2.  <span data-ttu-id="e1209-195">Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do ServiceModelSamples virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="e1209-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="e1209-196">Nezapomeňte zahrnout soubory v adresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="e1209-196">Be sure to include the files in the \bin directory.</span></span>  
  
3.  <span data-ttu-id="e1209-197">Zkopírujte soubor skriptu klienta ve složce \client ve složce jazyka na klientský počítač.</span><span class="sxs-lookup"><span data-stu-id="e1209-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4.  <span data-ttu-id="e1209-198">V souboru skriptu změňte hodnotu adresu definice koncového bodu tak, aby odpovídala nové adresy vaší služby.</span><span class="sxs-lookup"><span data-stu-id="e1209-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="e1209-199">Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="e1209-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5.  <span data-ttu-id="e1209-200">Zkopírujte soubor WSDL do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="e1209-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="e1209-201">V souboru WSDL serviceWsdl.xml, nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="e1209-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6.  <span data-ttu-id="e1209-202">Kopírování knihovně Client.dll ve složce \client\bin ve složce pro specifický jazyk do jiného adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="e1209-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="e1209-203">Z příkazového řádku přejděte do adresáře cílové v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="e1209-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="e1209-204">Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nezapomeňte příkazový řádek spustit jako správce.</span><span class="sxs-lookup"><span data-stu-id="e1209-204">If using [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], make sure to run the command prompt as Administrator.</span></span>  
  
8.  <span data-ttu-id="e1209-205">Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` Export knihovny dll tlb souboru.</span><span class="sxs-lookup"><span data-stu-id="e1209-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="e1209-206">"Typ upozornění – Exportér knihovny" je očekávána, ale není problém, protože obecného typu se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="e1209-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="e1209-207">Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` typy zaregistrovat u modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e1209-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="e1209-208">Ujistěte se, zda cesta byla nastavena na složku, která obsahuje `regasm.exe` před spuštěním příkazu.</span><span class="sxs-lookup"><span data-stu-id="e1209-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="e1209-209">Zadejte `gacutil.exe /i client.dll` přidat sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="e1209-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="e1209-210">Ujistěte se, zda cesta byla nastavena na složku, která obsahuje `gacutil.exe` před spuštěním příkazu.</span><span class="sxs-lookup"><span data-stu-id="e1209-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="e1209-211">Test službě můžete dostat z klientského počítače pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="e1209-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="e1209-212">Na klientském počítači spusťte ComCalcClient.vbs.</span><span class="sxs-lookup"><span data-stu-id="e1209-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e1209-213">Vyčistěte po vzorku</span><span class="sxs-lookup"><span data-stu-id="e1209-213">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="e1209-214">Z bezpečnostních důvodů odeberte definici virtuální adresář a oprávnění udělená v průběhu instalace, když skončíte s ukázky.</span><span class="sxs-lookup"><span data-stu-id="e1209-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1209-215">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1209-215">See Also</span></span>
