---
title: Instalace služby Řízení front zpráv (MSMQ)
description: Naučte se instalovat službu Řízení front zpráv 4,0 a službu Řízení front zpráv 3,0 pro použití s ukázkami WFC jako součást jednorázového postupu nastavení.
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 0d0cb87b40b1cb11eb7692c2fa1e890ec815b13d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244462"
---
# <a name="installing-message-queuing-msmq"></a>Instalace služby Řízení front zpráv (MSMQ)
Následující postupy ukazují, jak nainstalovat službu Řízení front zpráv 4,0 a službu Řízení front zpráv 3,0.  
  
> [!NOTE]
> V systému Windows XP a Windows Server 2003 není služba Řízení front zpráv 4,0 k dispozici.  
  
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
    > Pokud používáte systém Windows Server 2003, vyberte aplikační server pro přístup do služby Řízení front zpráv.  
  
4. Zajistěte, aby byla na stránce podrobností vybrána možnost Podpora služby MSMQ HTTP.  
  
5. Kliknutím na tlačítko **OK** zavřete stránku s podrobnostmi a pak klikněte na tlačítko **Další**. Dokončete instalaci.  
  
6. Pokud se zobrazí výzva k restartování počítače, kliknutím na tlačítko **OK** dokončete instalaci.  
  
## <a name="see-also"></a>Viz také

- [Pokyny k instalaci](set-up-instructions.md)
