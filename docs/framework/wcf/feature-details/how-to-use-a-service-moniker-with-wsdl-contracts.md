---
title: "Postupy: Použití monikeru služby u kontraktů WSDL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c44b09f512a7625360ca5036316d03a4602c5186
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="2c7c6-102">Postupy: Použití monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="2c7c6-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="2c7c6-103">Pokud chcete mít zcela samostatné klienta zprostředkovatel komunikace s objekty COM, existují situace.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="2c7c6-104">Koncový bod MEX a klienta WCF, které pravděpodobně není registrována knihovny DLL pro zprostředkovatel komunikace s objekty COM, nemusí vystavit službu, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="2c7c6-105">V těchto případech můžete vytvořit soubor WSDL, který popisuje službu a předejte ji do monikeru služby WCF.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="2c7c6-106">Toto téma popisuje, jak volat ukázku získávání spuštění WCF pomocí Přezdívka WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="2c7c6-107">Použití monikeru služby WSDL</span><span class="sxs-lookup"><span data-stu-id="2c7c6-107">Using the WSDL service moniker</span></span>  
  
1.  <span data-ttu-id="2c7c6-108">Otevření a sestavení GettingStarted ukázkové řešení.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-108">Open and build the GettingStarted sample solution.</span></span>  
  
2.  <span data-ttu-id="2c7c6-109">Otevřete Internet Explorer a přejděte k http://localhost/ServiceModelSamples/Service.svc Ujistěte se, že služba funguje.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-109">Open Internet Explorer and browse to http://localhost/ServiceModelSamples/Service.svc to make sure that the service is working.</span></span>  
  
3.  <span data-ttu-id="2c7c6-110">V souboru Service.cs přidejte následující atribut na třídě CalculatorService:</span><span class="sxs-lookup"><span data-stu-id="2c7c6-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4.  <span data-ttu-id="2c7c6-111">Přidáte obor názvů vazbu ke službě App.config:</span><span class="sxs-lookup"><span data-stu-id="2c7c6-111">Add a binding namespace to the service App.config:</span></span>  
  
  
  
5.  <span data-ttu-id="2c7c6-112">Vytvořte soubor WSDL pro aplikace pro čtení.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="2c7c6-113">Protože obory názvů byly přidány v krocích 3 a 4, můžete se dotázat na celý popis WSDL služby procházením http://localhost/ServiceModelSamples/Service.svc?wsdl aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to http://localhost/ServiceModelSamples/Service.svc?wsdl.</span></span> <span data-ttu-id="2c7c6-114">Pak můžete soubor uložte z aplikace Internet Explorer jako serviceWSDL.xml.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="2c7c6-115">Pokud nezadáte obory názvů v krocích 3 a 4, nebudou vrácená z dotazu výše uvedenou adresu URL dokumentu WSDL dokončení WSDL.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="2c7c6-116">Dokument WSDL vrátil bude obsahovat několik příkazů importu, které import jiné dokumenty WSDL.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="2c7c6-117">Je nutné projít každý příkaz import a vytvořit úplný dokument WSDL kombinování WSDL vrácená ze služby s WSDL importovat.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6.  <span data-ttu-id="2c7c6-118">Otevřete Visual Basic 6.0 a vytvořte nový soubor standardní .exe.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="2c7c6-119">Přidání tlačítka do formuláře a dvakrát klikněte na tlačítko pro přidání do obslužná rutina kliknutí na následující kód:</span><span class="sxs-lookup"><span data-stu-id="2c7c6-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
    >  Pokud Přezdívka je poškozený nebo pokud služba není dostupná volání `GetObject` se vrátí chyba s oznámením "Neplatná syntaxe".  <span data-ttu-id="2c7c6-121">Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7.  <span data-ttu-id="2c7c6-122">Spuštění aplikace Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2c7c6-122">Run the Visual Basic application.</span></span> <span data-ttu-id="2c7c6-123">Zobrazí se okno se zprávou s výsledky volání Subtract (145, 76.54).</span><span class="sxs-lookup"><span data-stu-id="2c7c6-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c7c6-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c7c6-124">See Also</span></span>  
 [<span data-ttu-id="2c7c6-125">Začínáme</span><span class="sxs-lookup"><span data-stu-id="2c7c6-125">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="2c7c6-126">Integrace s přehled aplikace modelu COM</span><span class="sxs-lookup"><span data-stu-id="2c7c6-126">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
