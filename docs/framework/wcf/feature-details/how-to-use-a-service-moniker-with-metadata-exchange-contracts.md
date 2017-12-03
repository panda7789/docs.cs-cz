---
title: "Postupy: použití Monikeru služby s kontrakty Metadata Exchange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31720b0639f9be68a2124b4ff844a2837787ef81
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="242b8-102">Postupy: použití Monikeru služby s kontrakty Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="242b8-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="242b8-103">Po vývoj některé nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, můžete rozhodnout, že chcete být schopni volání tyto služby ze skriptu nebo aplikace Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="242b8-103">After developing some new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="242b8-104">Jedno z těchto metod bude generovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sestavení klienta zaregistrovat sestavení modelu COM, nainstalujte sestavení v mezipaměti GAC a pak odkazovat typy modelu COM z kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="242b8-104">One method would be to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="242b8-105">Když distribuujete aplikace, budete ji muset distribuovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] také sestavení klienta.</span><span class="sxs-lookup"><span data-stu-id="242b8-105">When you distribute the application, you will have to distribute the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Client assembly as well.</span></span> <span data-ttu-id="242b8-106">Uživatel pak bude mít k registraci sestavení klienta WCF u modelu COM a jeho následné uložení do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="242b8-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="242b8-107">Zprostředkovatel komunikace s objekty COM také umožňuje provádět stejné volání služby bez nutnosti spoléhat se na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sestavení klienta.</span><span class="sxs-lookup"><span data-stu-id="242b8-107"> COM Interop also allows you to make the same service calls without relying on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly.</span></span> <span data-ttu-id="242b8-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přezdívka umožňuje volat žádný [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby z jakéhokoli jazyka kompatibilní COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) a tak dále) zadáním exchange (Mex) koncový bod metadat identifikátor URI, který používá monikeru služby extrahovat typ informace o službě.</span><span class="sxs-lookup"><span data-stu-id="242b8-108">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker allows you to call any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="242b8-109">Toto téma popisuje, jak volat Začínáme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázkové pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přezdívka, která určuje koncový bod Mex.</span><span class="sxs-lookup"><span data-stu-id="242b8-109">This topic describes how to call the Getting Started [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="242b8-110">Typy definované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nikdy skutečně instance sestavení klienta.</span><span class="sxs-lookup"><span data-stu-id="242b8-110">The types defined by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly are never actually instantiated.</span></span> <span data-ttu-id="242b8-111">Sestavení se používá pouze pro metadata.</span><span class="sxs-lookup"><span data-stu-id="242b8-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="242b8-112">Použití monikeru služby s adresou Mex</span><span class="sxs-lookup"><span data-stu-id="242b8-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="242b8-113">Sestavit ukázku Začínáme a aplikaci Internet Explorer a přejděte do jeho adresa URL (http://localhost/ServiceModelSamples/Service.svc) k zajištění, že služba funguje.</span><span class="sxs-lookup"><span data-stu-id="242b8-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="242b8-114">Vytvořte skript jazyka Visual Basic nebo Visual Basic aplikaci, která obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="242b8-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="242b8-115">Spuštění aplikace Visual Basic nebo skriptu.</span><span class="sxs-lookup"><span data-stu-id="242b8-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="242b8-116">Služby, ke kterému se připojujete musí vystavit koncový bod Mex pro Přezdívka moct číst metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="242b8-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="242b8-117">Další informace najdete v tématu [postupy: publikování metadat služby promocí konfigurační soubor](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="242b8-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="242b8-118">Pokud Přezdívka je poškozený nebo pokud služba není dostupná, volání `GetObject` se vrátí chyba s oznámením "Neplatnou syntaxi."</span><span class="sxs-lookup"><span data-stu-id="242b8-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="242b8-119">Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="242b8-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="242b8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="242b8-120">See Also</span></span>  
 [<span data-ttu-id="242b8-121">Postupy: použití Monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="242b8-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="242b8-122">Postupy: použití Monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="242b8-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
