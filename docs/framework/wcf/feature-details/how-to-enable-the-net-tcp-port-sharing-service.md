---
title: 'Postupy: Povolení Služby sdílení portů Net.TCP'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 20db0ef427a5e791bd6b8dcef90bf7911ae0d4a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343477"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Postupy: Povolení Služby sdílení portů Net.TCP
Windows Communication Foundation (WCF) používá službu Windows volá služba Sdílení portů Net.TCP k usnadnění sdílení portů TCP napříč více procesy. Tato služba je nainstalován jako součást služby WCF, ale služba není povolená ve výchozím nastavení jako bezpečnostní opatření a proto musíte ručně povolit před prvním použitím. Toto téma popisuje, jak nakonfigurovat službu Net TCP Port Sharing pomocí modulu snap-In konzoly Microsoft Management Console (MMC).  
  
 Po povolení služby Sdílení portů Net.TCP a spustit ručně, najdete v článku [jak: Konfigurace použití sdílení portů ve službě WCF](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) informace o tom, jak nakonfigurovat svoji službu pro tuto službu používat.  
  
 Ukázku, která používá net.tcp:// sdílení portů najdete v tématu [ukázka sdílení portů Net.TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Chcete-li povolit službu Net.TCP Port Sharing pomocí konzoly MMC  
  
1. Z nabídky Start otevřete konzolu pro správu služeb tak, že otevřete okno příkazového řádku a zadáte `services.msc` nebo otevřením spustit a zadáním `services.msc` do pole.  
  
2. V **název** klikněte pravým tlačítkem na sloupec v seznamu služeb, **služba Sdílení portů Net.Tcp**a vyberte **vlastnosti** z nabídky.  
  
3. Povolit ruční spuštění služby, v **vlastnosti** vyberte okno **Obecné** kartu a v **typ spouštění** vyberte ručně a klepněte na tlačítko **Použít**.  
  
4. Chcete-li spustit službu, v oblasti stavu služby, klikněte na tlačítko **Start** tlačítko. Stav služby nyní zobrazeno "Začínáme".  
  
5. Chcete-li vrátit do seznamu služeb, klikněte na tlačítko **OK**a ukončete konzolu MMC.  
  
## <a name="example"></a>Příklad  
  
## <a name="see-also"></a>Viz také:

- [Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Konfigurace služby sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
