---
title: Konfigurace vaší aplikace
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 6fc33e7b114bb78f823575a2b456d601ae75db94
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937644"
---
# <a name="configuring-your-application"></a><span data-ttu-id="dda56-102">Konfigurace vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="dda56-102">Configuring Your Application</span></span>
<span data-ttu-id="dda56-103">Windows Communication Foundation (WCF) používá konfigurační systém .NET a umožňuje nakonfigurovat služby v oboru počítače i aplikace.</span><span class="sxs-lookup"><span data-stu-id="dda56-103">Windows Communication Foundation (WCF) uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="dda56-104">Nastavení konfigurace definované službou WCF se nachází ve skupině oddílů `<system.serviceModel>`.</span><span class="sxs-lookup"><span data-stu-id="dda56-104">Configuration settings defined by WCF are located in the `<system.serviceModel>` section group.</span></span> <span data-ttu-id="dda56-105">Další informace o tom, jak nakonfigurovat službu WCF, najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="dda56-105">For more information about how to configure a WCF service, see the following topics:</span></span>  
  
- [<span data-ttu-id="dda56-106">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="dda56-106">Configuring Services</span></span>](../configuring-services.md)  
  
- [<span data-ttu-id="dda56-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dda56-107">\<system.serviceModel></span></span>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="dda56-108">Nastavení konfigurace definovaná aplikací jsou definovaná ve skupině oddílů `<appSettings>`.</span><span class="sxs-lookup"><span data-stu-id="dda56-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> <span data-ttu-id="dda56-109">Další informace o nastavení aplikace v konfiguračních souborech .NET najdete v tématu [\<appSettings >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dda56-109">For more information about application settings in .NET configuration files, see [\<appSettings>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228154(v=vs.100)).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="dda56-110">Použití editoru konfigurace</span><span class="sxs-lookup"><span data-stu-id="dda56-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="dda56-111">[Nástroj Editor konfigurace služby WCF (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) umožňuje správcům a vývojářům vytvářet a upravovat nastavení konfigurace služeb WCF pomocí grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dda56-111">The WCF [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="dda56-112">Pomocí tohoto nástroje můžete spravovat nastavení vazeb WCF, chování, služeb a diagnostiky bez nutnosti přímo upravovat konfigurační soubory XML.</span><span class="sxs-lookup"><span data-stu-id="dda56-112">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="dda56-113">Úpravy konfiguračních souborů v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dda56-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="dda56-114">Chcete-li upravit konfigurační soubor projektu služby WCF v aplikaci Visual Studio, klikněte na něj pravým tlačítkem **Průzkumník řešení** a vyberte položku **Upravit konfiguraci WCF konfigurace** položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="dda56-114">To edit the configuration file of a WCF service project in Visual Studio, right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="dda56-115">Spustí se [Nástroj Configuration Editor (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="dda56-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dda56-116">Pokud upravíte konfigurační soubor projektu webové služby WCF v aplikaci Visual Studio tak, že na něj kliknete pravým tlačítkem myši v **Průzkumník řešení**, Všimněte si, že chybí položka místní nabídky pro **úpravu konfigurace WCF** .</span><span class="sxs-lookup"><span data-stu-id="dda56-116">If you edit the configuration file of a WCF Web Service project in Visual Studio by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="dda56-117">Pokud chcete tento problém vyřešit, klikněte na nabídku **nástroje** a vyberte **Editor konfigurace služby WCF**.</span><span class="sxs-lookup"><span data-stu-id="dda56-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="dda56-118">Potom můžete kliknout pravým tlačítkem na konfigurační soubor a použít položku místní nabídky **Upravit konfiguraci WCF** .</span><span class="sxs-lookup"><span data-stu-id="dda56-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda56-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dda56-119">See also</span></span>

- [<span data-ttu-id="dda56-120">Editor konfigurace (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="dda56-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../configuration-editor-tool-svcconfigeditor-exe.md)
- [<span data-ttu-id="dda56-121">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="dda56-121">Configuring Services</span></span>](../configuring-services.md)
- [<span data-ttu-id="dda56-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dda56-122">\<system.serviceModel></span></span>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
