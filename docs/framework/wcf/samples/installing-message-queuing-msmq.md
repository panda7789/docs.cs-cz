---
title: Instalace služby Řízení front zpráv (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 64736f8f0a34a53658dd2838738a3d36b3891d2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954944"
---
# <a name="installing-message-queuing-msmq"></a>Instalace služby Řízení front zpráv (MSMQ)
Následující postupy ukazují, jak nainstalovat 4.0 služby Řízení front zpráv a 3.0 služby Řízení front zpráv.  
  
> [!NOTE]
>  Zprávy služby Řízení front 4.0 není k dispozici v [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>K instalaci na Windows Server 2008 nebo Windows Server 2008 R2 4.0 služby Řízení front zpráv  
  
1. Ve Správci serveru klikněte na tlačítko **funkce**.  
  
2. V pravém podokně v části **Souhrn funkcí**, klikněte na tlačítko **přidat funkce**.  
  
3. V okně výsledný rozbalte **služby Řízení front zpráv**.  
  
4. Rozbalte **služba Řízení front zpráv**.  
  
5. Klikněte na tlačítko **Integrace adresářové služby** (pro počítače připojené k doméně), potom klikněte na **podpora protokolu HTTP**.  
  
6. Klikněte na tlačítko **Další**, pak klikněte na tlačítko **nainstalovat**.  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>K instalaci na Windows 7 nebo Windows Vista 4.0 služby Řízení front zpráv  
  
1. Otevřete **Ovládací panely**.  
  
2. Klikněte na tlačítko **programy** a pak v části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce Windows**.  
  
3. Rozbalíte Server Microsoft Message Queue (MSMQ), rozbalte Server Core Microsoft Message Queue (MSMQ) a poté zaškrtněte políčka pro následující funkce služby Řízení front zpráv k instalaci:  
  
    - MSMQ domény služby integrace služby Active Directory (pro počítače připojené k doméně).  
  
    - MSMQ HTTP Support.  
  
4. Klikněte na **OK**.  
  
5. Pokud se zobrazí výzva k restartování počítače, klikněte na tlačítko **OK** k dokončení instalace.  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>K instalaci na Windows XP a Windows Server 2003 3.0 služby Řízení front zpráv  
  
1. Otevřete **Ovládací panely**.  
  
2. Klikněte na tlačítko **přidat nebo odebrat programy** a potom klikněte na tlačítko **přidat součásti Windows**.  
  
3. Vyberte služby Řízení front zpráv a klikněte na tlačítko **podrobnosti**.  
  
    > [!NOTE]
    >  Pokud používáte [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], vyberte aplikační Server pro přístup k řízení front zpráv.  
  
4. Ujistěte se, že možnost vybraných na stránce s podrobnostmi MSMQ – podpora protokolu HTTP.  
  
5. Klikněte na tlačítko **OK** opustili stránku podrobností, a potom klikněte na **Další**. Dokončete instalaci.  
  
6. Pokud se zobrazí výzva k restartování počítače, klikněte na tlačítko **OK** k dokončení instalace.  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k instalaci](../../../../docs/framework/wcf/samples/set-up-instructions.md)
