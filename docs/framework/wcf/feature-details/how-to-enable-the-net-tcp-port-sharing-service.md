---
title: "Postupy: povolení služby Sdílení portů Net.TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9934d198b8f3e30a4dc350c968263851ebeab1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Postupy: povolení služby Sdílení portů Net.TCP
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]používá službu systému Windows s názvem služba Net.TCP Port Sharing usnadňuje sdílení portů TCP více procesy. Tato služba nainstaluje jako součást [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ale služba není povolena ve výchozím nastavení jako bezpečnostní opatření a, musí se zapnout ručně před prvním použití. Toto téma popisuje, jak nakonfigurovat službu Net TCP Port Sharing pomocí modulu snap-In konzoly Microsoft Management Console (MMC).  
  
 Po povolení služby Sdílení portů Net.TCP a jej spustit ručně, najdete v části [postupy: konfigurace použít sdílení portů ve službě WCF](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) informace o tom, jak nakonfigurovat služby k používání této služby.  
  
 Příklad, který používá net.tcp:// sdílení portů, najdete v článku [ukázka sdílení portů Net.TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Chcete-li povolit službu Net.TCP Port Sharing pomocí konzoly MMC  
  
1.  Z nabídky Start, otevřete konzolu pro správu služby tak, že otevřete okno příkazového řádku a zadáte `services.msc` nebo otevřením spustit a zadáním `services.msc` do pole Otevřít.  
  
2.  V **název** sloupec seznamu služeb, klikněte pravým tlačítkem myši **služba Net.Tcp Port Sharing**a vyberte **vlastnosti** z nabídky.  
  
3.  Povolit ruční spuštění služby, v **vlastnosti** vyberte okno **Obecné** kartě a v **typ spuštění** pole vyberte ručně a pak klikněte na **Použít**.  
  
4.  Chcete-li spustit službu, v oblasti stav služby, klikněte na tlačítko **spustit** tlačítko. Stav služby by nyní měla zobrazovat "Začínáme".  
  
5.  Chcete-li se vrátit do seznamu služeb, klikněte na tlačítko **OK**a zavřete konzolu MMC.  
  
## <a name="example"></a>Příklad  
  
## <a name="see-also"></a>Viz také  
 [Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [Konfigurace služby Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
