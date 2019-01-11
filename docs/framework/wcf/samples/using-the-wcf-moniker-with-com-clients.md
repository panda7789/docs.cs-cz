---
title: Použití monikeru služby WCF u klientů modelu COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 6e5bb35d0d1d9128ddbc5f7ab4dd81c3bc0f8fbf
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221632"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="9be21-102">Použití monikeru služby WCF u klientů modelu COM</span><span class="sxs-lookup"><span data-stu-id="9be21-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="9be21-103">Tato ukázka demonstruje použití monikeru služby Windows Communication Foundation (WCF) k integraci webové služby do založené na modelu COM. vývojových prostředích, jako je například Microsoft Office Visual Basic for Applications (Office VBA) nebo Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="9be21-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="9be21-104">Tento příklad se skládá z klienta Windows Script Host (VBS), podpůrné klientské knihovny (DLL) a služby knihovny (.dll) hostované v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="9be21-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="9be21-105">Služba je služba kalkulačky a klient modelu COM zavolá matematických operací – přidat, odečítání, násobení a rozdělit – ve službě.</span><span class="sxs-lookup"><span data-stu-id="9be21-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="9be21-106">Činnost klienta je viditelný v ovládacím prvku windows pole zpráv.</span><span class="sxs-lookup"><span data-stu-id="9be21-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9be21-107">Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9be21-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9be21-108">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="9be21-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9be21-109">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9be21-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9be21-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9be21-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9be21-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9be21-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="9be21-112">Implementuje služby `ICalculator` kontrakt definovaný, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="9be21-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="9be21-113">Vzorek ukazuje tři alternativní přístupy k použití monikeru:</span><span class="sxs-lookup"><span data-stu-id="9be21-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
-   <span data-ttu-id="9be21-114">Typu kontraktu – smlouvy je registrován jako typ viditelné modelu COM v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="9be21-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
-   <span data-ttu-id="9be21-115">Smlouva WSDL – smlouvy se dodává ve formě dokument WSDL.</span><span class="sxs-lookup"><span data-stu-id="9be21-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="9be21-116">Kontraktů výměny metadat – smlouvy je načten v době běhu z koncového bodu metadat Exchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="9be21-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="9be21-117">Typu kontraktu</span><span class="sxs-lookup"><span data-stu-id="9be21-117">Typed Contract</span></span>  
 <span data-ttu-id="9be21-118">Používat zástupný název typu kontraktu použití, musí být zaregistrovaný s odpovídajícím způsobem atributy typy pro kontrakt služby s modelu COM.</span><span class="sxs-lookup"><span data-stu-id="9be21-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="9be21-119">Klient nejprve musí být generovány pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9be21-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="9be21-120">Spusťte následující příkaz z příkazového řádku v adresáři klienta ke generování typové proxy.</span><span class="sxs-lookup"><span data-stu-id="9be21-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="9be21-121">Tato třída musí být součástí projektu a projekt by měl být nakonfigurovaný pro generování viditelný modulem COM, podepsané sestavení při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="9be21-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="9be21-122">Tento atribut by měl být zahrnuty v souboru AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="9be21-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="9be21-123">Po vytvoření projektu, zaregistrujte typ viditelný modulem COM s použitím `regasm` jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9be21-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="9be21-124">Sestavení, který je vytvořen, měli byste přidat do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="9be21-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="9be21-125">I když není nezbytně nutné, tato funkce zjednodušuje proces hledání sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9be21-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="9be21-126">Následující příkaz přidá sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="9be21-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  <span data-ttu-id="9be21-127">Moniker služby vyžaduje pouze registrace typu a nepoužívá ke komunikaci se službou proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="9be21-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="9be21-128">ComCalcClient.vbs klientská aplikace používá `GetObject` funkce proxy serveru pro službu, pomocí syntaxe moniker služby zadáním adresy, vazby, sestavit a kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="9be21-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="9be21-129">Zadejte parametry používané zástupný název:</span><span class="sxs-lookup"><span data-stu-id="9be21-129">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="9be21-130">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="9be21-130">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="9be21-131">Vazby, který klient musí použít pro připojení pomocí tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9be21-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="9be21-132">V takovém případě wsHttpBinding definované v systému se používá, i když je možné definovat vlastní vazby v konfiguračních souborů klienta.</span><span class="sxs-lookup"><span data-stu-id="9be21-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="9be21-133">Pro použití s Windows Script Host je vlastní vazby definované v souboru Cscript.exe.config ve stejném adresáři jako Cscript.exe.</span><span class="sxs-lookup"><span data-stu-id="9be21-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
