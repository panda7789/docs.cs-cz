---
title: 'Postupy: Nasazení aplikace integrací COM+'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: b4ae7f730296d54debc1cf2971b61e5700503430
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595424"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="0ca2c-102">Postupy: Nasazení aplikace integrací COM+</span><span class="sxs-lookup"><span data-stu-id="0ca2c-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="0ca2c-103">Po zapsání aplikace pro integraci COM+ můžete ji chtít nasadit na jiný počítač.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="0ca2c-104">Toto téma popisuje, jak přesunout integrační aplikaci modelu COM+ z jednoho počítače do jiného.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="0ca2c-105">Přesun aplikace pro integraci hostované v modelu COM+</span><span class="sxs-lookup"><span data-stu-id="0ca2c-105">Moving a COM+ hosted Integration App</span></span>  
  
1. <span data-ttu-id="0ca2c-106">Ujistěte se, že je na obou počítačích nainstalovaný WCF.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-106">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="0ca2c-107">Exportujte aplikaci z počítače A.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-107">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="0ca2c-108">Importujte aplikaci na počítač B.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-108">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="0ca2c-109">Nastavte kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-109">Set the Application Root Directory.</span></span> <span data-ttu-id="0ca2c-110">Podle konvence je% PROGRAMFILES%/ComPlus aplikací/{AppGUID}.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5. <span data-ttu-id="0ca2c-111">Zkopírujte soubory Application. config a Application. manifest z kořenového adresáře aplikace v počítači A do kořenového adresáře aplikace v počítači B.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6. <span data-ttu-id="0ca2c-112">Upravte adresy koncových bodů služby v souboru Application. config na počítači B a Identifikujte příslušný počítač.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="0ca2c-113">Například změňte `http://machineA/MyService` na `http://machineB/MyService` .</span><span class="sxs-lookup"><span data-stu-id="0ca2c-113">For example, change `http://machineA/MyService` to `http://machineB/MyService`.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="0ca2c-114">Přesun webové aplikace hostované na webu</span><span class="sxs-lookup"><span data-stu-id="0ca2c-114">Moving a Web-hosted integration application</span></span>  
  
1. <span data-ttu-id="0ca2c-115">Ujistěte se, že je na obou počítačích nainstalovaný WCF.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-115">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="0ca2c-116">Exportujte aplikaci z počítače A.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-116">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="0ca2c-117">Importujte aplikaci na počítač B.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-117">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="0ca2c-118">Vytvořte složku IIS vroot na počítači B.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-118">Create an IIS vroot on machine B.</span></span>  
  
5. <span data-ttu-id="0ca2c-119">Zkopírujte soubor. svc (Component. svc) a soubor Web. config z adresáře vroot na počítači A do nově vytvořené složky vroot v počítači B.</span><span class="sxs-lookup"><span data-stu-id="0ca2c-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca2c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ca2c-120">See also</span></span>

- [<span data-ttu-id="0ca2c-121">Přehled integrace s aplikacemi modelu COM+</span><span class="sxs-lookup"><span data-stu-id="0ca2c-121">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
- [<span data-ttu-id="0ca2c-122">Postupy: Konfigurace nastavení služby modelu COM+</span><span class="sxs-lookup"><span data-stu-id="0ca2c-122">How to: Configure COM+ Service Settings</span></span>](how-to-configure-com-service-settings.md)
- [<span data-ttu-id="0ca2c-123">Postupy: Použití nástroje pro konfiguraci modelu služby COM+</span><span class="sxs-lookup"><span data-stu-id="0ca2c-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](how-to-use-the-com-service-model-configuration-tool.md)
