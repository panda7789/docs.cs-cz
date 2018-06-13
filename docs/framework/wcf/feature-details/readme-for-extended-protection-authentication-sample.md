---
title: Soubor ReadMe pro ukázku rozšířené ochrany ověřování
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d45271180b7f00ba78d106f2a93d5860375da5f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495077"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="ec5eb-102">Soubor ReadMe pro ukázku rozšířené ochrany ověřování</span><span class="sxs-lookup"><span data-stu-id="ec5eb-102">ReadMe for Extended Protection Authentication Sample</span></span>
<span data-ttu-id="ec5eb-103">Rozšířená ochrana je initiative zabezpečení k ochraně proti útokům man-in-the-middle (typu MITM), ve kterých útočník ("man-in-the-middle") zachycuje pověření klienta a používá je pro přístup k zabezpečeným prostředkům na určený server klienta.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>  
  
 <span data-ttu-id="ec5eb-104">Další informace najdete v tématu [Rozšířená ochrana pro ověřování – přehled](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ec5eb-104">For more information, see [Extended Protection for Authentication Overview](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec5eb-105">Tato ukázka funguje pouze při hostované ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="ec5eb-106">Nefunguje na vývojový Server sady Visual Studio vzhledem k tomu, který nepodporuje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ec5eb-107">Chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="ec5eb-107">To Set Up, Build, and Run the Sample</span></span>  
  
1.  <span data-ttu-id="ec5eb-108">Instalace služby IIS na počítači z panelu Přidat nebo odebrat programy -> funkce systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>  
  
2.  <span data-ttu-id="ec5eb-109">Zapnout ověřování systému Windows v funkce systému Windows: Internetová informační služba -> Webová služba -> zabezpečení -> ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>  
  
3.  <span data-ttu-id="ec5eb-110">Zapnout aktivace protokolu HTTP v funkce systému Windows: Microsoft .NET Framework 3.5.1 -> Aktivace Windows Communication Foundation HTTP.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>  
  
4.  <span data-ttu-id="ec5eb-111">Tato ukázka vyžaduje klienta k navázání zabezpečeného kanálu se serverem a proto vyžaduje přítomnost certifikát serveru, které můžete nainstalovat ze Správce Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="ec5eb-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="ec5eb-112">Otevřete Správce služby IIS -> certifikáty serveru (na kartě zobrazení funkce).</span><span class="sxs-lookup"><span data-stu-id="ec5eb-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>  
  
    2.  <span data-ttu-id="ec5eb-113">Pro účely testování tuto ukázku, můžete vytvořit certifikát podepsaný svým držitelem.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="ec5eb-114">(Pokud nechcete, aby vás zeptá, certifikát nebude zabezpečené v aplikaci Internet Explorer, nebudete ho nainstalovat do úložiště Důvěryhodné kořenové certifikační autority).</span><span class="sxs-lookup"><span data-stu-id="ec5eb-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>  
  
5.  <span data-ttu-id="ec5eb-115">Přejděte do podokna akce pro výchozí web.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="ec5eb-116">Klikněte na tlačítko Upravit lokality -> vazby.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="ec5eb-117">Přidejte HTTPS jako typ, pokud ještě není představovat číslo portu 443 a přiřadit certifikát SSL vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>  
  
6.  <span data-ttu-id="ec5eb-118">Vytvořte službu.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-118">Build the service.</span></span> <span data-ttu-id="ec5eb-119">Tento virtuální adresář ve službě IIS pro vás vytvoří (z akce sestavení post zadána ve vlastnostech projektu) a zkopíruje soubory knihoven dll, .svc a konfigurace podle potřeby pro službu být hostovaná na webu.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>  
  
7.  <span data-ttu-id="ec5eb-120">Otevřete Správce služby IIS.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-120">Open the IIS Manager.</span></span> <span data-ttu-id="ec5eb-121">Klikněte pravým tlačítkem na virtuální adresář (ExtendedProtection), který jste vytvořili v předchozím kroku a vyberte převod na aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>  
  
8.  <span data-ttu-id="ec5eb-122">Otevřete modul ověřování ve Správci služby IIS pro tento virtuální adresář a povolit ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>  
  
9. <span data-ttu-id="ec5eb-123">Otevřete rozšířená nastavení pro ověřování systému Windows pro tento virtuální adresář a nastavte ji na povinné, protože v ukázce odpovídající nastavení ExtendedProtection nastavena vždy.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>  
  
10. <span data-ttu-id="ec5eb-124">Službu můžete otestovat přístup k adresu URL z okna prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="ec5eb-125">Pokud chcete přístup k této adrese URL z křížové počítače, ujistěte se, že brána firewall, je otevřené pro všechna příchozí připojení HTTP a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>  
  
11. <span data-ttu-id="ec5eb-126">Otevřete soubor konfigurace klienta a zadejte název počítače úplné \<klienta >- \<koncový bod >-atribut adresu, nahraďte << full_machine_name >>.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing <<full_machine_name>>.</span></span>  
  
12. <span data-ttu-id="ec5eb-127">Spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-127">Run the client.</span></span> <span data-ttu-id="ec5eb-128">Klient komunikuje se služba navázáním zabezpečeného kanálu a použitím rozšířené ochrany v pozadí.</span><span class="sxs-lookup"><span data-stu-id="ec5eb-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
