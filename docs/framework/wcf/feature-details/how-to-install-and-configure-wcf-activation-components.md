---
title: 'Postupy: Instalace a konfigurace aktivačních komponent WCF'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: f7a846b076691394cb855e4978e890cdcac76eb2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597030"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="24b5b-102">Postupy: Instalace a konfigurace aktivačních komponent WCF</span><span class="sxs-lookup"><span data-stu-id="24b5b-102">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="24b5b-103">Toto téma popisuje kroky potřebné k nastavení aktivační služby procesů systému Windows (označované také jako) v systému Windows Vista pro hostování služby Windows Communication Foundation (WCF), které nekomunikují přes síťové protokoly HTTP.</span><span class="sxs-lookup"><span data-stu-id="24b5b-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="24b5b-104">Následující části popisují kroky pro tuto konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="24b5b-104">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="24b5b-105">Nainstalujte (nebo potvrďte instalaci produktu) aktivační komponenty WCF.</span><span class="sxs-lookup"><span data-stu-id="24b5b-105">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="24b5b-106">Konfigurace měla podporovat protokol jiného typu než HTTP.</span><span class="sxs-lookup"><span data-stu-id="24b5b-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="24b5b-107">Následující postup nakonfiguruje Windows Vista pro aktivaci protokolem TCP.</span><span class="sxs-lookup"><span data-stu-id="24b5b-107">The following procedure configures Windows Vista for TCP activation.</span></span>

<span data-ttu-id="24b5b-108">Po instalaci a konfiguraci nástroje se podívejte na téma [Postupy: hostování služby WCF ve službě was](how-to-host-a-wcf-service-in-was.md) pro postupy vytvoření služby WCF, která zveřejňuje koncový bod bez http, který využívá.</span><span class="sxs-lookup"><span data-stu-id="24b5b-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="24b5b-109">Instalace součástí technologie WCF pro aktivaci bez protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="24b5b-109">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="24b5b-110">Klikněte na tlačítko **Start** a potom klikněte na **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="24b5b-110">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="24b5b-111">Klikněte na **programy**a potom klikněte na **programy a funkce**.</span><span class="sxs-lookup"><span data-stu-id="24b5b-111">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="24b5b-112">V nabídce **úlohy** klikněte na **zapnout nebo vypnout funkce systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="24b5b-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="24b5b-113">Vyhledejte uzel WinFX, vyberte a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="24b5b-113">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="24b5b-114">Vyberte pole **součásti technologie WCF bez protokolu HTTP** a uložte nastavení.</span><span class="sxs-lookup"><span data-stu-id="24b5b-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="24b5b-115">Konfigurace nástroje WAS na podporu aktivace protokolem TCP</span><span class="sxs-lookup"><span data-stu-id="24b5b-115">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="24b5b-116">Aby bylo možné podporovat NET. TCP Activation, musí být výchozí webová stránka nejprve svázána s portem NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="24b5b-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="24b5b-117">To můžete provést pomocí nástroje Appcmd. exe, který se instaluje se sadou nástrojů pro správu služby IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="24b5b-117">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="24b5b-118">V okně příkazového řádku na úrovni správce spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="24b5b-118">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="24b5b-119">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="24b5b-119">This command is a single line of text.</span></span> <span data-ttu-id="24b5b-120">Tento příkaz přidá vazbu sítě NET. TCP na výchozí webovou stránku, která naslouchá na portu TCP 808 s libovolným názvem hostitele.</span><span class="sxs-lookup"><span data-stu-id="24b5b-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="24b5b-121">I když všechny aplikace v rámci lokality sdílí společnou vazbu NET. TCP, každá aplikace může povolit podporu NET. TCP samostatně.</span><span class="sxs-lookup"><span data-stu-id="24b5b-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="24b5b-122">Pokud chcete pro aplikaci povolit NET. TCP, spusťte následující příkaz z příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="24b5b-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="24b5b-123">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="24b5b-123">This command is a single line of text.</span></span> <span data-ttu-id="24b5b-124">Tento příkaz umožňuje, \<*WCF Application*> aby k aplikaci/aplikace bylo možné pracovat pomocí obou `http://localhost/<WCF Application>` i `net.tcp://localhost/<WCF Application>` .</span><span class="sxs-lookup"><span data-stu-id="24b5b-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="24b5b-125">Odeberte vazbu na lokalitu NET. TCP, kterou jste přidali pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="24b5b-125">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="24b5b-126">Následující dva kroky jsou implementovány v dávkovém souboru s názvem RemoveNetTcpSiteBinding. cmd, který je umístěn v ukázkovém adresáři.</span><span class="sxs-lookup"><span data-stu-id="24b5b-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="24b5b-127">Ze seznamu povolených protokolů odeberte NET. TCP spuštěním následujícího příkazu v okně příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="24b5b-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="24b5b-128">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="24b5b-128">This command is a single line of text.</span></span>

    2. <span data-ttu-id="24b5b-129">Odeberte vazbu sítě NET. TCP spuštěním následujícího příkazu v okně příkazového řádku se zvýšenými oprávněními:</span><span class="sxs-lookup"><span data-stu-id="24b5b-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="24b5b-130">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="24b5b-130">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="24b5b-131">Odebrání NET. TCP ze seznamu povolených protokolů</span><span class="sxs-lookup"><span data-stu-id="24b5b-131">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="24b5b-132">Chcete-li odebrat NET. TCP ze seznamu povolených protokolů, spusťte následující příkaz v okně příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="24b5b-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="24b5b-133">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="24b5b-133">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="24b5b-134">Postup odebrání vazby webu NET. TCP</span><span class="sxs-lookup"><span data-stu-id="24b5b-134">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="24b5b-135">Chcete-li odebrat vazbu sítě NET. TCP, spusťte následující příkaz v okně příkazového řádku na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="24b5b-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="24b5b-136">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="24b5b-136">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="24b5b-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="24b5b-137">See also</span></span>

- [<span data-ttu-id="24b5b-138">Aktivace protokolem TCP</span><span class="sxs-lookup"><span data-stu-id="24b5b-138">TCP Activation</span></span>](../samples/tcp-activation.md)
- [<span data-ttu-id="24b5b-139">Aktivace MSMQ</span><span class="sxs-lookup"><span data-stu-id="24b5b-139">MSMQ Activation</span></span>](../samples/msmq-activation.md)
- [<span data-ttu-id="24b5b-140">Aktivace pojmenovaného kanálu</span><span class="sxs-lookup"><span data-stu-id="24b5b-140">NamedPipe Activation</span></span>](../samples/namedpipe-activation.md)
- <span data-ttu-id="24b5b-141">[Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="24b5b-141">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
