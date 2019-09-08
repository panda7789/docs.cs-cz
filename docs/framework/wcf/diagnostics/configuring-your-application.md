---
title: Konfigurace vaší aplikace
ms.date: 03/30/2017
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
ms.openlocfilehash: 4e19e4d0ecb6bc90402f99dddd280ee1dbcf7ea0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798146"
---
# <a name="configuring-your-application"></a>Konfigurace vaší aplikace
Windows Communication Foundation (WCF) používá konfigurační systém .NET a umožňuje nakonfigurovat služby v oboru počítače i aplikace.  
  
 Nastavení konfigurace definované službou WCF se nachází ve `<system.serviceModel>` skupině oddíl. Další informace o tom, jak nakonfigurovat službu WCF, najdete v následujících tématech:  
  
- [Konfigurace služeb](../configuring-services.md)  
  
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Nastavení konfigurace definovaná aplikací jsou definovaná ve `<appSettings>` skupině oddílů. Další informace o nastavení aplikace v konfiguračních souborech .NET naleznete v tématu [ \<appSettings >](https://go.microsoft.com/fwlink/?LinkId=95159).  
  
## <a name="using-the-configuration-editor"></a>Použití editoru konfigurace  
 [Nástroj Editor konfigurace služby WCF (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) umožňuje správcům a vývojářům vytvářet a upravovat nastavení konfigurace služeb WCF pomocí grafického uživatelského rozhraní. Pomocí tohoto nástroje můžete spravovat nastavení vazeb WCF, chování, služeb a diagnostiky bez nutnosti přímo upravovat konfigurační soubory XML.  
  
## <a name="editing-configuration-files-in-visual-studio"></a>Úpravy konfiguračních souborů v aplikaci Visual Studio  
 Chcete-li upravit konfigurační soubor projektu služby WCF v aplikaci Visual Studio, klikněte na něj pravým tlačítkem **Průzkumník řešení** a vyberte položku **Upravit konfiguraci WCF konfigurace** položky nabídky. Spustí se [Nástroj Configuration Editor (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md).  
  
> [!NOTE]
> Pokud upravíte konfigurační soubor projektu webové služby WCF v aplikaci Visual Studio tak, že na něj kliknete pravým tlačítkem myši v **Průzkumník řešení**, Všimněte si, že chybí položka místní nabídky pro **úpravu konfigurace WCF** . Pokud chcete tento problém vyřešit, klikněte na nabídku **nástroje** a vyberte **Editor konfigurace služby WCF**. Potom můžete kliknout pravým tlačítkem na konfigurační soubor a použít položku místní nabídky **Upravit konfiguraci WCF** .  
  
## <a name="see-also"></a>Viz také:

- [Editor konfigurace (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)
- [Konfigurace služeb](../configuring-services.md)
- [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md)
