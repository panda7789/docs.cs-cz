---
title: Konfigurace vaší aplikace
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 9a1365bb567c552fb087e67a10e48fe0bc2da873
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652039"
---
# <a name="configuring-your-application"></a>Konfigurace vaší aplikace
Windows Communication Foundation (WCF) využívá konfigurační systém .NET a umožňuje vám nakonfigurovat služby v počítači a aplikační oboru.  
  
 Nastavení konfigurace určené WCF se nachází v `<system.serviceModel>` skupiny oddílů. Další informace o tom, jak nakonfigurovat službu WCF naleznete v následujících tématech:  
  
- [Konfigurace služeb](../../../../docs/framework/wcf/configuring-services.md)  
  
- [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Nastavení konfigurace definované aplikací, které jsou definovány v `<appSettings>` skupiny oddílů. Další informace o nastavení aplikace v .NET konfigurační soubory, naleznete v tématu [ \<appSettings >](https://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Pomocí editoru konfigurace  
 WCF [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) umožňuje správcům a vývojářům umožňuje vytvářet a upravovat nastavení konfigurace pro služby WCF pomocí grafického uživatelského rozhraní. Pomocí tohoto nástroje můžete spravovat nastavení pro vazby WCF, chování, služby a diagnostické nástroje bez přímou úpravou konfiguračních souborů XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Úprava konfiguračních souborů v sadě Visual Studio  
 Úprava konfiguračního souboru projektu služby WCF v sadě Visual Studio, klikněte pravým tlačítkem myši klikněte na něj v **Průzkumníka řešení** a zvolte **upravit konfigurace WCF** položka kontextové nabídky. Tím se spustí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
>  Pokud upravíte kliknutím pravým tlačítkem myši v konfiguračním souboru projektu webové služby WCF v sadě Visual Studio **Průzkumníka řešení**, Všimněte si, že **upravit konfigurace WCF** chybí položka kontextové nabídky. Chcete-li vyřešit tento problém, klikněte na tlačítko **nástroje** nabídky a zvolte **Editor konfigurace služby WCF**. Poté klikněte pravým tlačítkem na konfigurační soubor a použít **upravit konfigurace WCF** položka kontextové nabídky.  
  
## <a name="see-also"></a>Viz také:

- [Editor konfigurace (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [Konfigurace služeb](../../../../docs/framework/wcf/configuring-services.md)
- [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)
