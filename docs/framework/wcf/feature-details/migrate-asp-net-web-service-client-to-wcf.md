---
title: "Postupy: Migrace kódu klienta webové služby ASP.NET do služby Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: baf43f2bfa2175062c57f73e45835c251ac5769e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a><span data-ttu-id="d3727-102">Postupy: Migrace kódu klienta webové služby ASP.NET do služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d3727-102">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="d3727-103">Následující postup popisuje obecné kroky, které je třeba dodržet do migrace kódu klienta webové služby ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3727-103">The following procedure describes the broad steps that need to be followed to migrate ASP.NET Web Service client code to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="d3727-104">Postup</span><span class="sxs-lookup"><span data-stu-id="d3727-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a><span data-ttu-id="d3727-105">Do migrace kódu klienta webové služby ASP.NET do WCF</span><span class="sxs-lookup"><span data-stu-id="d3727-105">To migrate ASP.NET Web Service client code to WCF</span></span>  
  
1.  <span data-ttu-id="d3727-106">Ujistěte se, že o komplexní sadu testů pro klienta neexistují.</span><span class="sxs-lookup"><span data-stu-id="d3727-106">Ensure that a comprehensive set of tests exist for the client.</span></span>  
  
2.  <span data-ttu-id="d3727-107">Pomocí sady Visual Studio 2005 můžete upgradovat klienta aplikace rozhraní .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="d3727-107">Use Visual Studio 2005 to upgrade the client application to .NET 2.0.</span></span> <span data-ttu-id="d3727-108">Spusťte sadu testů.</span><span class="sxs-lookup"><span data-stu-id="d3727-108">Run the set of tests.</span></span>  
  
3.  <span data-ttu-id="d3727-109">Odebrání klientského projektu ASP.NET kód klienta.</span><span class="sxs-lookup"><span data-stu-id="d3727-109">Remove ASP.NET client code from the client project.</span></span> <span data-ttu-id="d3727-110">Tento kód se generuje pomocí nástroje WSDL.exe moduly.</span><span class="sxs-lookup"><span data-stu-id="d3727-110">That code is in modules generated using the WSDL.exe tool.</span></span>  
  
4.  <span data-ttu-id="d3727-111">Generovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta kódu pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d3727-111">Generate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client code using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="d3727-112">Přidání tohoto kódu do projektu klienta a sloučit výstup konfigurace do klienta existující konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="d3727-112">Add that code to the client project and merge the configuration output into the client’s existing configuration file.</span></span>  
  
5.  <span data-ttu-id="d3727-113">Kompilace aplikace.</span><span class="sxs-lookup"><span data-stu-id="d3727-113">Compile the application.</span></span> <span data-ttu-id="d3727-114">Oprava chyb kompilace nahrazením odkazy na bývalé typů klientů ASP.NET s odkazy na nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] typů klientů.</span><span class="sxs-lookup"><span data-stu-id="d3727-114">Repair the compilation errors by replacing references to the former ASP.NET client types with references to the new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client types.</span></span>  
  
6.  <span data-ttu-id="d3727-115">Spusťte sadu testů.</span><span class="sxs-lookup"><span data-stu-id="d3727-115">Run the set of tests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3727-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3727-116">See Also</span></span>  
 [<span data-ttu-id="d3727-117">Postupy: Migrace kódu webové služby ASP.NET na Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d3727-117">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
