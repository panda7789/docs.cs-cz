---
title: Použití monikeru služby WCF u klientů modelu COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 281921bf42910086b874194cb2d8b56fbf71e671
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544706"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="000ac-102">Použití monikeru služby WCF u klientů modelu COM</span><span class="sxs-lookup"><span data-stu-id="000ac-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="000ac-103">Tato ukázka předvádí, jak použít moniker služby Windows Communication Foundation (WCF) k integraci webových služeb do vývojových prostředí založených na modelu COM, jako je například systém Microsoft Office jazyk Visual Basic for Application (Office VBA) nebo Visual Basic 6,0.</span><span class="sxs-lookup"><span data-stu-id="000ac-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="000ac-104">Tato ukázka se skládá z klienta Windows Script Host (. vbs), podpůrné klientské knihovny (. dll) a knihovny služeb (. dll) hostované službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="000ac-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="000ac-105">Služba je služba kalkulačky a klient modelu COM volá matematické operace – přidat, odečíst, vynásobit a rozdělit – u služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="000ac-106">Aktivita klienta se zobrazí v okně se zprávou okna.</span><span class="sxs-lookup"><span data-stu-id="000ac-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="000ac-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="000ac-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="000ac-108">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="000ac-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="000ac-109">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="000ac-109">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="000ac-110">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="000ac-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="000ac-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="000ac-111">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="000ac-112">Služba implementuje kontrakt `ICalculator`, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="000ac-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="000ac-113">Ukázka předvádí tři alternativní přístupy k použití monikeru:</span><span class="sxs-lookup"><span data-stu-id="000ac-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="000ac-114">Typ kontraktu – kontrakt se na klientském počítači zaregistruje jako viditelný typ modelu COM.</span><span class="sxs-lookup"><span data-stu-id="000ac-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="000ac-115">Smlouva WSDL – smlouva je dodávána ve formě dokumentu WSDL.</span><span class="sxs-lookup"><span data-stu-id="000ac-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="000ac-116">Smlouva o výměně metadat – smlouva se načte za běhu z koncového bodu výměny metadat (MEX).</span><span class="sxs-lookup"><span data-stu-id="000ac-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="000ac-117">Zadaný kontrakt</span><span class="sxs-lookup"><span data-stu-id="000ac-117">Typed Contract</span></span>  
 <span data-ttu-id="000ac-118">Aby bylo možné použít moniker se zadaným typem kontraktu, musí být odpovídající typy pro kontrakt služby zaregistrované v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="000ac-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="000ac-119">Nejdřív je potřeba, aby se klient vygeneroval pomocí [Nástroje pro použití metadat ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="000ac-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="000ac-120">Spusťte následující příkaz z příkazového řádku v adresáři klienta pro vygenerování typovaného proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="000ac-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="000ac-121">Tato třída musí být zahrnutá v projektu a projekt by měl být nakonfigurovaný tak, aby při kompilaci generoval podepsané sestavení viditelné pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="000ac-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="000ac-122">Do souboru AssemblyInfo.cs by měl být zahrnut následující atribut.</span><span class="sxs-lookup"><span data-stu-id="000ac-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="000ac-123">Po sestavení projektu Zaregistrujte typy viditelné modelem COM pomocí `regasm`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="000ac-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="000ac-124">Sestavení, které je vytvořeno, by mělo být přidáno do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="000ac-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="000ac-125">I když není nezbytně nutné, zjednodušuje proces, který vyhledává sestavení.</span><span class="sxs-lookup"><span data-stu-id="000ac-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="000ac-126">Následující příkaz přidá sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="000ac-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> <span data-ttu-id="000ac-127">Moniker služby vyžaduje jenom registraci typu a nepoužívá proxy ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="000ac-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="000ac-128">Klientská aplikace ComCalcClient. vbs používá funkci `GetObject` k vytvoření proxy serveru pro službu pomocí syntaxe monikeru služby k určení adresy, vazby a kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="000ac-129">Parametry používané monikerem určují:</span><span class="sxs-lookup"><span data-stu-id="000ac-129">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="000ac-130">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-130">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="000ac-131">Vazba, kterou by měl klient použít pro připojení k tomuto koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="000ac-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="000ac-132">V takovém případě se používá systém wsHttpBinding definovaný i v případě, že vlastní vazby lze definovat v konfiguračních souborech klienta.</span><span class="sxs-lookup"><span data-stu-id="000ac-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="000ac-133">Pro použití s modulem Windows Script Host je vlastní vazba definovaná v souboru Cscript. exe. config ve stejném adresáři jako Cscript. exe.</span><span class="sxs-lookup"><span data-stu-id="000ac-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="000ac-134">Typ kontraktu, který je podporován na koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="000ac-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="000ac-135">Toto je typ, který se vygeneroval a zaregistroval výše.</span><span class="sxs-lookup"><span data-stu-id="000ac-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="000ac-136">Protože Visual Basic skript neposkytuje prostředí COM silného typu, musí být zadán identifikátor pro kontrakt.</span><span class="sxs-lookup"><span data-stu-id="000ac-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="000ac-137">Identifikátor GUID je `interfaceID` z CalcProxy. tlb, kterou lze zobrazit pomocí nástrojů modelu COM, jako je například prohlížeč objektů OLE/COM (OleView. exe).</span><span class="sxs-lookup"><span data-stu-id="000ac-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="000ac-138">Pro prostředí se silnými typy, jako je například Office VBA nebo Visual Basic 6,0, se do knihovny typů přidá explicitní odkaz a potom se dá deklarovat typ objektu proxy místo parametru kontraktu.</span><span class="sxs-lookup"><span data-stu-id="000ac-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="000ac-139">Tato funkce také poskytuje podporu technologie IntelliSense během vývoje klientských aplikací.</span><span class="sxs-lookup"><span data-stu-id="000ac-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="000ac-140">Po sestavení instance proxy k monikeru služby může klientská aplikace volat metody na proxy serveru, což vede k tomu, že infrastruktura monikeru služby volá odpovídající operace služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Při spuštění ukázky se odpověď na operaci zobrazí v okně se zprávou hostitele Windows Script Host. To ukazuje klientovi modelu COM, který provádí volání COM pomocí typového monikeru ke komunikaci se službou WCF. <span data-ttu-id="000ac-143">Bez ohledu na použití modelu COM v klientské aplikaci se komunikace se službou skládá pouze z volání webové služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="000ac-144">Kontrakt WSDL</span><span class="sxs-lookup"><span data-stu-id="000ac-144">WSDL Contract</span></span>  
 <span data-ttu-id="000ac-145">Chcete-li použít moniker se smlouvou WSDL, není vyžadována registrace klientské knihovny, ale kontrakt WSDL pro službu musí být načten pomocí mechanismu mimo IP síť, jako je například použití prohlížeče pro přístup ke koncovému bodu WSDL pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="000ac-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="000ac-146">Moniker pak může k této smlouvě přistupovat v době spuštění.</span><span class="sxs-lookup"><span data-stu-id="000ac-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="000ac-147">Klientská aplikace ComCalcClient. vbs používá `FileSystemObject` k přístupu k místně uloženému souboru WSDL a potom znovu používá funkci `GetObject` k vytvoření proxy pro službu.</span><span class="sxs-lookup"><span data-stu-id="000ac-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
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
  
 <span data-ttu-id="000ac-148">Parametry používané monikerem určují:</span><span class="sxs-lookup"><span data-stu-id="000ac-148">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="000ac-149">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-149">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="000ac-150">Vazba, kterou by měl klient použít pro připojení k tomuto koncovému bodu, a obor názvů, ve kterém je tato vazba definovaná.</span><span class="sxs-lookup"><span data-stu-id="000ac-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="000ac-151">V tomto případě se používá `wsHttpBinding_ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="000ac-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="000ac-152">WSDL, který definuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="000ac-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="000ac-153">V tomto případě se jedná o řetězec, který byl načten ze souboru serviceWsdl. XML.</span><span class="sxs-lookup"><span data-stu-id="000ac-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="000ac-154">Název a obor názvů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="000ac-154">The name and namespace of the contract.</span></span> <span data-ttu-id="000ac-155">Tato identifikace je povinná, protože WSDL může obsahovat více než jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="000ac-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="000ac-156">Ve výchozím nastavení generují služby WCF samostatné soubory WSDL pro každý obor názvů, který používá.</span><span class="sxs-lookup"><span data-stu-id="000ac-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="000ac-157">Tyto prvky jsou propojeny s použitím importované konstrukce WSDL.</span><span class="sxs-lookup"><span data-stu-id="000ac-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="000ac-158">Vzhledem k tomu, že moniker očekává jednu definici WSDL, služba musí buď použít jeden obor názvů, jak je znázorněno v této ukázce, nebo samostatné soubory musí být ručně sloučeny.</span><span class="sxs-lookup"><span data-stu-id="000ac-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="000ac-159">Po sestavení instance proxy k monikeru služby může klientská aplikace volat metody na proxy serveru, což vede k tomu, že infrastruktura monikeru služby volá odpovídající operace služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Při spuštění ukázky se odpověď na operaci zobrazí v okně se zprávou hostitele Windows Script Host. <span data-ttu-id="000ac-161">To ukazuje klientovi modelu COM, který provádí volání COM pomocí monikeru s kontraktem WSDL ke komunikaci se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="000ac-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="000ac-162">Kontrakt pro výměnu metadat</span><span class="sxs-lookup"><span data-stu-id="000ac-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="000ac-163">Chcete-li použít moniker se smlouvou MEX, stejně jako u kontraktu WSDL, není vyžadována registrace klienta.</span><span class="sxs-lookup"><span data-stu-id="000ac-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="000ac-164">Smlouva pro službu je načtena v době provádění prostřednictvím interního použití výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="000ac-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="000ac-165">Klientská aplikace ComCalcClient. vbs znovu používá funkci `GetObject` k vytvoření proxy serveru pro danou službu.</span><span class="sxs-lookup"><span data-stu-id="000ac-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="000ac-166">Parametry používané monikerem určují:</span><span class="sxs-lookup"><span data-stu-id="000ac-166">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="000ac-167">Adresa koncového bodu výměny metadat služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-167">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="000ac-168">Adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-168">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="000ac-169">Vazba, kterou by měl klient použít pro připojení k tomuto koncovému bodu, a obor názvů, ve kterém je tato vazba definovaná.</span><span class="sxs-lookup"><span data-stu-id="000ac-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="000ac-170">V tomto případě se používá `wsHttpBinding_ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="000ac-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="000ac-171">Název a obor názvů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="000ac-171">The name and namespace of the contract.</span></span> <span data-ttu-id="000ac-172">Tato identifikace je povinná, protože WSDL může obsahovat více než jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="000ac-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="000ac-173">Po sestavení instance proxy k monikeru služby může klientská aplikace volat metody na proxy serveru, což vede k tomu, že infrastruktura monikeru služby volá odpovídající operace služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Při spuštění ukázky se odpověď na operaci zobrazí v okně se zprávou hostitele Windows Script Host. <span data-ttu-id="000ac-175">To ukazuje klientovi modelu COM, který provádí volání COM pomocí monikeru se smlouvou MEX ke komunikaci se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="000ac-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="000ac-176">Nastavení a sestavení ukázky</span><span class="sxs-lookup"><span data-stu-id="000ac-176">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="000ac-177">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="000ac-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="000ac-178">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="000ac-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="000ac-179">Z Developer Command Prompt pro Visual Studio otevřete složku \client\bin ve složce specifické pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="000ac-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="000ac-180">Pokud používáte Windows Vista, Windows Server 2008, Windows 7 nebo Windows Server 2008 R2, ujistěte se, že spouštíte příkazový řádek s oprávněními správce.</span><span class="sxs-lookup"><span data-stu-id="000ac-180">If you are using Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="000ac-181">Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` pro export knihovny DLL do souboru TLB.</span><span class="sxs-lookup"><span data-stu-id="000ac-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="000ac-182">Očekává se "upozornění exportéra knihovny typů", ale nejedná se o problém, protože obecný typ není povinný.</span><span class="sxs-lookup"><span data-stu-id="000ac-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="000ac-183">Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` pro registraci typů pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="000ac-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="000ac-184">Očekává se "upozornění exportéra knihovny typů", ale nejedná se o problém, protože obecný typ není povinný.</span><span class="sxs-lookup"><span data-stu-id="000ac-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="000ac-185">Zadejte `gacutil.exe /i client.dll`, chcete-li přidat sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="000ac-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="000ac-186">Spuštění ukázky na stejném počítači</span><span class="sxs-lookup"><span data-stu-id="000ac-186">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="000ac-187">Otestujte, zda ke službě můžete přistupovat pomocí prohlížeče zadáním následující adresy: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="000ac-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="000ac-188">V odpovědi by se měla zobrazit Stránka s potvrzením.</span><span class="sxs-lookup"><span data-stu-id="000ac-188">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="000ac-189">Spusťte ComCalcClient. vbs z \Client, ze složky pro konkrétní jazyk.</span><span class="sxs-lookup"><span data-stu-id="000ac-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="000ac-190">Aktivita klienta se zobrazí v oknech se zprávou.</span><span class="sxs-lookup"><span data-stu-id="000ac-190">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="000ac-191">Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="000ac-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="000ac-192">Spuštění ukázky mezi počítači</span><span class="sxs-lookup"><span data-stu-id="000ac-192">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="000ac-193">Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="000ac-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="000ac-194">Skript Setupvroot. bat, který je součástí ukázky, se dá použít k vytvoření adresáře disku a virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="000ac-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="000ac-195">Zkopírujte programové soubory služby z%SystemDrive%\Inetpub\wwwroot\servicemodelsamples do virtuálního adresáře ServiceModelSamples na počítači služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="000ac-196">Nezapomeňte zahrnout soubory do adresáře \Bin.</span><span class="sxs-lookup"><span data-stu-id="000ac-196">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="000ac-197">Zkopírujte soubor skriptu klienta ze složky \Client ve složce pro konkrétní jazyk do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="000ac-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="000ac-198">V souboru skriptu změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby.</span><span class="sxs-lookup"><span data-stu-id="000ac-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="000ac-199">Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="000ac-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="000ac-200">Zkopírujte soubor WSDL do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="000ac-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="000ac-201">V souboru WSDL serviceWsdl. XML nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.</span><span class="sxs-lookup"><span data-stu-id="000ac-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="000ac-202">Zkopírujte knihovnu Client. dll ze složky \client\bin ve složce pro konkrétní jazyk do adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="000ac-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="000ac-203">Z příkazového řádku přejděte do cílového adresáře v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="000ac-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="000ac-204">Pokud používáte systém Windows Vista nebo Windows Server 2008, spusťte příkazový řádek jako správce.</span><span class="sxs-lookup"><span data-stu-id="000ac-204">If using Windows Vista or Windows Server 2008, make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="000ac-205">Zadejte `tlbexp.exe client.dll /out:CalcProxy.tlb` pro export knihovny DLL do souboru TLB.</span><span class="sxs-lookup"><span data-stu-id="000ac-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="000ac-206">Očekává se "upozornění exportéra knihovny typů", ale nejedná se o problém, protože obecný typ není povinný.</span><span class="sxs-lookup"><span data-stu-id="000ac-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="000ac-207">Zadejte `regasm.exe /tlb:CalcProxy.tlb client.dll` pro registraci typů pomocí modelu COM.</span><span class="sxs-lookup"><span data-stu-id="000ac-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="000ac-208">Před spuštěním příkazu zajistěte, aby byla cesta nastavená na složku, která obsahuje `regasm.exe`.</span><span class="sxs-lookup"><span data-stu-id="000ac-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="000ac-209">Zadejte `gacutil.exe /i client.dll`, chcete-li přidat sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="000ac-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="000ac-210">Před spuštěním příkazu zajistěte, aby byla cesta nastavená na složku, která obsahuje `gacutil.exe`.</span><span class="sxs-lookup"><span data-stu-id="000ac-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="000ac-211">Otestujte, zda ke službě můžete přistupovat z klientského počítače pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="000ac-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="000ac-212">V klientském počítači spusťte ComCalcClient. vbs.</span><span class="sxs-lookup"><span data-stu-id="000ac-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="000ac-213">Vyčištění po ukázce</span><span class="sxs-lookup"><span data-stu-id="000ac-213">To clean up after the sample</span></span>  
  
- <span data-ttu-id="000ac-214">Z bezpečnostních důvodů odeberte definici virtuálního adresáře a oprávnění udělená v krocích instalace, až budete hotovi s ukázkami.</span><span class="sxs-lookup"><span data-stu-id="000ac-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
