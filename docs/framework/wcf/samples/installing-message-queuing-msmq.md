---
title: Instalace služby Řízení front zpráv (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: b54fab13d644cafda8a070280d672c60cf71b675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501465"
---
# <a name="installing-message-queuing-msmq"></a>Instalace služby Řízení front zpráv (MSMQ)
Následující postupy ukazují, jak nainstalovat 4.0 služby Řízení front zpráv a 3.0 služby Řízení front zpráv.  
  
> [!NOTE]
>  Zprávy služby Řízení front 4.0 není k dispozici v [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Chcete-li nainstalovat 4.0 služby Řízení front zpráv v systému Windows Server 2008 nebo Windows Server 2008 R2  
  
1.  Ve Správci serveru klikněte na tlačítko **funkce**.  
  
2.  V pravém podokně v části **Souhrn funkcí**, klikněte na tlačítko **přidat funkce**.  
  
3.  V okně výsledné rozbalte **služby Řízení front zpráv**.  
  
4.  Rozbalte položku **služby Řízení front zpráv**.  
  
5.  Klikněte na tlačítko **Integrace adresářové služby** (pro počítače připojené k doméně), pak klikněte na **podpora protokolu HTTP**.  
  
6.  Klikněte na tlačítko **Další**, pak klikněte na tlačítko **nainstalovat**.  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Chcete-li nainstalovat 4.0 služby Řízení front zpráv na Windows 7 nebo Windows Vista  
  
1.  Otevřete **ovládací panely**.  
  
2.  Klikněte na tlačítko **programy** a pak v části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce systému Windows**.  
  
3.  Rozbalte Server Microsoft Message Queue (MSMQ), rozbalte možnost jádra serveru Microsoft Message Queue (MSMQ) a pak zaškrtněte políčka pro následující funkce služby Řízení front zpráv k instalaci:  
  
    -   Active Directory Domain Services integrována (pro počítače připojené k doméně).  
  
    -   Podpora protokolu HTTP služby MSMQ.  
  
4.  Click **OK**.  
  
5.  Pokud se zobrazí výzva k restartování počítače, klikněte na tlačítko **OK** k dokončení instalace.  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Chcete-li nainstalovat 3.0 služby Řízení front zpráv v systému Windows XP a Windows Server 2003  
  
1.  Otevřete **ovládací panely**.  
  
2.  Klikněte na tlačítko **odebrat programy** a pak klikněte na **přidat součásti systému Windows**.  
  
3.  Vyberte služby Řízení front zpráv a klikněte na **podrobnosti**.  
  
    > [!NOTE]
    >  Pokud používáte [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], vyberte aplikační Server pro přístup k služby Řízení front zpráv.  
  
4.  Zajistěte, aby možnost zvolené MSMQ podpora protokolu HTTP na stránce Podrobnosti.  
  
5.  Klikněte na tlačítko **OK** opustíte stránce s podrobnostmi o, a pak klikněte na **Další**. Dokončete instalaci.  
  
6.  Pokud se zobrazí výzva k restartování počítače, klikněte na tlačítko **OK** k dokončení instalace.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k instalaci](../../../../docs/framework/wcf/samples/set-up-instructions.md)
