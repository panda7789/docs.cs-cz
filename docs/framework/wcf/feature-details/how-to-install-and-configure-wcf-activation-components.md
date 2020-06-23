---
title: 'Postupy: Instalace a konfigurace aktivačních komponent WCF'
description: Naučte se, jak nastavit aktivační službu procesů systému Windows (WAS) v systému Windows Vista na hostování služeb WCF, které nekomunikují prostřednictvím protokolu HTTP.
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 84a0dcc4fed28ebd7a536bdabfcdc389be6072d8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246880"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="82590-103">Postupy: Instalace a konfigurace aktivačních komponent WCF</span><span class="sxs-lookup"><span data-stu-id="82590-103">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="82590-104">Toto téma popisuje kroky potřebné k nastavení aktivační služby procesů systému Windows (označované také jako) v systému Windows Vista pro hostování služby Windows Communication Foundation (WCF), které nekomunikují přes síťové protokoly HTTP.</span><span class="sxs-lookup"><span data-stu-id="82590-104">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="82590-105">Následující části popisují kroky pro tuto konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="82590-105">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="82590-106">Nainstalujte (nebo potvrďte instalaci produktu) aktivační komponenty WCF.</span><span class="sxs-lookup"><span data-stu-id="82590-106">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="82590-107">Konfigurace měla podporovat protokol jiného typu než HTTP.</span><span class="sxs-lookup"><span data-stu-id="82590-107">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="82590-108">Následující postup nakonfiguruje Windows Vista pro aktivaci protokolem TCP.</span><span class="sxs-lookup"><span data-stu-id="82590-108">The following procedure configures Windows Vista for TCP activation.</span></span>

<span data-ttu-id="82590-109">Po instalaci a konfiguraci nástroje se podívejte na téma [Postupy: hostování služby WCF ve službě was](how-to-host-a-wcf-service-in-was.md) pro postupy vytvoření služby WCF, která zveřejňuje koncový bod bez http, který využívá.</span><span class="sxs-lookup"><span data-stu-id="82590-109">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="82590-110">Instalace součástí technologie WCF pro aktivaci bez protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="82590-110">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="82590-111">Klikněte na tlačítko **Start** a potom klikněte na **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="82590-111">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="82590-112">Klikněte na **programy**a potom klikněte na **programy a funkce**.</span><span class="sxs-lookup"><span data-stu-id="82590-112">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="82590-113">V nabídce **úlohy** klikněte na **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="82590-113">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="82590-114">Vyhledejte uzel WinFX, vyberte a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="82590-114">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="82590-115">Vyberte pole **součásti technologie WCF bez protokolu HTTP** a uložte nastavení.</span><span class="sxs-lookup"><span data-stu-id="82590-115">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="82590-116">Konfigurace nástroje WAS na podporu aktivace protokolem TCP</span><span class="sxs-lookup"><span data-stu-id="82590-116">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="82590-117">Aby bylo možné podporovat NET. TCP Activation, musí být výchozí webová stránka nejprve svázána s portem NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="82590-117">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="82590-118">To můžete provést pomocí Appcmd.exe, která se instaluje se sadou nástrojů pro správu služby IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="82590-118">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="82590-119">V okně příkazového řádku na úrovni správce spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="82590-119">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="82590-120">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="82590-120">This command is a single line of text.</span></span> <span data-ttu-id="82590-121">Tento příkaz přidá vazbu sítě NET. TCP na výchozí webovou stránku, která naslouchá na portu TCP 808 s libovolným názvem hostitele.</span><span class="sxs-lookup"><span data-stu-id="82590-121">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="82590-122">I když všechny aplikace v rámci lokality sdílí společnou vazbu NET. TCP, každá aplikace může povolit podporu NET. TCP samostatně.</span><span class="sxs-lookup"><span data-stu-id="82590-122">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="82590-123">Pokud chcete pro aplikaci povolit NET. TCP, spusťte následující příkaz z příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="82590-123">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="82590-124">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="82590-124">This command is a single line of text.</span></span> <span data-ttu-id="82590-125">Tento příkaz umožňuje, \<*WCF Application*> aby k aplikaci/aplikace bylo možné pracovat pomocí obou `http://localhost/<WCF Application>` i `net.tcp://localhost/<WCF Application>` .</span><span class="sxs-lookup"><span data-stu-id="82590-125">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="82590-126">Odeberte vazbu na lokalitu NET. TCP, kterou jste přidali pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="82590-126">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="82590-127">Následující dva kroky jsou implementovány v dávkovém souboru s názvem RemoveNetTcpSiteBinding. cmd, který je umístěn v ukázkovém adresáři.</span><span class="sxs-lookup"><span data-stu-id="82590-127">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="82590-128">Ze seznamu povolených protokolů odeberte NET. TCP spuštěním následujícího příkazu v okně příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="82590-128">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="82590-129">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="82590-129">This command is a single line of text.</span></span>

    2. <span data-ttu-id="82590-130">Odeberte vazbu sítě NET. TCP spuštěním následujícího příkazu v okně příkazového řádku se zvýšenými oprávněními:</span><span class="sxs-lookup"><span data-stu-id="82590-130">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="82590-131">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="82590-131">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="82590-132">Odebrání NET. TCP ze seznamu povolených protokolů</span><span class="sxs-lookup"><span data-stu-id="82590-132">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="82590-133">Chcete-li odebrat NET. TCP ze seznamu povolených protokolů, spusťte následující příkaz v okně příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="82590-133">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="82590-134">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="82590-134">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="82590-135">Postup odebrání vazby webu NET. TCP</span><span class="sxs-lookup"><span data-stu-id="82590-135">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="82590-136">Chcete-li odebrat vazbu sítě NET. TCP, spusťte následující příkaz v okně příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="82590-136">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="82590-137">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="82590-137">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="82590-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="82590-138">See also</span></span>

- [<span data-ttu-id="82590-139">Aktivace protokolem TCP</span><span class="sxs-lookup"><span data-stu-id="82590-139">TCP Activation</span></span>](../samples/tcp-activation.md)
- [<span data-ttu-id="82590-140">Aktivace MSMQ</span><span class="sxs-lookup"><span data-stu-id="82590-140">MSMQ Activation</span></span>](../samples/msmq-activation.md)
- [<span data-ttu-id="82590-141">Aktivace pojmenovaného kanálu</span><span class="sxs-lookup"><span data-stu-id="82590-141">NamedPipe Activation</span></span>](../samples/namedpipe-activation.md)
- <span data-ttu-id="82590-142">[Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="82590-142">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
