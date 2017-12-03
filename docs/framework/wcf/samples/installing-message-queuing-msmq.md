---
title: "Instalace služby Řízení front zpráv (MSMQ)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6a7ee646c2f6b20410c493ee139f08d11fc55d54
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
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
