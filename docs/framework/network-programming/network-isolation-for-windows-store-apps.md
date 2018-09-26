---
title: Izolace sítě pro aplikace Windows Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 97096d6fa41cd25a92c23cd47008b33fb6037190
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077431"
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="f1c4e-102">Izolace sítě pro aplikace Windows Store</span><span class="sxs-lookup"><span data-stu-id="f1c4e-102">Network Isolation for Windows Store Apps</span></span>
<span data-ttu-id="f1c4e-103">Třídy v <xref:System.Net>, <xref:System.Net.Http>, a <xref:System.Net.Http.Headers> obory názvů slouží k vývoji aplikací Windows Store a desktopové aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-103">Classes in the <xref:System.Net>,  <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="f1c4e-104">Při použití v aplikaci Windows Store, třídy v těchto oborech názvů jsou ovlivněny izolace sítě, součástí modelu zabezpečení aplikace používané [!INCLUDE[win8](../../../includes/win8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1c4e-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by the [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span> <span data-ttu-id="f1c4e-105">Musí být povoleno příslušné síťové funkce v manifestu aplikace pro Windows Store aplikaci pro systém umožňující přístup k síti.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="f1c4e-106">Kontrolní seznam pro izolaci sítě</span><span class="sxs-lookup"><span data-stu-id="f1c4e-106">Checklist for Network Isolation</span></span>  
 <span data-ttu-id="f1c4e-107">Kontrolní seznam použijte, abyste měli jistotu, že izolace sítě je nakonfigurován pro aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1.  <span data-ttu-id="f1c4e-108">Určení směru síťové požadavky na přístup potřebné aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="f1c4e-109">To může být odchozích požadavků klientem iniciované nebo nevyžádaná příchozí požadavky nebo může být kombinaci těchto typů požadavku sítě.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2.  <span data-ttu-id="f1c4e-110">Určete typ síťové prostředky, které tato aplikace bude komunikovat s.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-110">Determine the type of network resources that that app will communicate with.</span></span> <span data-ttu-id="f1c4e-111">Aplikace může potřebovat komunikovat s důvěryhodným prostředky v síti domácí nebo pracovní.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="f1c4e-112">Aplikace může být nutné pro komunikaci s prostředky v síti Internet.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="f1c4e-113">Aplikace může potřebovat přístup na oba typy síťových prostředků.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-113">An app might need access to both types of network resources.</span></span>  
  
3.  <span data-ttu-id="f1c4e-114">Konfigurace možností sítě minimální požadovanou izolaci v manifestu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4.  <span data-ttu-id="f1c4e-115">Nasazení a spuštění aplikace a otestovat ho pomocí nástrojů izolace sítě pro řešení potíží.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
 <span data-ttu-id="f1c4e-116">Podrobnější informace o tom, jak nakonfigurovat síťové funkce a nástroje pro izolaci používají k řešení potíží izolace sítě najdete v tématu [konfiguraci schopnosti izolace sítě](https://go.microsoft.com/fwlink/?LinkID=228265) v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] pro vývojáře dokumentace ke službě.</span><span class="sxs-lookup"><span data-stu-id="f1c4e-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](https://go.microsoft.com/fwlink/?LinkID=228265) in the [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c4e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1c4e-117">See Also</span></span>  
 [<span data-ttu-id="f1c4e-118">Připojení k webové službě</span><span class="sxs-lookup"><span data-stu-id="f1c4e-118">Connecting to a web service</span></span>](https://go.microsoft.com/fwlink/?LinkID=245696)  
 [<span data-ttu-id="f1c4e-119">Pokyny a kontrolní seznam pro izolaci sítě</span><span class="sxs-lookup"><span data-stu-id="f1c4e-119">Guidelines and checklist for network isolation</span></span>](https://go.microsoft.com/fwlink/?LinkID=228265)  
 [<span data-ttu-id="f1c4e-120">Rychlý start: Připojení pomocí položky HttpClient</span><span class="sxs-lookup"><span data-stu-id="f1c4e-120">Quickstart: Connecting using HttpClient</span></span>](https://go.microsoft.com/fwlink/?LinkId=245697)  
 [<span data-ttu-id="f1c4e-121">Jak používat HttpClient obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="f1c4e-121">How to use HttpClient handlers</span></span>](https://go.microsoft.com/fwlink/?LinkId=245699)  
 [<span data-ttu-id="f1c4e-122">Jak zabezpečit HttpClient připojení</span><span class="sxs-lookup"><span data-stu-id="f1c4e-122">How to secure HttpClient connections</span></span>](https://go.microsoft.com/fwlink/?LinkId=245698)  
 [<span data-ttu-id="f1c4e-123">Ukázka třídy HttpClient</span><span class="sxs-lookup"><span data-stu-id="f1c4e-123">HttpClient Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=242550)
