---
title: 'Postupy: Použití monikeru služby u kontraktů WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 7bc628952d4a7198f0b5545014ae931bbf73dab3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969005"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="eaa45-102">Postupy: Použití monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="eaa45-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="eaa45-103">Existují situace, kdy možná budete chtít mít zcela samostatný klient zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="eaa45-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="eaa45-104">Služba, kterou chcete volat, nesmí vystavit koncový bod MEX a Klientská knihovna WCF nemusí být registrována pro zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="eaa45-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="eaa45-105">V těchto případech můžete vytvořit soubor WSDL, který popisuje službu a předává ji do monikeru služby WCF.</span><span class="sxs-lookup"><span data-stu-id="eaa45-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="eaa45-106">Toto téma popisuje, jak volat ukázku Začínáme WCF pomocí monikeru WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="eaa45-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="eaa45-107">Použití monikeru služby WSDL</span><span class="sxs-lookup"><span data-stu-id="eaa45-107">Using the WSDL service moniker</span></span>  
  
1. <span data-ttu-id="eaa45-108">Otevřete a sestavte ukázkové řešení soubor GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="eaa45-108">Open and build the GettingStarted sample solution.</span></span>  
  
2. <span data-ttu-id="eaa45-109">Spusťte Internet Explorer a přejděte na `http://localhost/ServiceModelSamples/Service.svc` adresu a ujistěte se, že služba funguje.</span><span class="sxs-lookup"><span data-stu-id="eaa45-109">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3. <span data-ttu-id="eaa45-110">V souboru Service.cs přidejte následující atribut pro třídu CalculatorService:</span><span class="sxs-lookup"><span data-stu-id="eaa45-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. <span data-ttu-id="eaa45-111">Přidejte obor názvů vazby do App Service. config:</span><span class="sxs-lookup"><span data-stu-id="eaa45-111">Add a binding namespace to the service App.config:</span></span>  

5. <span data-ttu-id="eaa45-112">Vytvořte soubor WSDL, který má aplikace číst.</span><span class="sxs-lookup"><span data-stu-id="eaa45-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="eaa45-113">Vzhledem k tomu, že obory názvů byly přidány v krocích 3 a 4, můžete použít aplikaci IE k dotazování na celý popis služby WSDL `http://localhost/ServiceModelSamples/Service.svc?wsdl`, a to tak, že přejdete na.</span><span class="sxs-lookup"><span data-stu-id="eaa45-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="eaa45-114">Pak můžete soubor uložit z aplikace Internet Explorer jako serviceWSDL. XML.</span><span class="sxs-lookup"><span data-stu-id="eaa45-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="eaa45-115">Pokud neurčíte obory názvů v krocích 3 a 4, dokument WSDL vrácený z dotazu na výše uvedenou adresu URL nebude kompletní WSDL.</span><span class="sxs-lookup"><span data-stu-id="eaa45-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="eaa45-116">Vrácený dokument WSDL bude obsahovat několik příkazů importu, které importují jiné dokumenty WSDL.</span><span class="sxs-lookup"><span data-stu-id="eaa45-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="eaa45-117">Budete muset projít každým příkazem importu a sestavit kompletní dokument WSDL a kombinaci prvku WSDL vráceného z této služby s importovaným jazykem WSDL.</span><span class="sxs-lookup"><span data-stu-id="eaa45-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6. <span data-ttu-id="eaa45-118">Otevřete Visual Basic 6,0 a vytvořte nový standardní soubor. exe.</span><span class="sxs-lookup"><span data-stu-id="eaa45-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="eaa45-119">Přidejte do formuláře tlačítko a dvakrát klikněte na tlačítko a přidejte následující kód do obslužné rutiny Click:</span><span class="sxs-lookup"><span data-stu-id="eaa45-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    > Pokud je moniker poškozený nebo pokud není služba k dispozici, volání `GetObject` vrátí chybu s názvem neplatná syntaxe.  <span data-ttu-id="eaa45-121">Pokud se zobrazí tato chyba, ujistěte se, že moniker, který používáte, je správný a služba je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="eaa45-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7. <span data-ttu-id="eaa45-122">Spusťte aplikaci Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eaa45-122">Run the Visual Basic application.</span></span> <span data-ttu-id="eaa45-123">Zobrazí se okno se zprávou s výsledky volání odečíst (145, 76,54).</span><span class="sxs-lookup"><span data-stu-id="eaa45-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa45-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eaa45-124">See also</span></span>

- [<span data-ttu-id="eaa45-125">Začínáme</span><span class="sxs-lookup"><span data-stu-id="eaa45-125">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="eaa45-126">Přehled integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="eaa45-126">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
