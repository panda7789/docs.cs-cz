---
title: Soubor ReadMe pro ukázku rozšířené ochrany ověřování
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 9b0a3535282a1fcc1103651f5601459e80d3d8d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601098"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="9921b-102">Soubor ReadMe pro ukázku rozšířené ochrany ověřování</span><span class="sxs-lookup"><span data-stu-id="9921b-102">ReadMe for Extended Protection Authentication Sample</span></span>

<span data-ttu-id="9921b-103">Rozšířená ochrana je bezpečnostní iniciativa pro ochranu proti útokům MITM (man-in-the-middle), kdy útočník ("muž-in-the-middle") zachycuje přihlašovací údaje klienta a používá je k přístupu k zabezpečeným prostředkům na zamýšleném serveru klienta.</span><span class="sxs-lookup"><span data-stu-id="9921b-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>

<span data-ttu-id="9921b-104">Další informace najdete v tématu [Rozšířená ochrana pro ověřování – přehled](extended-protection-for-authentication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9921b-104">For more information, see [Extended Protection for Authentication Overview](extended-protection-for-authentication-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9921b-105">Tato ukázka funguje jenom v případě, že je hostovaná ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="9921b-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="9921b-106">Nefunguje na vývojovém serveru sady Visual Studio, protože nepodporuje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9921b-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9921b-107">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="9921b-107">To Set Up, Build, and Run the Sample</span></span>

1. <span data-ttu-id="9921b-108">Nainstalujte službu IIS na počítači pomocí ovládacího panelu Přidat nebo odebrat programy – > funkce Windows.</span><span class="sxs-lookup"><span data-stu-id="9921b-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>

2. <span data-ttu-id="9921b-109">Zapnout ověřování systému Windows ve funkcích Windows: Internetová informační služba-> World World World World Services-> zabezpečení – > ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9921b-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>

3. <span data-ttu-id="9921b-110">Zapnutí aktivace protokolem HTTP v součástech systému Windows: Microsoft .NET Framework 3.5.1 – > Windows Communication Foundation aktivace protokolem HTTP.</span><span class="sxs-lookup"><span data-stu-id="9921b-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>

4. <span data-ttu-id="9921b-111">Tato ukázka vyžaduje, aby klient navázal zabezpečený kanál se serverem, takže vyžaduje přítomnost certifikátu serveru, který se dá nainstalovat z správce Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="9921b-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>

    1. <span data-ttu-id="9921b-112">Otevřete Správce služby IIS-> certifikáty serveru (na kartě zobrazení funkcí).</span><span class="sxs-lookup"><span data-stu-id="9921b-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>

    2. <span data-ttu-id="9921b-113">Pro účely testování této ukázky můžete vytvořit certifikát podepsaný svým držitelem.</span><span class="sxs-lookup"><span data-stu-id="9921b-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="9921b-114">(Pokud nechcete, aby Internet Explorer zobrazil výzvu k tomu, že certifikát není zabezpečený, můžete ho nainstalovat v úložišti Důvěryhodné kořenové certifikační autority certifikátu).</span><span class="sxs-lookup"><span data-stu-id="9921b-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>

5. <span data-ttu-id="9921b-115">Přejít do podokna akce pro výchozí web.</span><span class="sxs-lookup"><span data-stu-id="9921b-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="9921b-116">Klikněte na Upravit vazby > webů.</span><span class="sxs-lookup"><span data-stu-id="9921b-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="9921b-117">Přidejte HTTPS jako typ, pokud ještě neexistuje, s číslem portu 443 a přiřaďte certifikát SSL, který jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="9921b-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>

6. <span data-ttu-id="9921b-118">Sestavte službu.</span><span class="sxs-lookup"><span data-stu-id="9921b-118">Build the service.</span></span> <span data-ttu-id="9921b-119">Tím se vytvoří virtuální adresář ve službě IIS pro vás (od akce po sestavení určené ve vlastnostech projektu) a zkopírování souborů DLL, svc a config, jak je to nutné, aby byla služba hostitelem webu.</span><span class="sxs-lookup"><span data-stu-id="9921b-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>

7. <span data-ttu-id="9921b-120">Otevřete Správce služby IIS.</span><span class="sxs-lookup"><span data-stu-id="9921b-120">Open the IIS Manager.</span></span> <span data-ttu-id="9921b-121">Klikněte pravým tlačítkem na virtuální adresář (ExtendedProtection), který jste vytvořili v předchozím kroku, a vyberte převést na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9921b-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>

8. <span data-ttu-id="9921b-122">Otevřete modul ověřování ve Správci služby IIS pro tento virtuální adresář a povolte ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9921b-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>

9. <span data-ttu-id="9921b-123">Otevřete upřesňující nastavení pro ověřování systému Windows pro tento virtuální adresář a nastavte jej na požadováno, protože v ukázce je odpovídající nastavení ExtendedProtection nastaveno na vždy.</span><span class="sxs-lookup"><span data-stu-id="9921b-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>

10. <span data-ttu-id="9921b-124">Službu můžete otestovat přístupem k adrese URL z okna prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="9921b-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="9921b-125">Pokud chcete získat přístup k této adrese URL z více počítačů, ujistěte se, že je brána firewall otevřená pro všechna příchozí připojení HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9921b-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>

11. <span data-ttu-id="9921b-126">Otevřete konfigurační soubor klienta a zadejte úplný název počítače pro \<client>  -  \<endpoint> atribut-address a nahraďte ho \<full_machine_name> .</span><span class="sxs-lookup"><span data-stu-id="9921b-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing \<full_machine_name>.</span></span>

12. <span data-ttu-id="9921b-127">Spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="9921b-127">Run the client.</span></span> <span data-ttu-id="9921b-128">Klient komunikuje se službou vytvořením zabezpečeného kanálu a použitím rozšířené ochrany v rámci pokrývání.</span><span class="sxs-lookup"><span data-stu-id="9921b-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
