---
title: 'Postupy: Nasazení aplikace integrací COM+'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: fcf525943e6e453253c6f4d3bcfa8a1a08df6909
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343373"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="3fb3d-102">Postupy: Nasazení aplikace integrací COM+</span><span class="sxs-lookup"><span data-stu-id="3fb3d-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="3fb3d-103">Jakmile jste napsali aplikace COM + integration, můžete chtít nasadit virtuální počítač na jiném počítači.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="3fb3d-104">Toto téma popisuje, jak aplikace integrací COM + přesunete z jednoho počítače do jiného.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="3fb3d-105">Přesunutí modelu COM + hostované aplikace integrace</span><span class="sxs-lookup"><span data-stu-id="3fb3d-105">Moving a COM+ hosted Integration App</span></span>  
  
1. <span data-ttu-id="3fb3d-106">Zkontrolujte, zda je na obou počítačích nainstalován WCF.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-106">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="3fb3d-107">Exportovat aplikaci z počítače A.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-107">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="3fb3d-108">Import aplikace na počítači B.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-108">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="3fb3d-109">Nastavte kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-109">Set the Application Root Directory.</span></span> <span data-ttu-id="3fb3d-110">Podle konvence, toto je aplikace %PROGRAMFILES%/ComPlus / {AppGUID}.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5. <span data-ttu-id="3fb3d-111">Zkopírujte soubory Application.config a Application.manifest z kořenového adresáře aplikace na počítači A do kořenového adresáře aplikace na počítači B.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6. <span data-ttu-id="3fb3d-112">Úprava adresy koncových bodů služby v souboru Application.config v počítači B k identifikaci příslušné počítače.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="3fb3d-113">Například změnit `http://machineA/MyService` k `http://machineB/MyService`.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-113">For example, change `http://machineA/MyService` to `http://machineB/MyService`.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="3fb3d-114">Přesunutí integrace hostované webové aplikace</span><span class="sxs-lookup"><span data-stu-id="3fb3d-114">Moving a Web-hosted integration application</span></span>  
  
1. <span data-ttu-id="3fb3d-115">Zkontrolujte, zda je na obou počítačích nainstalován WCF.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-115">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="3fb3d-116">Exportovat aplikaci z počítače A.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-116">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="3fb3d-117">Import aplikace na počítači B.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-117">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="3fb3d-118">Vytvořit složku IIS vroot na počítači B.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-118">Create an IIS vroot on machine B.</span></span>  
  
5. <span data-ttu-id="3fb3d-119">Kopírování souboru .svc (componentName.svc) a v souboru Web.config z virtuální kořenový adresář v počítači A do nově vytvořené virtuální kořenový adresář v počítači služby serveru B.</span><span class="sxs-lookup"><span data-stu-id="3fb3d-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb3d-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fb3d-120">See also</span></span>

- [<span data-ttu-id="3fb3d-121">Přehled integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="3fb3d-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
- [<span data-ttu-id="3fb3d-122">Postupy: Konfigurace nastavení služby modelu COM +</span><span class="sxs-lookup"><span data-stu-id="3fb3d-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
- [<span data-ttu-id="3fb3d-123">Postupy: Použijte nástroj pro konfiguraci modelu služby COM +</span><span class="sxs-lookup"><span data-stu-id="3fb3d-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
