---
title: "Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4b9496d471ca262e640c927619ccea8e4b4f4145
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="f3a34-102">Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)</span><span class="sxs-lookup"><span data-stu-id="f3a34-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="f3a34-103">Ke spuštění ukázky, které zabezpečeně komunikovat s Internetové informační služby (IIS), musíte vytvořit a nainstalovat certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="f3a34-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="f3a34-104">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="f3a34-104">Step 1.</span></span> <span data-ttu-id="f3a34-105">Vytváření certifikátů</span><span class="sxs-lookup"><span data-stu-id="f3a34-105">Creating Certificates</span></span>  
 <span data-ttu-id="f3a34-106">Chcete-li vytvořit certifikát pro počítač, otevřete příkazový řádek sady Visual Studio s oprávněními správce a spusťte Setup.bat, která je zahrnuta v každé vzorků, které používají zabezpečené komunikace se službou IIS.</span><span class="sxs-lookup"><span data-stu-id="f3a34-106">To create a certificate for your computer, open a Visual Studio command prompt with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="f3a34-107">Ujistěte se, že cesta obsahuje složku, která obsahuje Makecert.exe předtím, než spustíte tento dávkový soubor.</span><span class="sxs-lookup"><span data-stu-id="f3a34-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="f3a34-108">Tento příkaz slouží k vytvoření certifikátu v Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="f3a34-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="f3a34-109">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="f3a34-109">Step 2.</span></span> <span data-ttu-id="f3a34-110">Instalace certifikátů</span><span class="sxs-lookup"><span data-stu-id="f3a34-110">Installing Certificates</span></span>  
 <span data-ttu-id="f3a34-111">Kroky potřebné k instalaci certifikátů, který jste právě vytvořili závisí na které verze služby IIS, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="f3a34-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="f3a34-112">Chcete-li nainstalovat službu IIS do služby IIS 5.1 (Windows XP) a služby IIS 6.0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="f3a34-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1.  <span data-ttu-id="f3a34-113">Otevřete Internetová informační služba modul Snap-In konzoly MMC správce.</span><span class="sxs-lookup"><span data-stu-id="f3a34-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2.  <span data-ttu-id="f3a34-114">Klikněte pravým tlačítkem na výchozí web a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f3a34-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="f3a34-115">Vyberte **zabezpečení adresáře** kartě.</span><span class="sxs-lookup"><span data-stu-id="f3a34-115">Select the **Directory Security** tab.</span></span>  
  
4.  <span data-ttu-id="f3a34-116">Klikněte **certifikát serveru** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f3a34-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="f3a34-117">Spustí se Průvodce certifikátem webového serveru.</span><span class="sxs-lookup"><span data-stu-id="f3a34-117">The Web Server Certificate Wizard starts.</span></span>  
  
5.  <span data-ttu-id="f3a34-118">Dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="f3a34-118">Complete the wizard.</span></span> <span data-ttu-id="f3a34-119">Vyberte možnost přiřadit certifikát.</span><span class="sxs-lookup"><span data-stu-id="f3a34-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="f3a34-120">Vyberte ServiceModelSamples HTTPS Server certifikát ze seznamu certifikátů, které jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="f3a34-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="f3a34-121">![Služba IIS certifikátu průvodce](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="f3a34-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6.  <span data-ttu-id="f3a34-122">Otestovat přístup ke službě v prohlížeči pomocí https://localhost/servicemodelsamples/service.svc adresa HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f3a34-122">Test access to the service in a browser by using the HTTPS address https://localhost/servicemodelsamples/service.svc.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="f3a34-123">Pokud pomocí Httpcfg.exe byl dříve nakonfigurovaný protokol SSL</span><span class="sxs-lookup"><span data-stu-id="f3a34-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1.  <span data-ttu-id="f3a34-124">Použijte Makecert.exe (nebo spuštění Setup.bat) k vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="f3a34-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2.  <span data-ttu-id="f3a34-125">Spusťte Správce služby IIS a nainstalujte certifikát podle předchozích kroků.</span><span class="sxs-lookup"><span data-stu-id="f3a34-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3.  <span data-ttu-id="f3a34-126">Přidejte následující řádek kódu do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="f3a34-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f3a34-127">Tento kód je potřeba jenom pro testovací certifikáty jsou vytvořené Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="f3a34-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="f3a34-128">Nedoporučuje pro produkční kód.</span><span class="sxs-lookup"><span data-stu-id="f3a34-128">It is not recommended for production code.</span></span>  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="f3a34-129">Instalace služby IIS ve službě IIS 7.0 (Windows Vista a Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="f3a34-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1.  <span data-ttu-id="f3a34-130">Z **spustit** nabídky, klikněte na tlačítko **spustit**, pak zadejte **inetmgr** otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="f3a34-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="f3a34-131">Klikněte pravým tlačítkem myši **Default Web Site** a vyberte **Upravit vazby...**</span><span class="sxs-lookup"><span data-stu-id="f3a34-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3.  <span data-ttu-id="f3a34-132">Klikněte **přidat** tlačítko **vazby webu** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="f3a34-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4.  <span data-ttu-id="f3a34-133">Vyberte **HTTPS** z **typ** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="f3a34-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5.  <span data-ttu-id="f3a34-134">Vyberte **ServiceModelSamples HTTPS Server** z **certifikát SSL** rozevíracího seznamu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="f3a34-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6.  <span data-ttu-id="f3a34-135">Otestovat přístup ke službě v prohlížeči pomocí https://localhost/servicemodelsamples/service.svc adresa HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f3a34-135">Test access to the service in a browser by using the HTTPS address https://localhost/servicemodelsamples/service.svc.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3a34-136">Vzhledem k tomu, že testovací certifikát, který jste právě nainstalovali není důvěryhodný certifikát, kterým může dojít další upozornění zabezpečení aplikace Internet Explorer při procházení k místní webové adresy, které jsou zabezpečené s tímto certifikátem.</span><span class="sxs-lookup"><span data-stu-id="f3a34-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="f3a34-137">Odebrání certifikátů</span><span class="sxs-lookup"><span data-stu-id="f3a34-137">Removing Certificates</span></span>  
  
-   <span data-ttu-id="f3a34-138">Pomocí Správce Internetové informační služby, jako dříve směrované, ale odebrat certifikát nebo vazba nepřidávat ho.</span><span class="sxs-lookup"><span data-stu-id="f3a34-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
-   <span data-ttu-id="f3a34-139">Pomocí následujícího příkazu odeberte certifikát počítače.</span><span class="sxs-lookup"><span data-stu-id="f3a34-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
