---
title: Používání vývojářských nástrojů WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7e315c9e77eace9bdb0e66abed203452e5d7f9bb
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="7f2ac-102">Používání vývojářských nástrojů WCF</span><span class="sxs-lookup"><span data-stu-id="7f2ac-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="7f2ac-103">Tato část popisuje vývojářské nástroje Visual Studio, které vám může pomoci při vývoji vaší [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]služby.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-103">This section describes the Visual Studio development tools that can assist you in developing your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]service.</span></span>  
  
 <span data-ttu-id="7f2ac-104">Šablony sady Visual Studio můžete použít jako základ rychle vytvářet vlastní služby a pak použít [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatického hostitele služby a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testovacího klienta pro ladění a testování vaší služby.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host and [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client to debug and test your service.</span></span> <span data-ttu-id="7f2ac-105">Tyto nástroje společně poskytují rychlé a plynulé ladění a testování cyklu a bránit potřeba potvrdit k hostování modelu včas.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="7f2ac-106">Nástroje pro vývojáře WCF</span><span class="sxs-lookup"><span data-stu-id="7f2ac-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="7f2ac-107">Šablony sady Visual Studio pro WCF</span><span class="sxs-lookup"><span data-stu-id="7f2ac-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="7f2ac-108">Předdefinovaných šablon projektů a položek v sadě Visual Studio můžete použít v sadě Visual Studio můžete rychle vytvořit [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby a okolního aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-108">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="7f2ac-109">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="7f2ac-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="7f2ac-110">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Automaticky hostitel služby (WcfSvcHost.exe) umožňuje spuštění ladicího programu sady Visual Studio (F5) automaticky hostování a testovat službu byla implementována.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-110">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="7f2ac-111">Potom můžete otestovat pomocí služby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testování klienta (wcfTestClient.exe) nebo vlastního klienta najít a opravit všechny potenciální chyby.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-111">You can then test the service using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="7f2ac-112">Testovací klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="7f2ac-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="7f2ac-113"> Testovacího klienta (WcfTestClient.exe) je nástroj grafickým uživatelským rozhraním, který umožňuje vstupní parametry náhodné typy, odeslat tento vstup do služby a zobrazení, které odpovědi služba odesílá zpět.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-113"> Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="7f2ac-114">Poskytuje bezproblémové služby testování prostředí při kombinaci s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatického hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-114">It provides a seamless service testing experience when combined with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host.</span></span>  
  
 [<span data-ttu-id="7f2ac-115">Generování tříd datových typů z XML</span><span class="sxs-lookup"><span data-stu-id="7f2ac-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="7f2ac-116">Data XML uložené do schránky můžete vložit do kódu stránky.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="7f2ac-117">Třídy definované v datech se převede na typy kódu.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="7f2ac-118">Pomocí nástrojů bez oprávnění správce</span><span class="sxs-lookup"><span data-stu-id="7f2ac-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="7f2ac-119">Aby mohli uživatelé bez oprávnění správce k vývoji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, je vytvořit ACL (seznam řízení přístupu) pro obor názvů "http://+:8731/Design_Time_Addresses" při instalaci sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-119">To enable users without administrator privilege to develop [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="7f2ac-120">Seznam řízení přístupu je nastavené na (UI), který zahrnuje všechny interaktivní uživatelé přihlášení k počítači.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="7f2ac-121">Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam ACL umožňuje WCF nebo WF šablon odesílat a přijímat data ve výchozí konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="7f2ac-122">Umožňuje také uživatelům používat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatického hostitele služby (wcfSvcHost.exe) bez je udělení oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-122">It also enables users to use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="7f2ac-123">Můžete upravit přístup pomocí nástroje Netsh.exe v [!INCLUDE[wv](../../../includes/wv-md.md)] pod účtem zvýšenými na úroveň správce.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="7f2ac-124">Následuje příklad použití Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="7f2ac-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="7f2ac-125"> Netsh.exe, najdete v části [jak pomocí nástroje Netsh.exe a přepínače příkazového řádku](http://go.microsoft.com/fwlink/?LinkId=97877).</span><span class="sxs-lookup"><span data-stu-id="7f2ac-125"> Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f2ac-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f2ac-126">See Also</span></span>  
 [<span data-ttu-id="7f2ac-127">Šablony sady Visual Studio pro WCF</span><span class="sxs-lookup"><span data-stu-id="7f2ac-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="7f2ac-128">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="7f2ac-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="7f2ac-129">Testovací klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="7f2ac-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