-   <span data-ttu-id="9be21-134">Typ smlouvy, která je podporována v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="9be21-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="9be21-135">Jedná se o typ, který byl generován a zaregistrován výše.</span><span class="sxs-lookup"><span data-stu-id="9be21-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="9be21-136">Vzhledem k tomu, že skript jazyka Visual Basic neposkytuje prostředí modelu COM silného typu, je třeba zadat identifikátor pro kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9be21-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="9be21-137">Tento identifikátor GUID je `interfaceID` z CalcProxy.tlb, které lze zobrazit pomocí nástroje modelu COM, jako je například prohlížeč objektů OLE/COM (OleView.exe).</span><span class="sxs-lookup"><span data-stu-id="9be21-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="9be21-138">Silný prostředích, jako například Office VBA nebo Visual Basic 6.0 přidat explicitní odkaz na knihovnu typů a pak deklarační typ objektu proxy použít místo parametru kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9be21-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="9be21-139">To také poskytuje podporu technologie IntelliSense při vývoji klientských aplikací.</span><span class="sxs-lookup"><span data-stu-id="9be21-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="9be21-140">Instance proxy s monikeru služby s vytvořen, klientská aplikace může volat metody na proxy serveru, což vede k infrastruktuře moniker služby volání odpovídající operace služby.</span><span class="sxs-lookup"><span data-stu-id="9be21-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Při spuštění ukázky v reakci na operaci se zobrazí v okně Windows Script Host zprávy. Tento příklad ukazuje klient modelu COM, volání modelu COM pomocí zadaný moniker komunikovat se službou WCF. <span data-ttu-id="9be21-143">Komunikace se službou se skládá pouze z volání webové služby bez ohledu na použití modelu COM v klientské aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9be21-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="9be21-144">Kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="9be21-144">WSDL Contract</span></span>  
 <span data-ttu-id="9be21-145">Používat zástupný název kontraktu WSDL, není požadována žádná registrace knihovny klienta ale WSDL kontrakt služby musí být načten mechanismem out-of-band jako je například přístup ke koncovému bodu WSDL pro službu pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="9be21-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="9be21-146">Zástupný název mohlo dostat přístup k této smlouvy v době spuštění.</span><span class="sxs-lookup"><span data-stu-id="9be21-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="9be21-147">Klientská aplikace ComCalcClient.vbs používá `FileSystemObject` pro přístup k místně uloženého souboru WSDL a pak znovu použije `GetObject` funkce k vytvoření proxy serveru pro službu.</span><span class="sxs-lookup"><span data-stu-id="9be21-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
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
  
 <span data-ttu-id="9be21-148">Zadejte parametry používané zástupný název:</span><span class="sxs-lookup"><span data-stu-id="9be21-148">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="9be21-149">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="9be21-149">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="9be21-150">Vazby, který klient musí použít pro připojení pomocí tohoto koncového bodu a obor názvů, ve kterém je definován, že vazba.</span><span class="sxs-lookup"><span data-stu-id="9be21-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="9be21-151">V takovém případě `wsHttpBinding_ICalculator` se používá.</span><span class="sxs-lookup"><span data-stu-id="9be21-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="9be21-152">WSDL, který definuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9be21-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="9be21-153">V tomto případě je řetězec, který byl přečten ze souboru serviceWsdl.xml.</span><span class="sxs-lookup"><span data-stu-id="9be21-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
