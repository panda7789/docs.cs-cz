---
title: "Používání vývojářských nástrojů WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d253f38fab21496dd305cc67e7b6e84846579f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="613a9-102">Používání vývojářských nástrojů WCF</span><span class="sxs-lookup"><span data-stu-id="613a9-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="613a9-103">Tato část popisuje [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] nástroje pro vývoj, které vám může pomoci při vývoji vaší [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]služby.</span><span class="sxs-lookup"><span data-stu-id="613a9-103">This section describes the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)][!INCLUDE[indigo1](../../../includes/indigo1-md.md)] development tools that can assist you in developing your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]service.</span></span>  
  
 <span data-ttu-id="613a9-104">Můžete použít [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] šablony jako základ rychle vytvářet vlastní služby, potom použijte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatického hostitele služby a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testovacího klienta pro ladění a testování vaší služby.</span><span class="sxs-lookup"><span data-stu-id="613a9-104">You can use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] templates as a foundation to quickly build your own service, then use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host and [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client to debug and test your service.</span></span> <span data-ttu-id="613a9-105">Tyto nástroje společně poskytují rychlé a plynulé ladění a testování cyklu a bránit potřeba potvrdit k hostování modelu včas.</span><span class="sxs-lookup"><span data-stu-id="613a9-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="613a9-106">Nástroje pro vývojáře WCF</span><span class="sxs-lookup"><span data-stu-id="613a9-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="613a9-107">Šablony sady Visual Studio pro WCF</span><span class="sxs-lookup"><span data-stu-id="613a9-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="613a9-108">Můžete použít předdefinovanou [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] šablon projektů a položek v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] rychle sestavíte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby a okolního aplikace.</span><span class="sxs-lookup"><span data-stu-id="613a9-108">You can use the predefined [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] project and item templates in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] to quickly build [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="613a9-109">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="613a9-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="613a9-110">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Automaticky hostitel služby (WcfSvcHost.exe) umožňuje spustit [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ladicí program (F5) automaticky hostování a testovat službu byla implementována.</span><span class="sxs-lookup"><span data-stu-id="613a9-110">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (WcfSvcHost.exe) allows you to launch the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="613a9-111">Potom můžete otestovat pomocí služby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testování klienta (wcfTestClient.exe) nebo vlastního klienta najít a opravit všechny potenciální chyby.</span><span class="sxs-lookup"><span data-stu-id="613a9-111">You can then test the service using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="613a9-112">Testovací klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="613a9-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="613a9-113">Testovacího klienta (WcfTestClient.exe) je nástroj grafickým uživatelským rozhraním, který umožňuje vstupní parametry náhodné typy, odeslat tento vstup do služby a zobrazení, které odpovědi služba odesílá zpět.</span><span class="sxs-lookup"><span data-stu-id="613a9-113"> Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="613a9-114">Poskytuje bezproblémové služby testování prostředí při kombinaci s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatického hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="613a9-114">It provides a seamless service testing experience when combined with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host.</span></span>  
  
 [<span data-ttu-id="613a9-115">Generování tříd datových typů z XML</span><span class="sxs-lookup"><span data-stu-id="613a9-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="613a9-116">Data XML uložené do schránky můžete vložit do kódu stránky.</span><span class="sxs-lookup"><span data-stu-id="613a9-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="613a9-117">Třídy definované v datech se převede na typy kódu.</span><span class="sxs-lookup"><span data-stu-id="613a9-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="613a9-118">Pomocí nástrojů bez oprávnění správce</span><span class="sxs-lookup"><span data-stu-id="613a9-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="613a9-119">Aby mohli uživatelé bez oprávnění správce k vývoji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, ACL (seznam řízení přístupu) se vytvoří pro obor názvů "http://+:8731/Design_Time_Addresses" během instalace [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="613a9-119">To enable users without administrator privilege to develop [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="613a9-120">Seznam řízení přístupu je nastavené na (UI), který zahrnuje všechny interaktivní uživatelé přihlášení k počítači.</span><span class="sxs-lookup"><span data-stu-id="613a9-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="613a9-121">Správci mohou přidat nebo odebrat uživatele z tohoto seznamu ACL nebo otevřít další porty. Tento seznam ACL umožňuje WCF nebo WF šablon odesílat a přijímat data ve výchozí konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="613a9-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="613a9-122">Umožňuje také uživatelům používat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatického hostitele služby (wcfSvcHost.exe) bez je udělení oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="613a9-122">It also enables users to use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="613a9-123">Můžete upravit přístup pomocí nástroje Netsh.exe v [!INCLUDE[wv](../../../includes/wv-md.md)] pod účtem zvýšenými na úroveň správce.</span><span class="sxs-lookup"><span data-stu-id="613a9-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="613a9-124">Následuje příklad použití Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="613a9-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="613a9-125">Netsh.exe, najdete v části [jak pomocí nástroje Netsh.exe a přepínače příkazového řádku](http://go.microsoft.com/fwlink/?LinkId=97877).</span><span class="sxs-lookup"><span data-stu-id="613a9-125"> Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="613a9-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="613a9-126">See Also</span></span>  
 [<span data-ttu-id="613a9-127">Šablony sady Visual Studio pro WCF</span><span class="sxs-lookup"><span data-stu-id="613a9-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="613a9-128">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="613a9-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="613a9-129">Testovací klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="613a9-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
