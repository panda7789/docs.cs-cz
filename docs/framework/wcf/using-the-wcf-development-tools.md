---
title: Používání vývojářských nástrojů WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 82bb7e225492bcdba4d2e611de405a09571355c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183084"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="b2dc7-102">Používání vývojářských nástrojů WCF</span><span class="sxs-lookup"><span data-stu-id="b2dc7-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="b2dc7-103">Tato část popisuje vývojové nástroje sady Visual Studio, které vám mohou pomoci při vývoji služby WCFservice.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="b2dc7-104">Šablony sady Visual Studio můžete použít jako základ pro rychlé vytvoření vlastní služby a potom pomocí automatického hostitele služby WCF a testovacího klienta WCF k ladění a testování vaší služby.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="b2dc7-105">Tyto nástroje společně poskytují rychlé a bezproblémové ladění a testovací cyklus a vylučují potřebu zavázat se k hostitelskému modelu v rané fázi.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  

 > [!NOTE]
 > <span data-ttu-id="b2dc7-106">Počínaje Visual Studio 2017, wcf vývojové nástroje nejsou nainstalovány ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-106">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="b2dc7-107">Chcete-li tyto funkce používat, je nutné zajistit, aby byla v instalačníslužbě sady Visual Studio vybrána součást Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-107">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="b2dc7-108">Vývojářské nástroje WCF</span><span class="sxs-lookup"><span data-stu-id="b2dc7-108">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="b2dc7-109">Šablony sady Visual Studio pro WCF</span><span class="sxs-lookup"><span data-stu-id="b2dc7-109">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="b2dc7-110">Předdefinované šablony projektu a položek sady Visual Studio v sadě Visual Studio můžete rychle vytvářet služby WCF a okolní aplikace.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-110">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="b2dc7-111">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="b2dc7-111">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="b2dc7-112">Automatický hostitel služby WCF (WcfSvcHost.exe) umožňuje spustit ladicí program Sady Visual Studio (F5) pro automatické hostování a testování služby, kterou jste implementovali.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-112">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="b2dc7-113">Potom můžete otestovat službu pomocí WCF Test Client (wcfTestClient.exe) nebo vlastního klienta najít a opravit případné chyby.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-113">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="b2dc7-114">Testovací klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="b2dc7-114">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="b2dc7-115">WCF Test Client (WcfTestClient.exe) je nástroj GUI, který umožňuje zadat parametry libovolných typů, odeslat tento vstup do služby a zobrazit odpověď, kterou služba odešle zpět.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-115">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="b2dc7-116">Poskytuje bezproblémové testování služeb v kombinaci s automatickým hostitelem služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-116">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="b2dc7-117">Generování tříd datových typů z XML</span><span class="sxs-lookup"><span data-stu-id="b2dc7-117">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="b2dc7-118">Data XML uložená ve schránce lze vložit do znakové stránky.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-118">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="b2dc7-119">Třídy definované v datech budou převedeny na typy kódů.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-119">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="b2dc7-120">Použití nástrojů bez oprávnění správce</span><span class="sxs-lookup"><span data-stu-id="b2dc7-120">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="b2dc7-121">Chcete-li uživatelům bez oprávnění správce povolit vývoj služeb WCF, je běhemhttp://+:8731/Design_Time_Addressesinstalace sady Visual Studio vytvořen seznam ACL (Seznam řízení přístupu) pro obor názvů .</span><span class="sxs-lookup"><span data-stu-id="b2dc7-121">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="b2dc7-122">ACL je nastavena na (UI), který zahrnuje všechny interaktivní uživatele přihlášené k počítači.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-122">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="b2dc7-123">Správci mohou přidávat nebo odebírat uživatele z tohoto seznamu ACL nebo otevírat další porty. Tento přístupový kód umožňuje šablonám WCF nebo WF odesílat a přijímat data ve výchozí konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-123">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="b2dc7-124">Umožňuje také uživatelům používat automatický hostitel služby WCF (wcfSvcHost.exe) bez udělení oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-124">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="b2dc7-125">Přístup můžete upravit pomocí nástroje Netsh.exe v systému Windows Vista pod účtem správce se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-125">You can modify access using the Netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="b2dc7-126">Následuje příklad použití souboru Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="b2dc7-126">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="b2dc7-127">Další informace o nástroji Netsh.exe naleznete [v tématu Použití nástroje Netsh.exe tool a přepínačů příkazového řádku](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="b2dc7-127">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2dc7-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2dc7-128">See also</span></span>

- [<span data-ttu-id="b2dc7-129">Šablony sady Visual Studio pro WCF</span><span class="sxs-lookup"><span data-stu-id="b2dc7-129">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="b2dc7-130">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="b2dc7-130">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="b2dc7-131">Testovací klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="b2dc7-131">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
