---
title: "Konfigurace vaší aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f22fac02616070ecd6498ad0e158782001681ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-your-application"></a><span data-ttu-id="467c3-102">Konfigurace vaší aplikace</span><span class="sxs-lookup"><span data-stu-id="467c3-102">Configuring Your Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="467c3-103">používá konfigurační systém .NET a umožňuje vám nakonfigurovat služby v oboru počítače a aplikace.</span><span class="sxs-lookup"><span data-stu-id="467c3-103"> uses the .NET configuration system and allows you to configure services at both the machine and application scope.</span></span>  
  
 <span data-ttu-id="467c3-104">Nastavení konfigurace definované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou umístěné v `<system.serviceModel>` skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="467c3-104">Configuration settings defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are located in the `<system.serviceModel>` section group.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="467c3-105">Postup konfigurace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="467c3-105"> how to configure a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, see the following topics:</span></span>  
  
-   [<span data-ttu-id="467c3-106">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="467c3-106">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [<span data-ttu-id="467c3-107">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="467c3-107">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 <span data-ttu-id="467c3-108">Nastavení konfigurace definované aplikací, které jsou definovány v `<appSettings>` skupinu oddílů.</span><span class="sxs-lookup"><span data-stu-id="467c3-108">Application-defined configurations settings are defined in the `<appSettings>` section group.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="467c3-109">nastavení aplikace v rozhraní .NET konfigurační soubory, najdete v části [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).</span><span class="sxs-lookup"><span data-stu-id="467c3-109"> application settings in .NET configuration files, see [\<appSettings>](http://go.microsoft.com/fwlink/?LinkId=95159).</span></span>  
  
## <a name="using-the-configuration-editor"></a><span data-ttu-id="467c3-110">Pomocí editoru konfigurace</span><span class="sxs-lookup"><span data-stu-id="467c3-110">Using the Configuration Editor</span></span>  
 <span data-ttu-id="467c3-111">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [Nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umožňuje správcům a vývojářům umožňuje vytvořit a upravit nastavení konfigurace pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služeb pomocí grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="467c3-111">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)][Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) allows administrators and developers to create and modify configuration settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using a graphical user interface.</span></span> <span data-ttu-id="467c3-112">Pomocí tohoto nástroje můžete spravovat nastavení pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby, chování, služeb a diagnostiky bez přímou úpravou konfiguračních souborů XML.</span><span class="sxs-lookup"><span data-stu-id="467c3-112">With this tool, you can manage settings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bindings, behaviors, services, and diagnostics without directly editing XML configuration files.</span></span>  
  
## <a name="editing-configuration-files-in-visual-studio"></a><span data-ttu-id="467c3-113">Úprava konfiguračních souborů v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="467c3-113">Editing Configuration Files in Visual Studio</span></span>  
 <span data-ttu-id="467c3-114">Chcete-li upravit konfigurační soubor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projektu služby v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], klikněte pravým tlačítkem v **Průzkumníku řešení** a zvolte **upravit konfigurace WCF** položky kontextové nabídky.</span><span class="sxs-lookup"><span data-stu-id="467c3-114">To edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service project in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], right click it in **Solution Explorer** and choose the **Edit WCF Config** context menu item.</span></span> <span data-ttu-id="467c3-115">Spustí se [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="467c3-115">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="467c3-116">Pokud chcete upravit konfigurační soubor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projekt webové služby v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] kliknutím pravým tlačítkem myši v **Průzkumníku řešení**, Všimněte si, že **upravit konfigurace WCF** chybí položky kontextové nabídky .</span><span class="sxs-lookup"><span data-stu-id="467c3-116">If you edit the configuration file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Service project in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] by right-clicking it in **Solution Explorer**, notice that the **Edit WCF Config** context menu item is missing.</span></span> <span data-ttu-id="467c3-117">Chcete-li vyřešit tento problém, klikněte na tlačítko **nástroje** nabídce a zvolte **Editor konfigurace služby WCF**.</span><span class="sxs-lookup"><span data-stu-id="467c3-117">To workaround this issue, click the **Tools** menu, and choose **WCF Service Config Editor**.</span></span> <span data-ttu-id="467c3-118">Potom můžete klikněte pravým tlačítkem na soubor konfigurace a použít **upravit konfigurace WCF** položky kontextové nabídky.</span><span class="sxs-lookup"><span data-stu-id="467c3-118">After that, you can right-click a configuration file and use the **Edit WCF Config** context menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="467c3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="467c3-119">See Also</span></span>  
 [<span data-ttu-id="467c3-120">Nástroj Configuration Editor (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="467c3-120">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [<span data-ttu-id="467c3-121">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="467c3-121">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="467c3-122">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="467c3-122">\<system.serviceModel></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
