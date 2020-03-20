---
title: Použití monikeru služby WCF u klientů modelu COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: d4d812c59a504f365eb3ad63ddd45ba5a66296e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183238"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="2d8e3-102">Použití monikeru služby WCF u klientů modelu COM</span><span class="sxs-lookup"><span data-stu-id="2d8e3-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="2d8e3-103">Tato ukázka ukazuje, jak používat zástupný název služby WCF (Windows Communication Foundation) k integraci webových služeb do vývojových prostředí založených na modelu COM, jako je například Microsoft Office Visual Basic for Applications (Office VBA) nebo Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="2d8e3-104">Tato ukázka se skládá z klienta Hostitele skriptů systému Windows (.vbs), podpůrné klientské knihovny (.dll) a knihovny služeb (.dll) hostované Internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="2d8e3-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="2d8e3-105">Služba je služba kalkulačky a klient COM volá matematické operace – Přidat, Odečíst, Násobit a Rozdělit – ve službě.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="2d8e3-106">Aktivita klienta je viditelná v oknech okna okna okna se zprávou.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d8e3-107">Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2d8e3-108">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2d8e3-109">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2d8e3-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2d8e3-111">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="2d8e3-112">Služba implementuje `ICalculator` smlouvu definovanou, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="2d8e3-113">Ukázka ukazuje tři alternativní přístupy pro použití zástupný název:</span><span class="sxs-lookup"><span data-stu-id="2d8e3-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="2d8e3-114">Zadaný kontrakt – Smlouva je registrována jako viditelný typ com v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="2d8e3-115">WSDL smlouva – Smlouva je dodávána ve formě dokumentu WSDL.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="2d8e3-116">Kontrakt výměny metadat – Kontrakt je načten za běhu z koncového bodu Výměny metadat (MEX).</span><span class="sxs-lookup"><span data-stu-id="2d8e3-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="2d8e3-117">Zadaný kontrakt</span><span class="sxs-lookup"><span data-stu-id="2d8e3-117">Typed Contract</span></span>  
 <span data-ttu-id="2d8e3-118">Chcete-li použít zástupný název s typem smlouvy použití, vhodně přiřazené typy pro servisní smlouvu musí být registrovány com.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="2d8e3-119">Nejprve musí být klient vygenerován pomocí [nástroje ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="2d8e3-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="2d8e3-120">Spusťte následující příkaz z příkazového řádku v adresáři klienta a vygenerujte zadaný proxy server.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="2d8e3-121">Tato třída musí být zahrnuta do projektu a projekt by měl být nakonfigurován tak, aby při kompilaci generoval podepsané sestavení viditelné pro COM.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="2d8e3-122">Následující atribut by měl být zahrnut do souboru AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="2d8e3-123">Po sestavení projektu zaregistrujte typy viditelné `regasm` com pomocí, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="2d8e3-124">Sestavení, které je vytvořeno by měl být přidán do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="2d8e3-125">I když to není nezbytně nutné, zjednodušuje proces hledání sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="2d8e3-126">Následující příkaz přidá sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> <span data-ttu-id="2d8e3-127">Zástupné řešení služby vyžaduje pouze registraci typu a nepoužívá proxy server ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="2d8e3-128">Klientská aplikace ComCalcClient.vbs používá `GetObject` tuto funkci k vytvoření proxy serveru pro službu pomocí syntaxe zástupného prvku služby k určení adresy, vazby a smlouvy pro službu.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="2d8e3-129">Parametry použité zástupný název určit:</span><span class="sxs-lookup"><span data-stu-id="2d8e3-129">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="2d8e3-130">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-130">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="2d8e3-131">Vazba, kterou by měl klient použít k připojení k tomuto koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="2d8e3-132">V tomto případě se používá systémově definovaná wsHttpBinding i když vlastní vazby lze definovat v konfiguračních souborech klienta.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="2d8e3-133">Pro použití s hostitelem skriptů systému Windows je vlastní vazba definována v souboru Cscript.exe.config ve stejném adresáři jako Cscript.exe.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="2d8e3-134">Typ smlouvy, která je podporována v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="2d8e3-135">Toto je typ, který byl vygenerován a registrován výše.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="2d8e3-136">Vzhledem k tomu, že skript jazyka visual basic neposkytuje prostředí COM silného typu, musí být zadán identifikátor smlouvy.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="2d8e3-137">Tento identifikátor GUID je `interfaceID` z CalcProxy.tlb, který lze zobrazit pomocí nástrojů COM, jako je například PROHLÍŽEČ OBJEKTŮ OLE/COM (OleView.exe).</span><span class="sxs-lookup"><span data-stu-id="2d8e3-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="2d8e3-138">Pro prostředí silného typu, jako je například Office VBA nebo Visual Basic 6.0, přidání explicitní odkaz na knihovnu typů a pak deklarovat typ proxy objektu lze použít místo parametru smlouvy.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="2d8e3-139">To také poskytuje podporu IntelliSense během vývoje klientských aplikací.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="2d8e3-140">Po vytvoření instance proxy s zástupným serverem služby může klientská aplikace volat metody na serveru proxy, což vede k tomu, že infrastruktura zástupných spoje služby volá odpovídající operace služby.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Při spuštění ukázky se odpověď operace zobrazí v okně okna se zprávou Hostitele skriptů systému Windows. To ukazuje klienta modelu COM volání modelu COM pomocí zástupný název zadali ke komunikaci se službou WCF. <span data-ttu-id="2d8e3-143">I přes použití com v klientské aplikaci, komunikace se službou se skládá pouze z volání webové služby.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="2d8e3-144">WSDL smlouva</span><span class="sxs-lookup"><span data-stu-id="2d8e3-144">WSDL Contract</span></span>  
 <span data-ttu-id="2d8e3-145">Chcete-li použít zástupný název se smlouvou WSDL, není vyžadována žádná registrace knihovny klienta, ale wsdl smlouvy pro službu musí být načteny prostřednictvím mechanismu out-of-band, jako je například použití prohlížeče pro přístup ke koncovému bodu WSDL pro službu.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="2d8e3-146">Zástupné název pak přístup k této smlouvy v době provádění.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="2d8e3-147">Klientská aplikace ComCalcClient.vbs `FileSystemObject` používá přístup k místně uloženému souboru `GetObject` WSDL a poté znovu používá funkci k vytvoření proxy serveru pro službu.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
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
  
 <span data-ttu-id="2d8e3-148">Parametry použité zástupný název určit:</span><span class="sxs-lookup"><span data-stu-id="2d8e3-148">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="2d8e3-149">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-149">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="2d8e3-150">Vazba, kterou by měl klient použít k připojení k tomuto koncovému bodu a oboru názvů, ve kterém je tato vazba definována.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="2d8e3-151">V tomto případě `wsHttpBinding_ICalculator` se používá.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="2d8e3-152">WSDL, který definuje smlouvy.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="2d8e3-153">V tomto případě se jedná o řetězec, který byl přečten ze souboru serviceWsdl.xml.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="2d8e3-154">Název a obor názvů smlouvy.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-154">The name and namespace of the contract.</span></span> <span data-ttu-id="2d8e3-155">Tato identifikace je vyžadována, protože WSDL může obsahovat více než jednu smlouvu.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2d8e3-156">Ve výchozím nastavení služby WCF generují samostatné soubory WSDL pro každý obor názvů, který používá.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="2d8e3-157">Ty jsou spojeny s použitím wsdl import konstrukce.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="2d8e3-158">Vzhledem k tomu, že zástupný název očekává jednu definici WSDL, musí služba buď použít jeden obor názvů, jak je znázorněno v této ukázce, nebo samostatné soubory musí být ručně sloučeny.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="2d8e3-159">Po vytvoření instance proxy s zástupným serverem služby může klientská aplikace volat metody na serveru proxy, což vede k tomu, že infrastruktura zástupných spoje služby volá odpovídající operace služby.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Při spuštění ukázky se odpověď operace zobrazí v okně okna se zprávou Hostitele skriptů systému Windows. <span data-ttu-id="2d8e3-161">To ukazuje klienta MODELU COM volání modelu COM pomocí zástupný název se smlouvou WSDL pro komunikaci se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="2d8e3-162">Smlouva o výměně metadat</span><span class="sxs-lookup"><span data-stu-id="2d8e3-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="2d8e3-163">Chcete-li použít zástupný název se smlouvou MEX, jako u smlouvy WSDL, není vyžadována žádná registrace klienta.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="2d8e3-164">Smlouva pro službu je načtena v době spuštění prostřednictvím interního použití výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="2d8e3-165">Klientská aplikace ComCalcClient.vbs `GetObject` opět používá tuto funkci k vytvoření proxy serveru pro službu.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="2d8e3-166">Parametry použité zástupný název určit:</span><span class="sxs-lookup"><span data-stu-id="2d8e3-166">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="2d8e3-167">Adresa koncového bodu výměny metadat služby.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-167">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="2d8e3-168">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-168">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="2d8e3-169">Vazba, kterou by měl klient použít k připojení k tomuto koncovému bodu a oboru názvů, ve kterém je tato vazba definována.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="2d8e3-170">V tomto případě `wsHttpBinding_ICalculator` se používá.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="2d8e3-171">Název a obor názvů smlouvy.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-171">The name and namespace of the contract.</span></span> <span data-ttu-id="2d8e3-172">Tato identifikace je vyžadována, protože WSDL může obsahovat více než jednu smlouvu.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="2d8e3-173">Po vytvoření instance proxy s zástupným serverem služby může klientská aplikace volat metody na serveru proxy, což vede k tomu, že infrastruktura zástupných spoje služby volá odpovídající operace služby.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Při spuštění ukázky se odpověď operace zobrazí v okně okna se zprávou Hostitele skriptů systému Windows. <span data-ttu-id="2d8e3-175">To ukazuje klienta modelu COM volání modelu COM pomocí zástupný název se smlouvou MEX pro komunikaci se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="2d8e3-176">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="2d8e3-176">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="2d8e3-177">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d8e3-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2d8e3-178">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2d8e3-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="2d8e3-179">Na příkazovém řádku pro vývojáře sady Visual Studio otevřete složku \client\bin pod složkou specifickou pro daný jazyk.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2d8e3-180">Používáte-li systém Windows Vista, Windows Server 2008, Windows 7 nebo Windows Server 2008 R2, zkontrolujte, zda je spuštěn příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-180">If you are using Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="2d8e3-181">Zadáním `tlbexp.exe client.dll /out:CalcProxy.tlb` zadejte, chcete-li exportovat dll do souboru tlb.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="2d8e3-182">"Upozornění vývozce knihovny typů" se očekává, ale není problém, protože obecný typ není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="2d8e3-183">Zadáním `regasm.exe /tlb:CalcProxy.tlb client.dll` zadejte, chcete-li zaregistrovat typy pomocí com.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="2d8e3-184">"Upozornění vývozce knihovny typů" se očekává, ale není problém, protože obecný typ není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="2d8e3-185">Zadáním `gacutil.exe /i client.dll` do pole přidáte sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="2d8e3-186">Spuštění ukázky ve stejném počítači</span><span class="sxs-lookup"><span data-stu-id="2d8e3-186">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="2d8e3-187">Otestujte, zda máte ke službě přístup pomocí prohlížeče, zadáním následující adresy: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="2d8e3-188">V reakci na to by měla být zobrazena stránka s potvrzením.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-188">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="2d8e3-189">Spusťte soubor ComCalcClient.vbs z \client z pod složky specifické pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="2d8e3-190">Aktivita klienta se zobrazí v oknech okna okna okna se zprávou.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-190">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="2d8e3-191">Pokud klient a služba nejsou schopni komunikovat, naleznete [v tématu Tipy pro řešení potíží pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2d8e3-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="2d8e3-192">Spuštění ukázky v počítačích</span><span class="sxs-lookup"><span data-stu-id="2d8e3-192">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="2d8e3-193">V počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="2d8e3-194">Skript Setupvroot.bat, který je součástí ukázky, lze použít k vytvoření adresáře disku a virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="2d8e3-195">Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do virtuálního adresáře ServiceModelSamples v počítači služby.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="2d8e3-196">Nezapomeňte zahrnout soubory do adresáře \bin.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-196">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="2d8e3-197">Zkopírujte soubor klientského skriptu ze složky \client pod složkou specifickou pro daný jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="2d8e3-198">V souboru skriptu změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese služby.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="2d8e3-199">Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="2d8e3-200">Zkopírujte soubor WSDL do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="2d8e3-201">V souboru WSDL serviceWsdl.xml nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="2d8e3-202">Zkopírujte knihovnu Client.dll ze složky \client\bin pod stolicí specifickou pro daný jazyk do adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="2d8e3-203">Z příkazového řádku přejděte do cílového adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="2d8e3-204">Pokud používáte systém Windows Vista nebo Windows Server 2008, nezapomeňte spustit příkazový řádek jako správce.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-204">If using Windows Vista or Windows Server 2008, make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="2d8e3-205">Zadáním `tlbexp.exe client.dll /out:CalcProxy.tlb` zadejte, chcete-li exportovat dll do souboru tlb.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="2d8e3-206">"Upozornění vývozce knihovny typů" se očekává, ale není problém, protože obecný typ není vyžadován.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="2d8e3-207">Zadáním `regasm.exe /tlb:CalcProxy.tlb client.dll` zadejte, chcete-li zaregistrovat typy pomocí com.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="2d8e3-208">Před spuštěním příkazu se ujistěte, že cesta byla nastavena na složku, která obsahuje. `regasm.exe`</span><span class="sxs-lookup"><span data-stu-id="2d8e3-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="2d8e3-209">Zadáním `gacutil.exe /i client.dll` do pole přidáte sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="2d8e3-210">Před spuštěním příkazu se ujistěte, že cesta byla nastavena na složku, která obsahuje. `gacutil.exe`</span><span class="sxs-lookup"><span data-stu-id="2d8e3-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="2d8e3-211">Otestujte, zda máte přístup ke službě z klientského počítače pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="2d8e3-212">V klientském počítači spusťte soubor ComCalcClient.vbs.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="2d8e3-213">Chcete-li vyčistit po vzorku</span><span class="sxs-lookup"><span data-stu-id="2d8e3-213">To clean up after the sample</span></span>  
  
- <span data-ttu-id="2d8e3-214">Z bezpečnostních důvodů odeberte definici virtuálního adresáře a oprávnění udělená v krocích nastavení po dokončení ukázek.</span><span class="sxs-lookup"><span data-stu-id="2d8e3-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
