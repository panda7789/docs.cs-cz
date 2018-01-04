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
ms.workload: dotnet
ms.openlocfilehash: 7d2b5b6d4a671a3eb281f49dd60fd3c00ee76f8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="159c0-102">Postupy: použití Monikeru služby s kontrakty Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="159c0-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="159c0-103">Po vývoj některé nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, můžete rozhodnout, že chcete být schopni volání tyto služby ze skriptu nebo aplikace Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="159c0-103">After developing some new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="159c0-104">Jedno z těchto metod bude generovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sestavení klienta zaregistrovat sestavení modelu COM, nainstalujte sestavení v mezipaměti GAC a pak odkazovat typy modelu COM z kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="159c0-104">One method would be to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="159c0-105">Když distribuujete aplikace, budete ji muset distribuovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] také sestavení klienta.</span><span class="sxs-lookup"><span data-stu-id="159c0-105">When you distribute the application, you will have to distribute the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Client assembly as well.</span></span> <span data-ttu-id="159c0-106">Uživatel pak bude mít k registraci sestavení klienta WCF u modelu COM a jeho následné uložení do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="159c0-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="159c0-107">Zprostředkovatel komunikace s objekty COM také umožňuje provádět stejné volání služby bez nutnosti spoléhat se na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sestavení klienta.</span><span class="sxs-lookup"><span data-stu-id="159c0-107"> COM Interop also allows you to make the same service calls without relying on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly.</span></span> <span data-ttu-id="159c0-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přezdívka umožňuje volat žádný [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby z jakéhokoli jazyka kompatibilní COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) a tak dále) zadáním exchange (Mex) koncový bod metadat identifikátor URI, který používá monikeru služby extrahovat typ informace o službě.</span><span class="sxs-lookup"><span data-stu-id="159c0-108">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker allows you to call any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="159c0-109">Toto téma popisuje, jak volat Začínáme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázkové pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přezdívka, která určuje koncový bod Mex.</span><span class="sxs-lookup"><span data-stu-id="159c0-109">This topic describes how to call the Getting Started [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="159c0-110">Typy definované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nikdy skutečně instance sestavení klienta.</span><span class="sxs-lookup"><span data-stu-id="159c0-110">The types defined by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly are never actually instantiated.</span></span> <span data-ttu-id="159c0-111">Sestavení se používá pouze pro metadata.</span><span class="sxs-lookup"><span data-stu-id="159c0-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="159c0-112">Použití monikeru služby s adresou Mex</span><span class="sxs-lookup"><span data-stu-id="159c0-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="159c0-113">Sestavit ukázku Začínáme a aplikaci Internet Explorer a přejděte do jeho adresa URL (http://localhost/ServiceModelSamples/Service.svc) k zajištění, že služba funguje.</span><span class="sxs-lookup"><span data-stu-id="159c0-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="159c0-114">Vytvořte skript jazyka Visual Basic nebo Visual Basic aplikaci, která obsahuje následující kód:</span><span class="sxs-lookup"><span data-stu-id="159c0-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="159c0-115">Spuštění aplikace Visual Basic nebo skriptu.</span><span class="sxs-lookup"><span data-stu-id="159c0-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="159c0-116">Služby, ke kterému se připojujete musí vystavit koncový bod Mex pro Přezdívka moct číst metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="159c0-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="159c0-117">Další informace najdete v tématu [postupy: publikování metadat služby promocí konfigurační soubor](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="159c0-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="159c0-118">Pokud Přezdívka je poškozený nebo pokud služba není dostupná, volání `GetObject` se vrátí chyba s oznámením "Neplatnou syntaxi."</span><span class="sxs-lookup"><span data-stu-id="159c0-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="159c0-119">Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="159c0-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="159c0-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="159c0-120">See Also</span></span>  
 [<span data-ttu-id="159c0-121">Postupy: Použití monikeru služby Windows Communication Foundation bez registrace</span><span class="sxs-lookup"><span data-stu-id="159c0-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="159c0-122">Postupy: Použití monikeru služby u kontraktů WSDL</span><span class="sxs-lookup"><span data-stu-id="159c0-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
