---
title: 'Postupy: Migrace kódu klienta webové služby ASP.NET do služby Windows Communication Foundation'
ms.date: 03/30/2017
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
ms.openlocfilehash: cb60f9cb2e8f35ee703b049eae9e3d99c1ec7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491127"
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a><span data-ttu-id="415f0-102">Postupy: Migrace kódu klienta webové služby ASP.NET do služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="415f0-102">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="415f0-103">Následující postup popisuje obecné kroky, které je třeba dodržet do migrace kódu klienta webové služby ASP.NET do WCF.</span><span class="sxs-lookup"><span data-stu-id="415f0-103">The following procedure describes the broad steps that need to be followed to migrate ASP.NET Web Service client code to WCF.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="415f0-104">Postup</span><span class="sxs-lookup"><span data-stu-id="415f0-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a><span data-ttu-id="415f0-105">Do migrace kódu klienta webové služby ASP.NET do WCF</span><span class="sxs-lookup"><span data-stu-id="415f0-105">To migrate ASP.NET Web Service client code to WCF</span></span>  
  
1.  <span data-ttu-id="415f0-106">Ujistěte se, že o komplexní sadu testů pro klienta neexistují.</span><span class="sxs-lookup"><span data-stu-id="415f0-106">Ensure that a comprehensive set of tests exist for the client.</span></span>  
  
2.  <span data-ttu-id="415f0-107">Pomocí sady Visual Studio 2005 můžete upgradovat klienta aplikace rozhraní .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="415f0-107">Use Visual Studio 2005 to upgrade the client application to .NET 2.0.</span></span> <span data-ttu-id="415f0-108">Spusťte sadu testů.</span><span class="sxs-lookup"><span data-stu-id="415f0-108">Run the set of tests.</span></span>  
  
3.  <span data-ttu-id="415f0-109">Odebrání klientského projektu ASP.NET kód klienta.</span><span class="sxs-lookup"><span data-stu-id="415f0-109">Remove ASP.NET client code from the client project.</span></span> <span data-ttu-id="415f0-110">Tento kód se generuje pomocí nástroje WSDL.exe moduly.</span><span class="sxs-lookup"><span data-stu-id="415f0-110">That code is in modules generated using the WSDL.exe tool.</span></span>  
  
4.  <span data-ttu-id="415f0-111">Generovat pomocí kódu klienta WCF [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="415f0-111">Generate WCF client code using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="415f0-112">Přidání tohoto kódu do projektu klienta a sloučit výstup konfigurace do klienta existující konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="415f0-112">Add that code to the client project and merge the configuration output into the client’s existing configuration file.</span></span>  
  
5.  <span data-ttu-id="415f0-113">Kompilace aplikace.</span><span class="sxs-lookup"><span data-stu-id="415f0-113">Compile the application.</span></span> <span data-ttu-id="415f0-114">Opravte chyby kompilace nahrazením odkazy na bývalé typů klientů ASP.NET s odkazy na nové typy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="415f0-114">Repair the compilation errors by replacing references to the former ASP.NET client types with references to the new WCF client types.</span></span>  
  
6.  <span data-ttu-id="415f0-115">Spusťte sadu testů.</span><span class="sxs-lookup"><span data-stu-id="415f0-115">Run the set of tests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415f0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="415f0-116">See Also</span></span>  
 [<span data-ttu-id="415f0-117">Postupy: Migrace kódu webové služby ASP.NET na Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="415f0-117">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
