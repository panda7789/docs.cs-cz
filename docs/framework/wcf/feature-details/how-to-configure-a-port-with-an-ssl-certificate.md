---
title: 'Postupy: Konfigurace portu s certifikátem SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 90d5424e12bb770dc3da85e1b2738206f4777c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185110"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="6b2b7-102">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="6b2b7-102">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="6b2b7-103">Při vytváření služby WCF (Windows Communication Foundation) <xref:System.ServiceModel.WSHttpBinding> s vlastní hospojnou službou Windows Communication Foundation (WCF) s třídou, která používá zabezpečení přenosu, je také nutné nakonfigurovat port s certifikátem X.509.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="6b2b7-104">Pokud nevytváříte samoobslužnou službu, můžete ji hostovat v Internetové informační službě (IIS).</span><span class="sxs-lookup"><span data-stu-id="6b2b7-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="6b2b7-105">Další informace naleznete v tématu [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="6b2b7-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="6b2b7-106">Chcete-li nakonfigurovat port, nástroj, který používáte, závisí na operačním systému spuštěném v počítači.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="6b2b7-107">Pokud používáte systém Windows Server 2003, použijte nástroj HttpCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-107">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="6b2b7-108">V systému Windows Server 2003 je tento nástroj nainstalován.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-108">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="6b2b7-109">Další informace naleznete v tématu [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="6b2b7-109">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="6b2b7-110">[Dokumentace nástroje podpory systému Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) vysvětluje syntaxi nástroje Httpcfg.exe.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-110">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="6b2b7-111">Pokud používáte systém Windows Vista, použijte nástroj Netsh.exe, který je již nainstalován.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-111">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="6b2b7-112">Úprava certifikátů uložených v počítači vyžaduje oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-112">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="6b2b7-113">Určení způsobu konfigurace portů</span><span class="sxs-lookup"><span data-stu-id="6b2b7-113">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="6b2b7-114">V systému Windows Server 2003 nebo Windows XP můžete pomocí nástroje HttpCfg.exe zobrazit aktuální konfiguraci portu pomocí přepínačů **dotazu** a **ssl,** jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-114">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="6b2b7-115">V systému Windows Vista použijte nástroj Netsh.exe k zobrazení aktuální konfigurace portu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-115">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="6b2b7-116">Získání kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="6b2b7-116">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="6b2b7-117">Pomocí modulu snap-in MMC certifikátů vyhledejte certifikát X.509, který má zamýšlený účel ověřování klienta.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-117">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="6b2b7-118">Další informace naleznete v [tématu How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="6b2b7-118">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="6b2b7-119">Přístup k kryptografickému otisku certifikátu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-119">Access the certificate's thumbprint.</span></span> <span data-ttu-id="6b2b7-120">Další informace naleznete v [tématu How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="6b2b7-120">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="6b2b7-121">Zkopírujte kryptografický otisk certifikátu do textového editoru, například poznámkový blok.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-121">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="6b2b7-122">Odstraňte všechny mezery mezi šestnáctkovými znaky.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-122">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="6b2b7-123">Jedním ze způsobů, jak toho dosáhnout, je použít funkci hledání a nahrazení textového editoru a nahradit každou mezeru prázdným znakem.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-123">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="6b2b7-124">Vazba certifikátu SSL na číslo portu</span><span class="sxs-lookup"><span data-stu-id="6b2b7-124">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="6b2b7-125">V systému Windows Server 2003 nebo Windows XP použijte nástroj HttpCfg.exe v režimu sady v úložišti SSL (Secure Sockets Layer) k vytvoření svázání certifikátu s číslem portu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-125">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="6b2b7-126">Nástroj používá kryptografický otisk k identifikaci certifikátu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-126">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="6b2b7-127">Přepínač **-i** má `IP`syntaxi`port` : a instruuje nástroj pro nastavení certifikátu na port 8012 počítače.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-127">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="6b2b7-128">Volitelně čtyři nuly, které předcházejí číslo lze také nahradit skutečnou IP adresu počítače.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-128">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="6b2b7-129">Přepínač **-h** určuje kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-129">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="6b2b7-130">V systému Windows Vista použijte nástroj Netsh.exe, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-130">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="6b2b7-131">Parametr **certhash** určuje kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-131">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="6b2b7-132">Parametr **ipport** určuje IP adresu a port a funguje stejně jako přepínač **-i** popsaného nástroje Httpcfg.exe.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-132">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="6b2b7-133">**Appid** parametr je GUID, který lze použít k identifikaci vlastnící aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-133">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="6b2b7-134">Vazba certifikátu SSL na číslo portu a podpora klientských certifikátů</span><span class="sxs-lookup"><span data-stu-id="6b2b7-134">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="6b2b7-135">Chcete-li podporovat klienty, kteří se ověřují pomocí certifikátů X.509 v transportní vrstvě, postupujte podle předchozího postupu, ale předáte další parametr příkazového řádku programu HttpCfg.exe, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-135">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="6b2b7-136">Přepínač **-f** má syntaxi kde `n` n je číslo mezi 1 a 7.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-136">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="6b2b7-137">Hodnota 2, jak je znázorněno v předchozím příkladu, umožňuje klientské certifikáty na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-137">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="6b2b7-138">Hodnota 3 umožňuje klientské certifikáty a mapuje tyto certifikáty na účet systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-138">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="6b2b7-139">Viz HttpCfg.exe Nápověda pro chování jiných hodnot.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-139">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="6b2b7-140">Chcete-li v systému Windows Vista podporovat klienty, kteří se ověřují pomocí certifikátů X.509 ve vrstvě přenosu, postupujte podle předchozího postupu, ale s dalším parametrem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-140">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="6b2b7-141">Odstranění certifikátu SSL z čísla portu</span><span class="sxs-lookup"><span data-stu-id="6b2b7-141">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="6b2b7-142">Pomocí nástroje HttpCfg.exe nebo Netsh.exe zobrazíte porty a kryptografické otisky všech vazeb v počítači.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-142">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="6b2b7-143">Chcete-li vytisknout informace na disk, použijte znak přesměrování ">", jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-143">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="6b2b7-144">V systému Windows Server 2003 nebo Windows XP použijte nástroj HttpCfg.exe s klíčovými slovy **delete** a **ssl.**</span><span class="sxs-lookup"><span data-stu-id="6b2b7-144">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="6b2b7-145">Pomocí přepínače **-i** `IP`určete :`port` number a **-h** switch pro určení kryptografického otisku.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-145">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="6b2b7-146">V systému Windows Vista použijte nástroj Netsh.exe, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-146">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="6b2b7-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b2b7-147">Example</span></span>  

 <span data-ttu-id="6b2b7-148">Následující kód ukazuje, jak vytvořit samoobslužnou službu <xref:System.ServiceModel.WSHttpBinding> pomocí třídy nastavené na zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-148">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="6b2b7-149">Při vytváření aplikace zadejte číslo portu v adrese.</span><span class="sxs-lookup"><span data-stu-id="6b2b7-149">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6b2b7-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b2b7-150">See also</span></span>

- [<span data-ttu-id="6b2b7-151">Zabezpečení přenosu HTTP</span><span class="sxs-lookup"><span data-stu-id="6b2b7-151">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
