---
title: Instalace služby Řízení front zpráv (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 42e66029f8538877ded424f72cb6c829444d1ee0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935983"
---
# <a name="installing-message-queuing-msmq"></a>Instalace služby Řízení front zpráv (MSMQ)
Následující postupy ukazují, jak nainstalovat službu Řízení front zpráv 4,0 a službu Řízení front zpráv 3,0.  
  
> [!NOTE]
> Služba Řízení front zpráv 4,0 není dostupná [!INCLUDE[wxp](../../../../includes/wxp-md.md)] v [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]a.  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Instalace služby Řízení front zpráv 4,0 v systému Windows Server 2008 nebo Windows Server 2008 R2  
  
1. V Správce serveru klikněte na **funkce**.  
  
2. V pravém podokně v části **Souhrn funkcí**klikněte na **Přidat funkce**.  
  
3. Ve výsledném okně rozbalte položku **Řízení front zpráv**.  
  
4. Rozbalte položku **služby Řízení front zpráv**.  
  
5. Klikněte na **integrace adresářových služeb** (pro počítače připojené k doméně) a pak klikněte na **Podpora protokolu HTTP**.  
  
6. Klikněte na **Další**a pak klikněte na **nainstalovat**.  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Instalace služby Řízení front zpráv 4,0 v systému Windows 7 nebo Windows Vista  
  
1. Otevřete **Ovládací panely**.  
  
2. Klikněte na **programy** a potom v části **programy a funkce**klikněte na **zapnout nebo vypnout funkce systému Windows**.  
  
3. Rozbalte server MSMQ (Microsoft Message Queue), rozbalte jádro serveru MSMQ (Microsoft Message Queue) a potom zaškrtněte políčka u následujících funkcí služby Řízení front zpráv pro instalaci:  
  
    - Integrace služby MSMQ Active Directory Domain Services (pro počítače připojené k doméně).  
  
    - Podpora protokolu HTTP služby MSMQ.  
  
4. Klikněte na **OK**.  
  
5. Pokud se zobrazí výzva k restartování počítače, kliknutím na tlačítko **OK** dokončete instalaci.  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Instalace služby Řízení front zpráv 3,0 v systému Windows XP a Windows Server 2003  
  
1. Otevřete **Ovládací panely**.  
  
2. Klikněte na **Přidat odebrat programy** a pak klikněte na **přidat součásti systému Windows**.  
  
3. Vyberte možnost Služba Řízení front zpráv a klikněte na tlačítko **Podrobnosti**.  
  
    > [!NOTE]
    >  Pokud používáte [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], vyberte aplikační server pro přístup do služby Řízení front zpráv.  
  
4. Zajistěte, aby byla na stránce podrobností vybrána možnost Podpora služby MSMQ HTTP.  
  
5. Kliknutím na tlačítko **OK** zavřete stránku s podrobnostmi a pak klikněte na tlačítko **Další**. Dokončete instalaci.  
  
6. Pokud se zobrazí výzva k restartování počítače, kliknutím na tlačítko **OK** dokončete instalaci.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k instalaci](../../../../docs/framework/wcf/samples/set-up-instructions.md)
