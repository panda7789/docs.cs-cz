---
title: 'Postupy: Povolení služby sdílení portů Net.TCP'
description: Naučte se konfigurovat službu sdílení portů net TCP pomocí konzoly MMC k povolení NET. TCP, která je ve výchozím nastavení zakázaná.
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 0292559e3befde7f0b00b36aa10a2d9615daf049
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246997"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Postupy: Povolení služby sdílení portů Net.TCP
Windows Communication Foundation (WCF) používá službu systému Windows s názvem služba sdílení portů Net. TCP, která usnadňuje sdílení portů TCP mezi více procesy. Tato služba je nainstalovaná jako součást WCF, ale ve výchozím nastavení není služba standardně povolená, protože je bezpečnostní opatření, takže před prvním použitím je nutné ručně povolit. Toto téma popisuje, jak nakonfigurovat službu sdílení portu NET TCP pomocí modulu snap-in konzoly Microsoft Management Console (MMC).  
  
 Jakmile povolíte službu sdílení portů Net. TCP a spustíte ji ručně, přečtěte si téma [Postupy: Konfigurace služby WCF pro použití sdílení portů](how-to-configure-a-wcf-service-to-use-port-sharing.md) , kde najdete informace o tom, jak službu nakonfigurovat tak, aby používala tuto službu.  
  
 Ukázku, která využívá sdílení NET. TCP://port, najdete v [ukázce sdílení portů Net. TCP](../samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Povolení služby sdílení portů Net. TCP pomocí konzoly MMC  
  
1. V nabídce Start otevřete konzolu pro správu služby buď otevřením okna příkazového řádku, zadáním `services.msc` nebo otevřením příkazu Spustit a zadáním `services.msc` do pole Otevřít.  
  
2. Ve sloupci **název** v seznamu služeb klikněte pravým tlačítkem na **službu sdílení portů Net. TCP**a v nabídce vyberte možnost **vlastnosti** .  
  
3. Chcete-li povolit ruční spuštění služby, v okně **vlastnosti** vyberte kartu **Obecné** a v poli **Typ spuštění** vyberte možnost ručně a potom klikněte na tlačítko **použít**.  
  
4. Službu spustíte tak, že v oblasti stav služby kliknete na tlačítko **Spustit** . Stav služby by nyní měl zobrazovat "spuštěno".  
  
5. Chcete-li se vrátit do seznamu služeb, klikněte na tlačítko **OK**a ukončete konzolu MMC.  
  
## <a name="example"></a>Příklad  
  
## <a name="see-also"></a>Viz také

- [Sdílení portů Net.TCP](net-tcp-port-sharing.md)
- [Konfigurace služby sdílení portů Net.TCP](configuring-the-net-tcp-port-sharing-service.md)
