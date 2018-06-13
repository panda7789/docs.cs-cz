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
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="6f2e4-102">Instalace služby Řízení front zpráv (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="6f2e4-102">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="6f2e4-103">Následující postupy ukazují, jak nainstalovat 4.0 služby Řízení front zpráv a 3.0 služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-103">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f2e4-104">Zprávy služby Řízení front 4.0 není k dispozici v [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f2e4-104">Message Queuing 4.0 is not available in [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="6f2e4-105">Chcete-li nainstalovat 4.0 služby Řízení front zpráv v systému Windows Server 2008 nebo Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="6f2e4-105">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1.  <span data-ttu-id="6f2e4-106">Ve Správci serveru klikněte na tlačítko **funkce**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-106">In Server Manager, click **Features**.</span></span>  
  
2.  <span data-ttu-id="6f2e4-107">V pravém podokně v části **Souhrn funkcí**, klikněte na tlačítko **přidat funkce**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-107">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3.  <span data-ttu-id="6f2e4-108">V okně výsledné rozbalte **služby Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-108">In the resulting window, expand **Message Queuing**.</span></span>  
  
4.  <span data-ttu-id="6f2e4-109">Rozbalte položku **služby Řízení front zpráv**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-109">Expand **Message Queuing Services**.</span></span>  
  
5.  <span data-ttu-id="6f2e4-110">Klikněte na tlačítko **Integrace adresářové služby** (pro počítače připojené k doméně), pak klikněte na **podpora protokolu HTTP**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-110">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6.  <span data-ttu-id="6f2e4-111">Klikněte na tlačítko **Další**, pak klikněte na tlačítko **nainstalovat**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-111">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="6f2e4-112">Chcete-li nainstalovat 4.0 služby Řízení front zpráv na Windows 7 nebo Windows Vista</span><span class="sxs-lookup"><span data-stu-id="6f2e4-112">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1.  <span data-ttu-id="6f2e4-113">Otevřete **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-113">Open **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="6f2e4-114">Klikněte na tlačítko **programy** a pak v části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-114">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3.  <span data-ttu-id="6f2e4-115">Rozbalte Server Microsoft Message Queue (MSMQ), rozbalte možnost jádra serveru Microsoft Message Queue (MSMQ) a pak zaškrtněte políčka pro následující funkce služby Řízení front zpráv k instalaci:</span><span class="sxs-lookup"><span data-stu-id="6f2e4-115">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    -   <span data-ttu-id="6f2e4-116">Active Directory Domain Services integrována (pro počítače připojené k doméně).</span><span class="sxs-lookup"><span data-stu-id="6f2e4-116">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    -   <span data-ttu-id="6f2e4-117">Podpora protokolu HTTP služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-117">MSMQ HTTP Support.</span></span>  
  
4.  <span data-ttu-id="6f2e4-118">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="6f2e4-119">Pokud se zobrazí výzva k restartování počítače, klikněte na tlačítko **OK** k dokončení instalace.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-119">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="6f2e4-120">Chcete-li nainstalovat 3.0 služby Řízení front zpráv v systému Windows XP a Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="6f2e4-120">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1.  <span data-ttu-id="6f2e4-121">Otevřete **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-121">Open **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="6f2e4-122">Klikněte na tlačítko **odebrat programy** a pak klikněte na **přidat součásti systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-122">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3.  <span data-ttu-id="6f2e4-123">Vyberte služby Řízení front zpráv a klikněte na **podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-123">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f2e4-124">Pokud používáte [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], vyberte aplikační Server pro přístup k služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-124">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], select Application Server to access Message Queuing.</span></span>  
  
4.  <span data-ttu-id="6f2e4-125">Zajistěte, aby možnost zvolené MSMQ podpora protokolu HTTP na stránce Podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-125">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5.  <span data-ttu-id="6f2e4-126">Klikněte na tlačítko **OK** opustíte stránce s podrobnostmi o, a pak klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-126">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="6f2e4-127">Dokončete instalaci.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-127">Complete the installation.</span></span>  
  
6.  <span data-ttu-id="6f2e4-128">Pokud se zobrazí výzva k restartování počítače, klikněte na tlačítko **OK** k dokončení instalace.</span><span class="sxs-lookup"><span data-stu-id="6f2e4-128">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f2e4-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f2e4-129">See Also</span></span>  
 [<span data-ttu-id="6f2e4-130">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="6f2e4-130">Set-Up Instructions</span></span>](../../../../docs/framework/wcf/samples/set-up-instructions.md)
