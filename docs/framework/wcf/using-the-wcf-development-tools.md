---
title: Používání vývojářských nástrojů WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 41d2ee2881b79ffb086a931ec6d271d409ac66db
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="def19-102">Používání vývojářských nástrojů WCF</span><span class="sxs-lookup"><span data-stu-id="def19-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="def19-103">Tato část popisuje vývojářské nástroje Visual Studio, které vám může pomoci při vývoji vaší WCFservice.</span><span class="sxs-lookup"><span data-stu-id="def19-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="def19-104">Můžete používat šablony sady Visual Studio jako základ pro rychle vytvářet vlastní služby a pak pomocí automatického hostitele služby WCF a testovacího klienta WCF pro ladění a testování vaší služby.</span><span class="sxs-lookup"><span data-stu-id="def19-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="def19-105">Tyto nástroje společně poskytují rychlé a plynulé ladění a testování cyklu a bránit potřeba potvrdit k hostování modelu včas.</span><span class="sxs-lookup"><span data-stu-id="def19-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="def19-106">Nástroje pro vývojáře WCF</span><span class="sxs-lookup"><span data-stu-id="def19-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="def19-107">Šablony sady Visual Studio pro WCF</span><span class="sxs-lookup"><span data-stu-id="def19-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="def19-108">Předdefinovaných šablon projektů a položek v sadě Visual Studio v sadě Visual Studio vám pomůže rychle vytvářet služby WCF a okolního aplikace.</span><span class="sxs-lookup"><span data-stu-id="def19-108">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="def19-109">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="def19-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="def19-110">Automatické hostitel služby WCF (WcfSvcHost.exe) umožňuje spuštění ladicího programu sady Visual Studio (F5) automaticky hostování a testovat službu, kterou jste implementovali.</span><span class="sxs-lookup"><span data-stu-id="def19-110">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="def19-111">Potom můžete otestovat pomocí klienta WCF Test (wcfTestClient.exe) nebo vlastního klienta najít a opravit všechny potenciální chyby.</span><span class="sxs-lookup"><span data-stu-id="def19-111">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="def19-112">Testovací klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="def19-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="def19-113">Testovacího klienta WCF (WcfTestClient.exe) je nástroj grafickým uživatelským rozhraním, který umožňuje vstupní parametry náhodné typy, odeslat tento vstup do služby a zobrazení, které odpovědi služba odesílá zpět.</span><span class="sxs-lookup"><span data-stu-id="def19-113">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="def19-114">Poskytuje bezproblémové služby testování prostředí při kombinaci s automaticky hostitel služby WCF.</span><span class="sxs-lookup"><span data-stu-id="def19-114">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="def19-115">Generování tříd datových typů z XML</span><span class="sxs-lookup"><span data-stu-id="def19-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="def19-116">Data XML uložené do schránky můžete vložit do kódu stránky.</span><span class="sxs-lookup"><span data-stu-id="def19-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="def19-117">Třídy definované v datech se převede na typy kódu.</span><span class="sxs-lookup"><span data-stu-id="def19-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="def19-118">Pomocí nástrojů bez oprávnění správce</span><span class="sxs-lookup"><span data-stu-id="def19-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="def19-119">Pokud chcete povolit uživatelům bez oprávnění správce k vývoji služeb WCF, se vytvoří ACL (seznam řízení přístupu) pro obor názvů "http://+:8731/Design_Time_Addresses" při instalaci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="def19-119">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="def19-120">Seznam řízení přístupu je nastavené na (UI), který zahrnuje všechny interaktivní uživatelé přihlášení k počítači.</span><span class="sxs-lookup"><span data-stu-id="def19-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="def19-121">Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam ACL umožňuje WCF nebo WF šablon odesílat a přijímat data ve výchozí konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="def19-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="def19-122">Taky umožňuje uživatelům používat automatické hostitel služby WCF (wcfSvcHost.exe) bez je udělení oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="def19-122">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="def19-123">Můžete upravit přístup pomocí nástroje Netsh.exe v [!INCLUDE[wv](../../../includes/wv-md.md)] pod účtem zvýšenými na úroveň správce.</span><span class="sxs-lookup"><span data-stu-id="def19-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="def19-124">Následuje příklad použití Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="def19-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="def19-125">Další informace o Netsh.exe najdete v tématu [jak pomocí nástroje Netsh.exe a přepínače příkazového řádku](http://go.microsoft.com/fwlink/?LinkId=97877).</span><span class="sxs-lookup"><span data-stu-id="def19-125">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def19-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="def19-126">See Also</span></span>  
 [<span data-ttu-id="def19-127">Šablony sady Visual Studio pro WCF</span><span class="sxs-lookup"><span data-stu-id="def19-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="def19-128">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="def19-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="def19-129">Testovací klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="def19-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
