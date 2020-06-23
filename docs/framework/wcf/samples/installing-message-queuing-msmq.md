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
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="c2594-103">Instalace služby Řízení front zpráv (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="c2594-103">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="c2594-104">Následující postupy ukazují, jak nainstalovat službu Řízení front zpráv 4,0 a službu Řízení front zpráv 3,0.</span><span class="sxs-lookup"><span data-stu-id="c2594-104">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2594-105">V systému Windows XP a Windows Server 2003 není služba Řízení front zpráv 4,0 k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c2594-105">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="c2594-106">Instalace služby Řízení front zpráv 4,0 v systému Windows Server 2008 nebo Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c2594-106">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="c2594-107">V Správce serveru klikněte na **funkce**.</span><span class="sxs-lookup"><span data-stu-id="c2594-107">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="c2594-108">V pravém podokně v části **Souhrn funkcí**klikněte na **Přidat funkce**.</span><span class="sxs-lookup"><span data-stu-id="c2594-108">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="c2594-109">Ve výsledném okně rozbalte položku **Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="c2594-109">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="c2594-110">Rozbalte položku **služby Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="c2594-110">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="c2594-111">Klikněte na **integrace adresářových služeb** (pro počítače připojené k doméně) a pak klikněte na **Podpora protokolu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="c2594-111">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="c2594-112">Klikněte na **Další**a pak klikněte na **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="c2594-112">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="c2594-113">Instalace služby Řízení front zpráv 4,0 v systému Windows 7 nebo Windows Vista</span><span class="sxs-lookup"><span data-stu-id="c2594-113">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="c2594-114">Otevřete **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="c2594-114">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="c2594-115">Klikněte na **programy** a potom v části **programy a funkce**klikněte na **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="c2594-115">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="c2594-116">Rozbalte server MSMQ (Microsoft Message Queue), rozbalte jádro serveru MSMQ (Microsoft Message Queue) a potom zaškrtněte políčka u následujících funkcí služby Řízení front zpráv pro instalaci:</span><span class="sxs-lookup"><span data-stu-id="c2594-116">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="c2594-117">Integrace služby MSMQ Active Directory Domain Services (pro počítače připojené k doméně).</span><span class="sxs-lookup"><span data-stu-id="c2594-117">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="c2594-118">Podpora protokolu HTTP služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c2594-118">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="c2594-119">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="c2594-119">Click **OK**.</span></span>  
  
5. <span data-ttu-id="c2594-120">Pokud se zobrazí výzva k restartování počítače, kliknutím na tlačítko **OK** dokončete instalaci.</span><span class="sxs-lookup"><span data-stu-id="c2594-120">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="c2594-121">Instalace služby Řízení front zpráv 3,0 v systému Windows XP a Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="c2594-121">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="c2594-122">Otevřete **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="c2594-122">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="c2594-123">Klikněte na **Přidat odebrat programy** a pak klikněte na **přidat součásti systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="c2594-123">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="c2594-124">Vyberte možnost Služba Řízení front zpráv a klikněte na tlačítko **Podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="c2594-124">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c2594-125">Pokud používáte systém Windows Server 2003, vyberte aplikační server pro přístup do služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="c2594-125">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="c2594-126">Zajistěte, aby byla na stránce podrobností vybrána možnost Podpora služby MSMQ HTTP.</span><span class="sxs-lookup"><span data-stu-id="c2594-126">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="c2594-127">Kliknutím na tlačítko **OK** zavřete stránku s podrobnostmi a pak klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="c2594-127">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="c2594-128">Dokončete instalaci.</span><span class="sxs-lookup"><span data-stu-id="c2594-128">Complete the installation.</span></span>  
  
6. <span data-ttu-id="c2594-129">Pokud se zobrazí výzva k restartování počítače, kliknutím na tlačítko **OK** dokončete instalaci.</span><span class="sxs-lookup"><span data-stu-id="c2594-129">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2594-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2594-130">See also</span></span>

- [<span data-ttu-id="c2594-131">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="c2594-131">Set-Up Instructions</span></span>](set-up-instructions.md)
