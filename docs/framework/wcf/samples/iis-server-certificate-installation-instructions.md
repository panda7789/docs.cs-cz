---
title: Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 8d0b80930424f0d8529f2b035a8e1167f361f99a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770279"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="53718-102">Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)</span><span class="sxs-lookup"><span data-stu-id="53718-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="53718-103">Ke spuštění ukázky, které zabezpečeně komunikovat s Internetové informační služby (IIS), musíte vytvořit a nainstalovat certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="53718-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="53718-104">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="53718-104">Step 1.</span></span> <span data-ttu-id="53718-105">Vytváření certifikátů</span><span class="sxs-lookup"><span data-stu-id="53718-105">Creating Certificates</span></span>  
 <span data-ttu-id="53718-106">Chcete-li vytvořit certifikát pro počítač, otevřete Developer Command Prompt pro sadu Visual Studio s oprávněními správce a spusťte Setup.bat, který je součástí všech ukázek, které používají zabezpečené komunikace se službou IIS.</span><span class="sxs-lookup"><span data-stu-id="53718-106">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="53718-107">Ujistěte se, že cesta obsahuje složku obsahující Makecert.exe předtím, než spustíte tento dávkový soubor.</span><span class="sxs-lookup"><span data-stu-id="53718-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="53718-108">Následující příkaz se používá k vytvoření certifikátu v Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="53718-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="53718-109">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="53718-109">Step 2.</span></span> <span data-ttu-id="53718-110">Instalace certifikátů</span><span class="sxs-lookup"><span data-stu-id="53718-110">Installing Certificates</span></span>  
 <span data-ttu-id="53718-111">Kroky potřebné k instalaci certifikátů, které jste právě vytvořili, závisí na kterou verzi služby IIS, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="53718-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="53718-112">Instalace služby IIS na IIS 5.1 (Windows XP) a služby IIS 6.0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="53718-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="53718-113">Otevřít Internetová informační služba modul Snap-In konzoly MMC správce.</span><span class="sxs-lookup"><span data-stu-id="53718-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="53718-114">Klikněte pravým tlačítkem na výchozí web a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="53718-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="53718-115">Vyberte **zabezpečení adresáře** kartu.</span><span class="sxs-lookup"><span data-stu-id="53718-115">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="53718-116">Klikněte na tlačítko **certifikát serveru** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="53718-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="53718-117">Spustí se Průvodce certifikátem webového serveru.</span><span class="sxs-lookup"><span data-stu-id="53718-117">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="53718-118">Dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="53718-118">Complete the wizard.</span></span> <span data-ttu-id="53718-119">Vyberte možnost přiřadit certifikát.</span><span class="sxs-lookup"><span data-stu-id="53718-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="53718-120">Vyberte ServiceModelSamples HTTPS Server certifikát ze seznamu certifikátů, které jsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="53718-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="53718-121">![Průvodce certifikátů služby IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="53718-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="53718-122">Otestovat přístup k této službě v prohlížeči pomocí adresu HTTPS `https://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="53718-122">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="53718-123">Pokud byla dříve nakonfigurovaný protokol SSL s využitím Httpcfg.exe</span><span class="sxs-lookup"><span data-stu-id="53718-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="53718-124">Použijte Makecert.exe (nebo spuštění Setup.bat) k vytvoření certifikátu serveru.</span><span class="sxs-lookup"><span data-stu-id="53718-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="53718-125">Spusťte Správce služby IIS a nainstalovat certifikát podle předchozích kroků.</span><span class="sxs-lookup"><span data-stu-id="53718-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="53718-126">Přidejte následující řádek kódu do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="53718-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="53718-127">Tento kód je potřeba jenom pro testovací certifikáty, jako jsou ty vytvořené Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="53718-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="53718-128">To se nedoporučuje pro produkční kód.</span><span class="sxs-lookup"><span data-stu-id="53718-128">It is not recommended for production code.</span></span>  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="53718-129">Instalace služby IIS ve službě IIS 7.0 (Windows Vista a Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="53718-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="53718-130">Z **Start** nabídky, klikněte na tlačítko **spustit**, zadejte **inetmgr** otevřete modul snap-in konzoly MMC Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="53718-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="53718-131">Klikněte pravým tlačítkem myši **výchozí webový server** a vyberte **Upravit vazby...**</span><span class="sxs-lookup"><span data-stu-id="53718-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="53718-132">Klikněte na tlačítko **přidat** tlačítko **vazby webu** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="53718-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="53718-133">Vyberte **HTTPS** z **typ** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="53718-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="53718-134">Vyberte **ServiceModelSamples HTTPS Server** z **certifikát SSL** rozevíracího seznamu a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="53718-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="53718-135">Otestovat přístup k této službě v prohlížeči pomocí adresu HTTPS `https://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="53718-135">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53718-136">Vzhledem k tomu, že testovací certifikát, který jste právě nainstalovali není důvěryhodný certifikát, další upozornění zabezpečení aplikace Internet Explorer můžete narazit, při přechodu na místní webové adresy, které jsou zabezpečené pomocí tohoto certifikátu.</span><span class="sxs-lookup"><span data-stu-id="53718-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="53718-137">Odebírání certifikátů</span><span class="sxs-lookup"><span data-stu-id="53718-137">Removing Certificates</span></span>  
  
-   <span data-ttu-id="53718-138">Pomocí Správce Internetové informační služby, jako dříve přesměruje, ale odebrat certifikát nebo vazby místo jeho přidání.</span><span class="sxs-lookup"><span data-stu-id="53718-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
-   <span data-ttu-id="53718-139">Pomocí následujícího příkazu odeberte certifikát počítače.</span><span class="sxs-lookup"><span data-stu-id="53718-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
