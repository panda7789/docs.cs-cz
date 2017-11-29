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
# <a name="configuring-your-application"></a>Konfigurace vaší aplikace
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]používá konfigurační systém .NET a umožňuje vám nakonfigurovat služby v oboru počítače a aplikace.  
  
 Nastavení konfigurace definované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou umístěné v `<system.serviceModel>` skupinu oddílů. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Postup konfigurace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, najdete v následujících tématech:  
  
-   [Konfigurace služeb](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Nastavení konfigurace definované aplikací, které jsou definovány v `<appSettings>` skupinu oddílů. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]nastavení aplikace v rozhraní .NET konfigurační soubory, najdete v části [ \<appSettings >](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Pomocí editoru konfigurace  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [Nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umožňuje správcům a vývojářům umožňuje vytvořit a upravit nastavení konfigurace pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služeb pomocí grafického uživatelského rozhraní. Pomocí tohoto nástroje můžete spravovat nastavení pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby, chování, služeb a diagnostiky bez přímou úpravou konfiguračních souborů XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Úprava konfiguračních souborů v sadě Visual Studio  
 Chcete-li upravit konfigurační soubor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projektu služby v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], klikněte pravým tlačítkem v **Průzkumníku řešení** a zvolte **upravit konfigurace WCF** položky kontextové nabídky. Spustí se [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Pokud chcete upravit konfigurační soubor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projekt webové služby v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] kliknutím pravým tlačítkem myši v **Průzkumníku řešení**, Všimněte si, že **upravit konfigurace WCF** chybí položky kontextové nabídky . Chcete-li vyřešit tento problém, klikněte na tlačítko **nástroje** nabídce a zvolte **Editor konfigurace služby WCF**. Potom můžete klikněte pravým tlačítkem na soubor konfigurace a použít **upravit konfigurace WCF** položky kontextové nabídky.  
  
## <a name="see-also"></a>Viz také  
 [Nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Konfigurace služeb](../../../../docs/framework/wcf/configuring-services.md)  
 [\<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
