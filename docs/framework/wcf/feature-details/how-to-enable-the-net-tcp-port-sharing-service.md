---
title: 'Postupy: povolení služby Sdílení portů Net.TCP'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 4b5a18e11d9fc15f23b5353883a63d838face58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490757"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Postupy: povolení služby Sdílení portů Net.TCP
Windows Communication Foundation (WCF) používá služba systému Windows s názvem služba Net.TCP Port Sharing usnadňuje sdílení portů TCP více procesy. Tato služba je nainstalován jako součást služby WCF, ale služba není povoleno ve výchozím nastavení jako bezpečnostní opatření a proto musí se zapnout ručně před první použití. Toto téma popisuje, jak nakonfigurovat službu Net TCP Port Sharing pomocí modulu snap-In konzoly Microsoft Management Console (MMC).  
  
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
 [Konfigurace služby sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
