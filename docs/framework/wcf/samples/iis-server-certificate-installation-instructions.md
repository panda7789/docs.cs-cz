---
title: Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 300d689925d60998ef475ad63f3878bf6d066850
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989858"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="5b3b7-102">Pokyny k instalaci certifikátu serveru Internetové informační služby (IIS)</span><span class="sxs-lookup"><span data-stu-id="5b3b7-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="5b3b7-103">Chcete-li spustit ukázky, které bezpečně komunikují s Internetová informační služba (IIS), je nutné vytvořit a nainstalovat certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="5b3b7-104">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-104">Step 1.</span></span> <span data-ttu-id="5b3b7-105">Vytváření certifikátů</span><span class="sxs-lookup"><span data-stu-id="5b3b7-105">Creating Certificates</span></span>  
 <span data-ttu-id="5b3b7-106">Chcete-li vytvořit certifikát pro váš počítač, otevřete Developer Command Prompt pro sadu Visual Studio s oprávněním správce a spusťte instalační program. bat, který je součástí všech ukázek, které používají zabezpečenou komunikaci se službou IIS.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-106">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="5b3b7-107">Před spuštěním tohoto dávkového souboru zajistěte, aby cesta obsahovala složku, která obsahuje nástroj Makecert. exe.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="5b3b7-108">Následující příkaz slouží k vytvoření certifikátu v Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```console  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="5b3b7-109">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-109">Step 2.</span></span> <span data-ttu-id="5b3b7-110">Instalace certifikátů</span><span class="sxs-lookup"><span data-stu-id="5b3b7-110">Installing Certificates</span></span>  
 <span data-ttu-id="5b3b7-111">Postup potřebný k instalaci certifikátů, které jste právě vytvořili, závisí na verzi služby IIS, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="5b3b7-112">Instalace služby IIS na IIS 5,1 (Windows XP) a IIS 6,0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="5b3b7-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="5b3b7-113">Otevřete modul snap-in konzoly MMC Internetová informační služba správce.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="5b3b7-114">Klikněte pravým tlačítkem na výchozí web a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="5b3b7-115">Vyberte kartu **zabezpečení adresáře** .</span><span class="sxs-lookup"><span data-stu-id="5b3b7-115">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="5b3b7-116">Klikněte na tlačítko **certifikát serveru** .</span><span class="sxs-lookup"><span data-stu-id="5b3b7-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="5b3b7-117">Spustí se Průvodce certifikátem webového serveru.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-117">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="5b3b7-118">Dokončete průvodce.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-118">Complete the wizard.</span></span> <span data-ttu-id="5b3b7-119">Vyberte možnost přiřazení certifikátu.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="5b3b7-120">V seznamu zobrazených certifikátů vyberte certifikát ServiceModelSamples-HTTPS-Server.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="5b3b7-121">![Průvodce certifikátem služby IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="5b3b7-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="5b3b7-122">Otestujte přístup ke službě v prohlížeči pomocí adresy `https://localhost/servicemodelsamples/service.svc`https.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-122">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="5b3b7-123">Pokud byl protokol SSL dřív nakonfigurovaný pomocí Httpcfg. exe</span><span class="sxs-lookup"><span data-stu-id="5b3b7-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="5b3b7-124">Pomocí nástroje MakeCert. exe (nebo spuštěním souboru Setup. bat) vytvořte certifikát serveru.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="5b3b7-125">Spusťte Správce služby IIS a nainstalujte certifikát podle předchozích kroků.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="5b3b7-126">Do klientského programu přidejte následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5b3b7-127">Tento kód je vyžadován pouze pro testovací certifikáty, například ty, které byly vytvořeny pomocí nástroje MakeCert. exe.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="5b3b7-128">Nedoporučuje se pro produkční kód.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-128">It is not recommended for production code.</span></span>  
  
```csharp  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="5b3b7-129">Instalace služby IIS na IIS 7,0 (Windows Vista a Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="5b3b7-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="5b3b7-130">V nabídce **Start** klikněte na tlačítko **Spustit**a zadejte příkaz **inetmgr** . tím otevřete modul snap-in konzoly MMC Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="5b3b7-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="5b3b7-131">Klikněte pravým tlačítkem na **výchozí web** a vyberte **Upravit vazby...**</span><span class="sxs-lookup"><span data-stu-id="5b3b7-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="5b3b7-132">Klikněte na tlačítko **Přidat** v dialogovém okně **vazby webu** .</span><span class="sxs-lookup"><span data-stu-id="5b3b7-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="5b3b7-133">V rozevíracím seznamu **typ** vyberte **https** .</span><span class="sxs-lookup"><span data-stu-id="5b3b7-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="5b3b7-134">V rozevíracím seznamu **certifikát SSL** vyberte **ServiceModelSamples-https-Server** a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="5b3b7-135">Otestujte přístup ke službě v prohlížeči pomocí adresy `https://localhost/servicemodelsamples/service.svc`https.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-135">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b3b7-136">Vzhledem k tomu, že testovací certifikát, který jste právě nainstalovali, není důvěryhodný certifikát, můžete při prohlížení místních webových adres zabezpečených pomocí tohoto certifikátu narazit na další upozornění zabezpečení aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="5b3b7-137">Odebírání certifikátů</span><span class="sxs-lookup"><span data-stu-id="5b3b7-137">Removing Certificates</span></span>  
  
- <span data-ttu-id="5b3b7-138">Použijte Internetová informační služba Manager jako dříve směrovaný, ale odeberte certifikát nebo vazbu místo přidávání.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
- <span data-ttu-id="5b3b7-139">Pomocí následujícího příkazu odeberte certifikát počítače.</span><span class="sxs-lookup"><span data-stu-id="5b3b7-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
