---
title: Konfigurace vaší aplikace
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 7dfd662fafa636e0fa97f118217ad1786d5aa444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-your-application"></a>Konfigurace vaší aplikace
Windows Communication Foundation (WCF) používá konfigurační systém .NET a umožňuje vám nakonfigurovat služby v oboru počítače a aplikace.  
  
 Nastavení konfigurace definované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou umístěné v `<system.serviceModel>` skupinu oddílů. Další informace o tom, jak nakonfigurovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, najdete v následujících tématech:  
  
-   [Konfigurace služeb](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Nastavení konfigurace definované aplikací, které jsou definovány v `<appSettings>` skupinu oddílů. Další informace o nastavení aplikace v konfiguračních souborech na rozhraní .NET najdete v tématu [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Pomocí editoru konfigurace  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [Nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umožňuje správcům a vývojářům umožňuje vytvořit a upravit nastavení konfigurace pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služeb pomocí grafického uživatelského rozhraní. Pomocí tohoto nástroje můžete spravovat nastavení pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby, chování, služeb a diagnostiky bez přímou úpravou konfiguračních souborů XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Úprava konfiguračních souborů v sadě Visual Studio  
 Chcete-li upravit konfigurační soubor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby projektu v sadě Visual Studio, klikněte pravým tlačítkem v **Průzkumníku řešení** a zvolte **upravit konfigurace WCF** položky kontextové nabídky. Spustí se [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Pokud chcete upravit konfigurační soubor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projektu webové služby v sadě Visual Studio kliknete pravým tlačítkem v **Průzkumníku řešení**, Všimněte si, že **upravit konfigurace WCF** chybí položky kontextové nabídky. Chcete-li vyřešit tento problém, klikněte na tlačítko **nástroje** nabídce a zvolte **Editor konfigurace služby WCF**. Potom můžete klikněte pravým tlačítkem na soubor konfigurace a použít **upravit konfigurace WCF** položky kontextové nabídky.  
  
## <a name="see-also"></a>Viz také  
 [Editor konfigurace (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Konfigurace služeb](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