-   <span data-ttu-id="9be21-154">Název a obor názvů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9be21-154">The name and namespace of the contract.</span></span> <span data-ttu-id="9be21-155">Tato identifikace totiž jazyka WSDL může obsahovat více než jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9be21-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9be21-156">Ve výchozím nastavení, služby WCF generovat samostatné soubory WSDL pro každý obor názvů, který používá.</span><span class="sxs-lookup"><span data-stu-id="9be21-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="9be21-157">Tyto jsou propojeny s použitím konstrukce importu WSDL.</span><span class="sxs-lookup"><span data-stu-id="9be21-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="9be21-158">Protože je moniker očekává jenom jednu definici WSDL, službu buď musí používat jednoho oboru názvů, jak je ukázáno v tomto příkladu nebo samostatné soubory je potřeba sloučit ručně.</span><span class="sxs-lookup"><span data-stu-id="9be21-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="9be21-159">Instance proxy s monikeru služby s vytvořen, klientská aplikace může volat metody na proxy serveru, což vede k infrastruktuře moniker služby volání odpovídající operace služby.</span><span class="sxs-lookup"><span data-stu-id="9be21-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Při spuštění ukázky v reakci na operaci se zobrazí v okně Windows Script Host zprávy. <span data-ttu-id="9be21-161">Tento příklad ukazuje klient modelu COM, volání COM použití monikeru u kontraktů WSDL komunikovat se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="9be21-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="9be21-162">Kontraktů Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="9be21-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="9be21-163">Pokud chcete použít zástupný název s kontraktem MEX, stejně jako u kontraktů WSDL, není požadována žádná registrace klienta.</span><span class="sxs-lookup"><span data-stu-id="9be21-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="9be21-164">Kontrakt služby je načten v době provádění prostřednictvím interní použití výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="9be21-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="9be21-165">Klientská aplikace ComCalcClient.vbs znovu používá `GetObject` funkce k vytvoření proxy serveru pro službu.</span><span class="sxs-lookup"><span data-stu-id="9be21-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="9be21-166">Zadejte parametry používané zástupný název:</span><span class="sxs-lookup"><span data-stu-id="9be21-166">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="9be21-167">Adresa koncového bodu služby metadata exchange.</span><span class="sxs-lookup"><span data-stu-id="9be21-167">The address of the service metadata exchange endpoint.</span></span>  
  
-   <span data-ttu-id="9be21-168">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="9be21-168">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="9be21-169">Vazby, který klient musí použít pro připojení pomocí tohoto koncového bodu a obor názvů, ve kterém je definován, že vazba.</span><span class="sxs-lookup"><span data-stu-id="9be21-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="9be21-170">V takovém případě `wsHttpBinding_ICalculator` se používá.</span><span class="sxs-lookup"><span data-stu-id="9be21-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="9be21-171">Název a obor názvů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9be21-171">The name and namespace of the contract.</span></span> <span data-ttu-id="9be21-172">Tato identifikace totiž jazyka WSDL může obsahovat více než jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="9be21-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="9be21-173">Instance proxy s monikeru služby s vytvořen, klientská aplikace může volat metody na proxy serveru, což vede k infrastruktuře moniker služby volání odpovídající operace služby.</span><span class="sxs-lookup"><span data-stu-id="9be21-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Při spuštění ukázky v reakci na operaci se zobrazí v okně Windows Script Host zprávy. <span data-ttu-id="9be21-175">Tento příklad ukazuje klient modelu COM, volání COM použití monikeru s kontraktem MEX komunikovat se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="9be21-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="9be21-176">K nastavení a sestavit ukázku</span><span class="sxs-lookup"><span data-stu-id="9be21-176">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="9be21-177">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9be21-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9be21-178">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9be21-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9be21-179">Z příkazový řádek vývojáře pro sadu Visual Studio, otevřete složku \client\bin, v rámci složky specifické pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="9be21-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9be21-180">Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 nebo Windows Server 2008 R2, ujistěte se, že spustit příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="9be21-180">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="9be21-181">Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` Export knihovny dll do souboru tlb.</span><span class="sxs-lookup"><span data-stu-id="9be21-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="9be21-182">"Zadejte upozornění exportéru knihovny typů" očekává se, ale není problém, protože obecného typu se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="9be21-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5.  <span data-ttu-id="9be21-183">Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` k registraci typů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="9be21-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="9be21-184">"Zadejte upozornění exportéru knihovny typů" očekává se, ale není problém, protože obecného typu se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="9be21-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6.  <span data-ttu-id="9be21-185">Zadejte `gacutil.exe /i client.dll` přidat sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="9be21-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="9be21-186">Ke spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="9be21-186">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="9be21-187">Test, který můžete přístup ke službě pomocí prohlížeče tak, že zadáte tuto adresu: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="9be21-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="9be21-188">Stránka s potvrzením má být zobrazena v odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9be21-188">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="9be21-189">Spusťte ComCalcClient.vbs z \client ze složky specifické pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="9be21-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="9be21-190">Činnost klienta se zobrazí v poli zpráv – windows.</span><span class="sxs-lookup"><span data-stu-id="9be21-190">Client activity is displayed in message box windows.</span></span>  
  
