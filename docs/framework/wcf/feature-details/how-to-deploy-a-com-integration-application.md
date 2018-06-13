---
title: 'Postupy: Nasazení aplikace integrací COM+'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 872d0f0c84c1ac0ea96a87ed24a386bb9bedcf85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490136"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="a9039-102">Postupy: Nasazení aplikace integrací COM+</span><span class="sxs-lookup"><span data-stu-id="a9039-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="a9039-103">Jednou byly zapsány aplikace integrací COM +, můžete chtít nasadit virtuální počítač na jiný počítač.</span><span class="sxs-lookup"><span data-stu-id="a9039-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="a9039-104">Toto téma popisuje postup přesunutí integrace aplikace modelu COM + z jednoho počítače do druhého.</span><span class="sxs-lookup"><span data-stu-id="a9039-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="a9039-105">Přesunutí modelu COM + hostované integrace aplikace</span><span class="sxs-lookup"><span data-stu-id="a9039-105">Moving a COM+ hosted Integration App</span></span>  
  
1.  <span data-ttu-id="a9039-106">Zkontrolujte, zda je na obou počítačích nainstalován WCF.</span><span class="sxs-lookup"><span data-stu-id="a9039-106">Ensure that WCF is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="a9039-107">Exportujte aplikace z počítače A.</span><span class="sxs-lookup"><span data-stu-id="a9039-107">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="a9039-108">Importovat aplikace na počítači B.</span><span class="sxs-lookup"><span data-stu-id="a9039-108">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="a9039-109">Nastavte kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="a9039-109">Set the Application Root Directory.</span></span> <span data-ttu-id="a9039-110">Podle konvence, to je %PROGRAMFILES%/ComPlus aplikace / {AppGUID}.</span><span class="sxs-lookup"><span data-stu-id="a9039-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5.  <span data-ttu-id="a9039-111">Zkopírujte soubory Application.config a Application.manifest z kořenového adresáře aplikace na počítače A do kořenového adresáře aplikace v počítači B.</span><span class="sxs-lookup"><span data-stu-id="a9039-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6.  <span data-ttu-id="a9039-112">Upravte adresy koncového bodu služby v souboru Application.config na počítači B identifikovat příslušný počítač.</span><span class="sxs-lookup"><span data-stu-id="a9039-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="a9039-113">Můžete například změnit http://machineA/MyService k http://machineB/MyService.</span><span class="sxs-lookup"><span data-stu-id="a9039-113">For example, change http://machineA/MyService to http://machineB/MyService.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="a9039-114">Přesunutí integrace hostované webové aplikace</span><span class="sxs-lookup"><span data-stu-id="a9039-114">Moving a Web-hosted integration application</span></span>  
  
1.  <span data-ttu-id="a9039-115">Zkontrolujte, zda je na obou počítačích nainstalován WCF.</span><span class="sxs-lookup"><span data-stu-id="a9039-115">Ensure that WCF is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="a9039-116">Exportujte aplikace z počítače A.</span><span class="sxs-lookup"><span data-stu-id="a9039-116">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="a9039-117">Importovat aplikace na počítači B.</span><span class="sxs-lookup"><span data-stu-id="a9039-117">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="a9039-118">Vytvořte kořenovou složku IIS v počítači B.</span><span class="sxs-lookup"><span data-stu-id="a9039-118">Create an IIS vroot on machine B.</span></span>  
  
5.  <span data-ttu-id="a9039-119">Zkopírujte soubor .svc (componentName.svc) a v souboru Web.config z vroot na počítač A pro nově vytvořený virtuální kořenový adresář na počítači B.</span><span class="sxs-lookup"><span data-stu-id="a9039-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9039-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9039-120">See Also</span></span>  
 [<span data-ttu-id="a9039-121">Přehled integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="a9039-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [<span data-ttu-id="a9039-122">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="a9039-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [<span data-ttu-id="a9039-123">Postupy: Použití nástroje pro konfiguraci služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="a9039-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
