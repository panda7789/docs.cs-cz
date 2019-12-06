---
title: Používání vývojářských nástrojů WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 8253a9136b2310deeb7c6d162a9f190c13ba02da
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837724"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="fee09-102">Používání vývojářských nástrojů WCF</span><span class="sxs-lookup"><span data-stu-id="fee09-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="fee09-103">Tato část popisuje vývojové nástroje sady Visual Studio, které vám můžou pomoct při vývoji WCFservice.</span><span class="sxs-lookup"><span data-stu-id="fee09-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="fee09-104">Šablony sady Visual Studio můžete použít jako základ k rychlému vytvoření vlastní služby a pak k ladění a testování služby použít automatické hostování služby WCF a testovacího klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="fee09-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="fee09-105">Tyto nástroje společně poskytují rychlý a bezproblémové cyklus ladění a testování a brání nutnosti potvrzování modelu hostování v rané fázi.</span><span class="sxs-lookup"><span data-stu-id="fee09-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
 
 > [!NOTE]
 > <span data-ttu-id="fee09-106">Počínaje sadou Visual Studio 2017 nejsou ve výchozím nastavení nainstalovány vývojové nástroje WCF.</span><span class="sxs-lookup"><span data-stu-id="fee09-106">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="fee09-107">Aby bylo možné používat tyto funkce, je nutné zajistit, aby byla v instalačním programu sady Visual Studio vybrána součást Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="fee09-107">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="fee09-108">Vývojářské nástroje WCF</span><span class="sxs-lookup"><span data-stu-id="fee09-108">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="fee09-109">Šablony sady Visual Studio pro WCF</span><span class="sxs-lookup"><span data-stu-id="fee09-109">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="fee09-110">Můžete použít předdefinované šablony projektů a položek sady Visual Studio v aplikaci Visual Studio k rychlému vytváření služeb WCF a okolních aplikací.</span><span class="sxs-lookup"><span data-stu-id="fee09-110">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="fee09-111">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="fee09-111">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="fee09-112">Automatické hostování služby WCF (WcfSvcHost. exe) umožňuje spustit ladicí program sady Visual Studio (F5) pro automatické hostování a testování služby, kterou jste nasadili.</span><span class="sxs-lookup"><span data-stu-id="fee09-112">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="fee09-113">Potom můžete službu otestovat pomocí testovacího klienta WCF (wcfTestClient. exe) nebo vašeho vlastního klienta a vyhledat a opravit případné chyby.</span><span class="sxs-lookup"><span data-stu-id="fee09-113">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="fee09-114">Testovací klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="fee09-114">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="fee09-115">Testovací klient služby WCF (WcfTestClient. exe) je nástroj grafického uživatelského rozhraní, který umožňuje zadat parametry libovolných typů, odeslat tento vstup do služby a zobrazit odpověď, kterou služba odesílá zpět.</span><span class="sxs-lookup"><span data-stu-id="fee09-115">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="fee09-116">Poskytuje bezproblémové prostředí pro testování služeb při kombinaci s automatickým hostitelem služby WCF.</span><span class="sxs-lookup"><span data-stu-id="fee09-116">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="fee09-117">Generování tříd datových typů z XML</span><span class="sxs-lookup"><span data-stu-id="fee09-117">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="fee09-118">Data XML uložená ve schránce lze vložit do znakové stránky.</span><span class="sxs-lookup"><span data-stu-id="fee09-118">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="fee09-119">Třídy definované v datech budou převedeny na typy kódu.</span><span class="sxs-lookup"><span data-stu-id="fee09-119">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="fee09-120">Používání nástrojů bez oprávnění správce</span><span class="sxs-lookup"><span data-stu-id="fee09-120">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="fee09-121">Aby uživatelé bez oprávnění správce mohli vyvíjet služby WCF, vytvoří se seznam ACL (Access Control) pro obor názvů "http://+:8731/Design_Time_Addresses" při instalaci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fee09-121">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="fee09-122">Seznam řízení přístupu (ACL) je nastavený na (uživatelské rozhraní), které zahrnuje všechny interaktivní uživatele přihlášené k počítači.</span><span class="sxs-lookup"><span data-stu-id="fee09-122">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="fee09-123">Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam ACL umožňuje odesílat a přijímat data v šablonách WCF nebo WF v jejich výchozí konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="fee09-123">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="fee09-124">Také umožňuje uživatelům používat automatické hostování služby WCF (wcfSvcHost. exe) bez udělení oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="fee09-124">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="fee09-125">Přístup můžete upravit pomocí nástroje Netsh. exe v systému Windows Vista pod účtem správce se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="fee09-125">You can modify access using the Netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="fee09-126">Následuje příklad použití nástroje Netsh. exe.</span><span class="sxs-lookup"><span data-stu-id="fee09-126">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="fee09-127">Další informace o nástroji Netsh. exe najdete v tématu [použití nástroje Netsh. exe a přepínačů příkazového řádku](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="fee09-127">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee09-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fee09-128">See also</span></span>

- [<span data-ttu-id="fee09-129">Šablony sady Visual Studio pro WCF</span><span class="sxs-lookup"><span data-stu-id="fee09-129">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="fee09-130">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="fee09-130">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="fee09-131">Testovací klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="fee09-131">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
