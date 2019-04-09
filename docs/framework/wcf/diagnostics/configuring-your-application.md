---
title: Konfigurace vaší aplikace
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 94bf5f4bbee8bb8bb462c4bf91be75d1627ec567
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087167"
---
# <a name="configuring-your-application"></a><span data-ttu-id="c3262-102">Konfigurace vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="c3262-102">Configuring Your Application</span></span>
<span data-ttu-id="c3262-103">Windows Communication Foundation (WCF) využívá konfigurační systém .NET a umožňuje vám nakonfigurovat služby v počítači a aplikační oboru.</span><span class="sxs-lookup"><span data-stu-id="c3262-103">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="c3262-104">Nastavení konfigurace určené WCF se nachází v `<system.serviceModel>` skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="c3262-104">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="c3262-105">Další informace o tom, jak nakonfigurovat službu WCF naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="c3262-105">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
-   [<span data-ttu-id="c3262-106">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="c3262-106">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [<span data-ttu-id="c3262-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c3262-107">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="c3262-108">Nastavení konfigurace definované aplikací, které jsou definovány v `<appSettings>` skupiny oddílů.</span><span class="sxs-lookup"><span data-stu-id="c3262-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="c3262-109">Další informace o nastavení aplikace v .NET konfigurační soubory, naleznete v tématu [ \<appSettings >](https://go.microsoft.com/fwlink/?LinkId=95159).</span><span class="sxs-lookup"><span data-stu-id="c3262-109">For more information about application settings in .NET configuration files, see [\<appSettings>](https://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="c3262-110">Pomocí editoru konfigurace</span><span class="sxs-lookup"><span data-stu-id="c3262-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="c3262-111">WCF [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umožňuje správcům a vývojářům umožňuje vytvářet a upravovat nastavení konfigurace pro služby WCF pomocí grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c3262-111">The WCF [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="c3262-112">Pomocí tohoto nástroje můžete spravovat nastavení pro vazby WCF, chování, služby a diagnostické nástroje bez přímou úpravou konfiguračních souborů XML.</span><span class="sxs-lookup"><span data-stu-id="c3262-112">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="c3262-113">Úprava konfiguračních souborů v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c3262-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="c3262-114">Úprava konfiguračního souboru projektu služby WCF v sadě Visual Studio, klikněte pravým tlačítkem myši klikněte na něj v **Průzkumníka řešení** a zvolte **upravit konfigurace WCF** položka kontextové nabídky.</span><span class="sxs-lookup"><span data-stu-id="c3262-114">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="c3262-115">Tím se spustí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c3262-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3262-116">Pokud upravíte kliknutím pravým tlačítkem myši v konfiguračním souboru projektu webové služby WCF v sadě Visual Studio **Průzkumníka řešení**, Všimněte si, že **upravit konfigurace WCF** chybí položka kontextové nabídky.</span><span class="sxs-lookup"><span data-stu-id="c3262-116">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="c3262-117">Chcete-li vyřešit tento problém, klikněte na tlačítko **nástroje** nabídky a zvolte **Editor konfigurace služby WCF**.</span><span class="sxs-lookup"><span data-stu-id="c3262-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="c3262-118">Poté klikněte pravým tlačítkem na konfigurační soubor a použít **upravit konfigurace WCF** položka kontextové nabídky.</span><span class="sxs-lookup"><span data-stu-id="c3262-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3262-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3262-119">See also</span></span>

- [<span data-ttu-id="c3262-120">Nástroj Configuration Editor (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="c3262-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="c3262-121">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="c3262-121">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)
- [<span data-ttu-id="c3262-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c3262-122">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
