---
title: Konfigurace vaší aplikace
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 1844c20ef961f191fb667e31d548518b193a7134
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803647"
---
# <a name="configuring-your-application"></a>Konfigurace vaší aplikace
Windows Communication Foundation (WCF) používá konfigurační systém .NET a umožňuje vám nakonfigurovat služby v oboru počítače a aplikace.  
  
 Nastavení konfigurace definované WCF jsou součástí `<system.serviceModel>` skupinu oddílů. Další informace o tom, jak nakonfigurovat služby WCF najdete v následujících tématech:  
  
-   [Konfigurace služeb](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Nastavení konfigurace definované aplikací, které jsou definovány v `<appSettings>` skupinu oddílů. Další informace o nastavení aplikace v konfiguračních souborech na rozhraní .NET najdete v tématu [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Pomocí editoru konfigurace  
 WCF[nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umožňuje správcům a vývojářům umožňuje vytvořit a upravit nastavení konfigurace pro služby WCF pomocí grafického uživatelského rozhraní. Pomocí tohoto nástroje můžete spravovat nastavení pro vazby WCF, chování, služeb a diagnostiky bez přímou úpravou konfiguračních souborů XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Úprava konfiguračních souborů v sadě Visual Studio  
 Chcete-li upravit konfigurační soubor projektu služby WCF v sadě Visual Studio, klikněte pravým tlačítkem v **Průzkumníku řešení** a zvolte **upravit konfigurace WCF** položky kontextové nabídky. Spustí se [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Pokud chcete upravit konfigurační soubor projektu webové služby WCF v sadě Visual Studio, kliknutím pravým tlačítkem myši v **Průzkumníku řešení**, Všimněte si, že **upravit konfigurace WCF** chybí položky kontextové nabídky. Chcete-li vyřešit tento problém, klikněte na tlačítko **nástroje** nabídce a zvolte **Editor konfigurace služby WCF**. Potom můžete klikněte pravým tlačítkem na soubor konfigurace a použít **upravit konfigurace WCF** položky kontextové nabídky.  
  
## <a name="see-also"></a>Viz také  
 [Editor konfigurace (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Konfigurace služeb](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
