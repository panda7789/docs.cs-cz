---
title: 'Postupy: Použití monikeru služby u kontraktů WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 2968641538bf0b4d0e136d5784bf69e5e7fcb3a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972884"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="febe7-102">Postupy: Použití monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="febe7-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="febe7-103">Pokud chcete úplně nezávislý klient komunikace s objekty COM, existují situace.</span><span class="sxs-lookup"><span data-stu-id="febe7-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="febe7-104">Na službu, kterou chcete volat nesmí zveřejnit koncový bod MEX a klientský WCF pro spolupráci s COM nelze registrovat knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="febe7-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="febe7-105">V těchto případech můžete vytvořit soubor WSDL, který popisuje službu a předejte ho do monikeru služby WCF.</span><span class="sxs-lookup"><span data-stu-id="febe7-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="febe7-106">Toto téma popisuje, jak volat získávání WCF spustit ukázku pomocí monikeru WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="febe7-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="febe7-107">Použití monikeru služby WSDL</span><span class="sxs-lookup"><span data-stu-id="febe7-107">Using the WSDL service moniker</span></span>  
  
1. <span data-ttu-id="febe7-108">Otevřít a sestavit GettingStarted ukázkové řešení.</span><span class="sxs-lookup"><span data-stu-id="febe7-108">Open and build the GettingStarted sample solution.</span></span>  
  
2. <span data-ttu-id="febe7-109">Spusťte aplikaci Internet Explorer a přejděte do `http://localhost/ServiceModelSamples/Service.svc` abyste měli jistotu, služba funguje.</span><span class="sxs-lookup"><span data-stu-id="febe7-109">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3. <span data-ttu-id="febe7-110">V souboru Service.cs přidejte následující atribut ve třídě CalculatorService:</span><span class="sxs-lookup"><span data-stu-id="febe7-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. <span data-ttu-id="febe7-111">Přidáte obor názvů vazby ve službě App.config:</span><span class="sxs-lookup"><span data-stu-id="febe7-111">Add a binding namespace to the service App.config:</span></span>  

5. <span data-ttu-id="febe7-112">Vytvoření souboru WSDL pro aplikace pro čtení.</span><span class="sxs-lookup"><span data-stu-id="febe7-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="febe7-113">Protože obory názvů byly přidány v krocích 3 a 4, můžete použít Internet Exploreru se dotázat na celý popis WSDL služby tak, že přejdete do `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="febe7-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="febe7-114">Potom můžete uložit soubor z aplikace Internet Explorer jako serviceWSDL.xml.</span><span class="sxs-lookup"><span data-stu-id="febe7-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="febe7-115">Pokud nezadáte obory názvů v krocích 3 a 4, nebudou dokumentu WSDL vrácená z dotazu výše zobrazenou adresu URL dokončení WSDL.</span><span class="sxs-lookup"><span data-stu-id="febe7-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="febe7-116">Dokument WSDL vrátil bude obsahovat několik příkazy pro import, které importují jiné dokumenty WSDL.</span><span class="sxs-lookup"><span data-stu-id="febe7-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="febe7-117">Budete muset projít každý příkaz import a sestavit kompletní dokumentu WSDL, kombinování WSDL vrácený službou WSDL importovat.</span><span class="sxs-lookup"><span data-stu-id="febe7-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6. <span data-ttu-id="febe7-118">Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe.</span><span class="sxs-lookup"><span data-stu-id="febe7-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="febe7-119">Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko Přidat následující kód do obslužné rutiny kliknutí:</span><span class="sxs-lookup"><span data-stu-id="febe7-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
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
    >  Pokud je moniker je poškozený nebo pokud služba není k dispozici volání `GetObject` vrátí chyba s oznámením "Neplatná syntaxe".  <span data-ttu-id="febe7-121">Pokud se zobrazí tato chyba, ujistěte se, že zástupný název, který používáte, je správná a služba není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="febe7-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7. <span data-ttu-id="febe7-122">Spuštění aplikace Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="febe7-122">Run the Visual Basic application.</span></span> <span data-ttu-id="febe7-123">Zobrazí se okno se zprávou s výsledky volání odečíst (145, 76.54).</span><span class="sxs-lookup"><span data-stu-id="febe7-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="febe7-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="febe7-124">See also</span></span>

- [<span data-ttu-id="febe7-125">Začínáme</span><span class="sxs-lookup"><span data-stu-id="febe7-125">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="febe7-126">Přehled integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="febe7-126">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
