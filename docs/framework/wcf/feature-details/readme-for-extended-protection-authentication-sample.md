---
title: Soubor ReadMe pro ukázku rozšířené ochrany ověřování
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 19fe961e346874346485442bd0ba90badab5f79f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192470"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="d2890-102">Soubor ReadMe pro ukázku rozšířené ochrany ověřování</span><span class="sxs-lookup"><span data-stu-id="d2890-102">ReadMe for Extended Protection Authentication Sample</span></span>
<span data-ttu-id="d2890-103">Rozšířená ochrana je iniciativy zabezpečení pro ochranu před útoky (typu MITM) man-in-the-middle, při které útočník ("man-in-the-middle") zachycuje přihlašovací údaje klienta a používá pro přístup k zabezpečeným prostředkům na serveru určené pro klienta.</span><span class="sxs-lookup"><span data-stu-id="d2890-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>  
  
 <span data-ttu-id="d2890-104">Další informace najdete v tématu [rozšířené ochrany pro ověřování – přehled](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d2890-104">For more information, see [Extended Protection for Authentication Overview](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2890-105">Tato ukázka funguje pouze v případě hostovaných ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="d2890-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="d2890-106">Nepracuje na vývojový Server sady Visual Studio vzhledem k tomu, který nepodporuje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d2890-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d2890-107">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="d2890-107">To Set Up, Build, and Run the Sample</span></span>  
  
1.  <span data-ttu-id="d2890-108">Instalace služby IIS na počítači z panelu Přidat nebo odebrat programy -> funkce Windows.</span><span class="sxs-lookup"><span data-stu-id="d2890-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>  
  
2.  <span data-ttu-id="d2890-109">Zapnout ověřování Windows, v části funkce Windows: Internetová informační služba -> Webová služba -> zabezpečení -> ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="d2890-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>  
  
3.  <span data-ttu-id="d2890-110">Zapnout Aktivace protokolem HTTP ve funkcích Windows: rozhraní Microsoft .NET Framework 3.5.1 -> HTTP aktivace Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="d2890-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>  
  
4.  <span data-ttu-id="d2890-111">Tato ukázka vyžaduje klienta k navázání zabezpečeného kanálu se serverem a proto vyžaduje přítomnost certifikát serveru, který si můžete nainstalovat pomocí Správce Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="d2890-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="d2890-112">Otevřete Správce služby IIS -> certifikáty serveru (na kartě zobrazení funkce).</span><span class="sxs-lookup"><span data-stu-id="d2890-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>  
  
    2.  <span data-ttu-id="d2890-113">Pro účely testování tuto ukázku, můžete vytvořit certifikát podepsaný svým držitelem.</span><span class="sxs-lookup"><span data-stu-id="d2890-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="d2890-114">(Pokud nechcete, aby se vás zeptá na certifikát, nebude zabezpečený v aplikaci Internet Explorer, můžete nainstalovat jej do úložiště Důvěryhodné kořenové certifikační autority).</span><span class="sxs-lookup"><span data-stu-id="d2890-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>  
  
5.  <span data-ttu-id="d2890-115">Přejděte do podokna akcí pro výchozí web.</span><span class="sxs-lookup"><span data-stu-id="d2890-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="d2890-116">Klikněte na Upravit lokality -> vazby.</span><span class="sxs-lookup"><span data-stu-id="d2890-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="d2890-117">Přidáte HTTPS jako typ, pokud ještě není k dispozici s číslem portu 443 a přiřadit certifikát SSL vytvořený v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="d2890-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>  
  
6.  <span data-ttu-id="d2890-118">Vytvořte službu.</span><span class="sxs-lookup"><span data-stu-id="d2890-118">Build the service.</span></span> <span data-ttu-id="d2890-119">To vytvoří virtuální adresář ve službě IIS za vás (ze zadaného ve vlastnostech projektu akci po sestavení) a zkopíruje soubory dll, svc a konfiguračním podle potřeby služby bude hostovaná na webu.</span><span class="sxs-lookup"><span data-stu-id="d2890-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>  
  
7.  <span data-ttu-id="d2890-120">Otevřete Správce služby IIS.</span><span class="sxs-lookup"><span data-stu-id="d2890-120">Open the IIS Manager.</span></span> <span data-ttu-id="d2890-121">Klikněte pravým tlačítkem na virtuální adresář (Rozšířená ochrana ExtendedProtection), který jste vytvořili v předchozím kroku a vyberte převést na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d2890-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>  
  
8.  <span data-ttu-id="d2890-122">Otevřete modul ověřování ve Správci služby IIS pro tento virtuální adresář a povolení ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="d2890-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>  
  
9. <span data-ttu-id="d2890-123">Otevřít rozšířené nastavení pro Windows ověřování pro tento virtuální adresář a nastavte ho na povinné, protože v ukázce je odpovídající ExtendedProtection nastavená na hodnotu Always.</span><span class="sxs-lookup"><span data-stu-id="d2890-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>  
  
10. <span data-ttu-id="d2890-124">Službu můžete otestovat přístup k adresu URL z okna prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="d2890-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="d2890-125">Pokud chcete přístup k této adrese URL z mezi počítači, ujistěte se, že brána firewall otevřená pro všechna příchozí připojení HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d2890-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>  
  
11. <span data-ttu-id="d2890-126">Otevřete soubor konfigurace klienta a zadejte název počítače úplné \<klienta >- \<endpoint > – atribut adresy nahrazení << full_machine_name >>.</span><span class="sxs-lookup"><span data-stu-id="d2890-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing <<full_machine_name>>.</span></span>  
  
12. <span data-ttu-id="d2890-127">Spustíte klienta.</span><span class="sxs-lookup"><span data-stu-id="d2890-127">Run the client.</span></span> <span data-ttu-id="d2890-128">Klient komunikuje se služba navázáním zabezpečeného kanálu a použitím rozšířené ochrany na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d2890-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
