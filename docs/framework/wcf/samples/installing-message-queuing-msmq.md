---
title: Instalace služby Řízení front zpráv (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 1bf79ed5dbcb9f2ace903260cc440e77df3aef09
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592291"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="6ad3f-102">Instalace služby Řízení front zpráv (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="6ad3f-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="6ad3f-103">Následující postupy ukazují, jak nainstalovat službu Řízení front zpráv 4,0 a službu Řízení front zpráv 3,0.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ad3f-104">V systému Windows XP a Windows Server 2003 není služba Řízení front zpráv 4,0 k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-104">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="6ad3f-105">Instalace služby Řízení front zpráv 4,0 v systému Windows Server 2008 nebo Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="6ad3f-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="6ad3f-106">V Správce serveru klikněte na **funkce**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-106">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="6ad3f-107">V pravém podokně v části **Souhrn funkcí**klikněte na **Přidat funkce**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="6ad3f-108">Ve výsledném okně rozbalte položku **Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="6ad3f-109">Rozbalte položku **služby Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-109">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="6ad3f-110">Klikněte na **integrace adresářových služeb** (pro počítače připojené k doméně) a pak klikněte na **Podpora protokolu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="6ad3f-111">Klikněte na **Další**a pak klikněte na **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="6ad3f-112">Instalace služby Řízení front zpráv 4,0 v systému Windows 7 nebo Windows Vista</span><span class="sxs-lookup"><span data-stu-id="6ad3f-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="6ad3f-113">Otevřete **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-113">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="6ad3f-114">Klikněte na **programy** a potom v části **programy a funkce**klikněte na **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="6ad3f-115">Rozbalte server MSMQ (Microsoft Message Queue), rozbalte jádro serveru MSMQ (Microsoft Message Queue) a potom zaškrtněte políčka u následujících funkcí služby Řízení front zpráv pro instalaci:</span><span class="sxs-lookup"><span data-stu-id="6ad3f-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="6ad3f-116">Integrace služby MSMQ Active Directory Domain Services (pro počítače připojené k doméně).</span><span class="sxs-lookup"><span data-stu-id="6ad3f-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="6ad3f-117">Podpora protokolu HTTP služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-117">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="6ad3f-118">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-118">Click **OK**.</span></span>  
  
5. <span data-ttu-id="6ad3f-119">Pokud se zobrazí výzva k restartování počítače, kliknutím na tlačítko **OK** dokončete instalaci.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="6ad3f-120">Instalace služby Řízení front zpráv 3,0 v systému Windows XP a Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="6ad3f-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="6ad3f-121">Otevřete **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-121">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="6ad3f-122">Klikněte na **Přidat odebrat programy** a pak klikněte na **přidat součásti systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="6ad3f-123">Vyberte možnost Služba Řízení front zpráv a klikněte na tlačítko **Podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6ad3f-124">Pokud používáte systém Windows Server 2003, vyberte aplikační server pro přístup do služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-124">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="6ad3f-125">Zajistěte, aby byla na stránce podrobností vybrána možnost Podpora služby MSMQ HTTP.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="6ad3f-126">Kliknutím na tlačítko **OK** zavřete stránku s podrobnostmi a pak klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="6ad3f-127">Dokončete instalaci.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-127">Complete the installation.</span></span>  
  
6. <span data-ttu-id="6ad3f-128">Pokud se zobrazí výzva k restartování počítače, kliknutím na tlačítko **OK** dokončete instalaci.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad3f-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ad3f-129">See also</span></span>

- [<span data-ttu-id="6ad3f-130">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="6ad3f-130">Set-Up Instructions</span></span>](set-up-instructions.md)