3.  <span data-ttu-id="9be21-191">Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy k řešení potíží s](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="9be21-191">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="9be21-192">Ke spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="9be21-192">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="9be21-193">Na počítači se službou vytvořte virtuální adresář s názvem ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="9be21-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="9be21-194">Setupvroot.bat skript dodaný s ukázkou je možné vytvořit na disku a virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9be21-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2.  <span data-ttu-id="9be21-195">Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do ServiceModelSamples virtuálního adresáře na počítači se službou.</span><span class="sxs-lookup"><span data-stu-id="9be21-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="9be21-196">Nezapomeňte zahrnout soubory v adresáři \bin.</span><span class="sxs-lookup"><span data-stu-id="9be21-196">Be sure to include the files in the \bin directory.</span></span>  
  
3.  <span data-ttu-id="9be21-197">Zkopírujte instalační soubor klienta skriptu ze složky \client v rámci složky specifické pro jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="9be21-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4.  <span data-ttu-id="9be21-198">V souboru skriptu změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adresu služby.</span><span class="sxs-lookup"><span data-stu-id="9be21-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="9be21-199">Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="9be21-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5.  <span data-ttu-id="9be21-200">Zkopírujte soubor WSDL na klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="9be21-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="9be21-201">V souboru WSDL serviceWsdl.xml, nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="9be21-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6.  <span data-ttu-id="9be21-202">Zkopírujte Client.dll knihovny ze složky \client\bin v rámci složky specifické pro jazyk do adresáře na klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="9be21-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="9be21-203">Z příkazového řádku přejděte do této cílové složky v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="9be21-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="9be21-204">Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], ujistěte se, že příkazový řádek spustit jako správce.</span><span class="sxs-lookup"><span data-stu-id="9be21-204">If using [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], make sure to run the command prompt as Administrator.</span></span>  
  
8.  <span data-ttu-id="9be21-205">Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` Export knihovny dll do souboru tlb.</span><span class="sxs-lookup"><span data-stu-id="9be21-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="9be21-206">"Zadejte upozornění exportéru knihovny typů" očekává se, ale není problém, protože obecného typu se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="9be21-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="9be21-207">Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` k registraci typů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="9be21-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="9be21-208">Zajištění byla nastavena tato cesta ke složce, která obsahuje `regasm.exe` před spuštěním příkazu.</span><span class="sxs-lookup"><span data-stu-id="9be21-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="9be21-209">Zadejte `gacutil.exe /i client.dll` přidat sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="9be21-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="9be21-210">Zajištění byla nastavena tato cesta ke složce, která obsahuje `gacutil.exe` před spuštěním příkazu.</span><span class="sxs-lookup"><span data-stu-id="9be21-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="9be21-211">Testovací službě můžete dostat z klientského počítače pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="9be21-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="9be21-212">Na klientském počítači spusťte ComCalcClient.vbs.</span><span class="sxs-lookup"><span data-stu-id="9be21-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="9be21-213">K vyčištění po vzorku</span><span class="sxs-lookup"><span data-stu-id="9be21-213">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="9be21-214">Z bezpečnostních důvodů odstranit definici virtuální adresář a oprávnění udělené v kroků instalace, až budete hotovi s ukázkami.</span><span class="sxs-lookup"><span data-stu-id="9be21-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be21-215">Viz také</span><span class="sxs-lookup"><span data-stu-id="9be21-215">See Also</span></span>
