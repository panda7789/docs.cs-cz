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
ms.openlocfilehash: 412aa2bb2a56fbe654b0d9ce5f4b9b5176fc5549
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921304"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="b80fd-102">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="b80fd-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="b80fd-103">Při vytváření služby Windows Communication Foundation v místním prostředí (WCF) s třídou <xref:System.ServiceModel.WSHttpBinding>, která používá zabezpečení přenosu, je také nutné nakonfigurovat port s certifikátem X. 509.</span><span class="sxs-lookup"><span data-stu-id="b80fd-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="b80fd-104">Pokud nevytváříte samoobslužně hostované služby, můžete službu hostovat na Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="b80fd-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="b80fd-105">Další informace najdete v tématu [zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="b80fd-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="b80fd-106">K nakonfigurování portu závisí nástroj, který použijete, na operačním systému, který běží na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="b80fd-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="b80fd-107">Pokud používáte systém Windows Server 2003 nebo Windows XP, použijte nástroj HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="b80fd-107">If you are running Windows Server 2003 or Windows XP, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="b80fd-108">V systému Windows Server 2003 je tento nástroj nainstalován.</span><span class="sxs-lookup"><span data-stu-id="b80fd-108">With Windows Server 2003 this tool is installed.</span></span> <span data-ttu-id="b80fd-109">V systému Windows XP můžete nástroj stáhnout pomocí [nástrojů podpory systému Windows XP Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606).</span><span class="sxs-lookup"><span data-stu-id="b80fd-109">With Windows XP, you can download the tool at [Windows XP Service Pack 2 Support Tools](https://go.microsoft.com/fwlink/?LinkId=88606).</span></span> <span data-ttu-id="b80fd-110">Další informace najdete v tématu [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="b80fd-110">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="b80fd-111">Dokumentace k nástrojům [podpory systému Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) vysvětluje syntaxi nástroje HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="b80fd-111">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="b80fd-112">Pokud používáte systém Windows Vista, použijte nástroj Netsh. exe, který je již nainstalován.</span><span class="sxs-lookup"><span data-stu-id="b80fd-112">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="b80fd-113">Toto téma popisuje, jak provést několik postupů:</span><span class="sxs-lookup"><span data-stu-id="b80fd-113">This topic describes how to accomplish several procedures:</span></span>  
  
- <span data-ttu-id="b80fd-114">Určení aktuální konfigurace portu počítače.</span><span class="sxs-lookup"><span data-stu-id="b80fd-114">Determining a computer's current port configuration.</span></span>  
  
- <span data-ttu-id="b80fd-115">Získávání kryptografického otisku certifikátu (nutné pro následující dva postupy).</span><span class="sxs-lookup"><span data-stu-id="b80fd-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
- <span data-ttu-id="b80fd-116">Naváže certifikát SSL na konfiguraci portu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-116">Binding an SSL certificate to a port configuration.</span></span>  
  
- <span data-ttu-id="b80fd-117">Vytvořte vazbu certifikátu SSL s konfigurací portu a podpůrnými klientskými certifikáty.</span><span class="sxs-lookup"><span data-stu-id="b80fd-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
- <span data-ttu-id="b80fd-118">Odstraňuje se certifikát SSL z čísla portu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="b80fd-119">Nezapomeňte, že změna certifikátů uložených v počítači vyžaduje oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="b80fd-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="b80fd-120">Určení způsobu konfigurace portů</span><span class="sxs-lookup"><span data-stu-id="b80fd-120">To determine how ports are configured</span></span>  
  
1. <span data-ttu-id="b80fd-121">V systému Windows Server 2003 nebo Windows XP použijte nástroj HttpCfg. exe k zobrazení aktuální konfigurace portu pomocí přepínačů **dotaz** a **SSL** , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-121">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="b80fd-122">V systému Windows Vista se pomocí nástroje Netsh. exe zobrazí aktuální konfigurace portů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-122">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="b80fd-123">Získání kryptografického otisku certifikátu</span><span class="sxs-lookup"><span data-stu-id="b80fd-123">To get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="b80fd-124">Pomocí modulu snap-in Certifikáty konzoly MMC Najděte certifikát X. 509, který má zamýšlený účel ověřování klienta.</span><span class="sxs-lookup"><span data-stu-id="b80fd-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="b80fd-125">Další informace najdete v tématu [Postup: zobrazení certifikátů pomocí modulu snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="b80fd-125">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="b80fd-126">Přístup k kryptografickému otisku certifikátu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-126">Access the certificate's thumbprint.</span></span> <span data-ttu-id="b80fd-127">Další informace najdete v tématu [Postup: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="b80fd-127">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="b80fd-128">Zkopírujte kryptografický otisk certifikátu do textového editoru, například do poznámkového bloku.</span><span class="sxs-lookup"><span data-stu-id="b80fd-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="b80fd-129">Odebere všechny mezery mezi šestnáctkovými znaky.</span><span class="sxs-lookup"><span data-stu-id="b80fd-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="b80fd-130">Jedním ze způsobů, jak toho dosáhnout, je použít funkci Find-and-nahrazování textového editoru a nahradit každou mezeru znakem null.</span><span class="sxs-lookup"><span data-stu-id="b80fd-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="b80fd-131">Vytvoření vazby certifikátu SSL k číslu portu</span><span class="sxs-lookup"><span data-stu-id="b80fd-131">To bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="b80fd-132">V systému Windows Server 2003 nebo Windows XP použijte nástroj HttpCfg. exe v režimu "Set" v úložišti SSL (Secure Sockets Layer) (SSL) k navázání certifikátu na číslo portu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-132">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="b80fd-133">Nástroj používá kryptografický otisk k identifikaci certifikátu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="b80fd-134">Přepínač **-i** má syntaxi `IP`:`port` a instruuje nástroj, aby nastavil certifikát na port 8012 počítače.</span><span class="sxs-lookup"><span data-stu-id="b80fd-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="b80fd-135">Volitelně se čtyřmi nulami, které předcházejí číslu, může nahradit také skutečnou IP adresou počítače.</span><span class="sxs-lookup"><span data-stu-id="b80fd-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="b80fd-136">Přepínač **-h** určuje kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="b80fd-137">V systému Windows Vista použijte nástroj Netsh. exe, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-137">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - <span data-ttu-id="b80fd-138">Parametr **certhash** určuje kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="b80fd-139">Parametr **ipport** určuje IP adresu a port a funguje stejně jako přepínač **-i** nástroje HttpCfg. exe, který je popsán.</span><span class="sxs-lookup"><span data-stu-id="b80fd-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="b80fd-140">Parametr **AppID** je identifikátor GUID, který lze použít k identifikaci vlastnící aplikace.</span><span class="sxs-lookup"><span data-stu-id="b80fd-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="b80fd-141">Vytvoření vazby certifikátu SSL k číslu portu a podpora klientských certifikátů</span><span class="sxs-lookup"><span data-stu-id="b80fd-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="b80fd-142">V systému Windows Server 2003 nebo Windows XP pro podporu klientů, kteří se ověřují pomocí certifikátů X. 509 na transportní vrstvě, postupujte podle výše uvedeného postupu, ale předejte další parametr příkazového řádku HttpCfg. exe, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-142">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="b80fd-143">Přepínač **-f** má syntaxi `n`, kde n je číslo v rozmezí od 1 do 7.</span><span class="sxs-lookup"><span data-stu-id="b80fd-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="b80fd-144">Hodnota 2, jak je znázorněno v předchozím příkladu, umožňuje klientské certifikáty na transportní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="b80fd-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="b80fd-145">Hodnota 3 povolí klientským certifikátům a mapuje tyto certifikáty na účet systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b80fd-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="b80fd-146">Chování dalších hodnot naleznete v nápovědě k HttpCfg. exe.</span><span class="sxs-lookup"><span data-stu-id="b80fd-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="b80fd-147">Pokud chcete v systému Windows Vista podporovat klienty, kteří se ověřují pomocí certifikátů X. 509 na transportní vrstvě, postupujte podle výše uvedeného postupu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-147">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="b80fd-148">Odstranění certifikátu SSL z čísla portu</span><span class="sxs-lookup"><span data-stu-id="b80fd-148">To delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="b80fd-149">Pomocí nástroje HttpCfg. exe nebo Netsh. exe zobrazte porty a kryptografické otisky všech vazeb v počítači.</span><span class="sxs-lookup"><span data-stu-id="b80fd-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="b80fd-150">Chcete-li vytisknout informace na disk, použijte znak přesměrování ">", jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="b80fd-151">V systému Windows Server 2003 nebo Windows XP použijte nástroj HttpCfg. exe s klíčovými slovy **Delete** a **SSL** .</span><span class="sxs-lookup"><span data-stu-id="b80fd-151">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="b80fd-152">Pomocí přepínače **-i** zadejte `IP`:`port` číslo a přepínač **-h** k určení kryptografického otisku.</span><span class="sxs-lookup"><span data-stu-id="b80fd-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="b80fd-153">V systému Windows Vista použijte nástroj Netsh. exe, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-153">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="b80fd-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="b80fd-154">Example</span></span>  
 <span data-ttu-id="b80fd-155">Následující kód ukazuje, jak vytvořit samoobslužnou službu pomocí <xref:System.ServiceModel.WSHttpBinding> třídy nastavenou na zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="b80fd-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="b80fd-156">Při vytváření aplikace zadejte číslo portu v adrese.</span><span class="sxs-lookup"><span data-stu-id="b80fd-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b80fd-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b80fd-157">See also</span></span>

- [<span data-ttu-id="b80fd-158">Zabezpečení přenosu HTTP</span><span class="sxs-lookup"><span data-stu-id="b80fd-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
