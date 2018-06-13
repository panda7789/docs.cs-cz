---
title: Izolace sítě pro aplikace Windows Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d3a26d6c3fc500691fa007abfe9c8fd069f9e812
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398089"
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="dee42-102">Izolace sítě pro aplikace Windows Store</span><span class="sxs-lookup"><span data-stu-id="dee42-102">Network Isolation for Windows Store Apps</span></span>
<span data-ttu-id="dee42-103">Třídy v <xref:System.Net>, <xref:System.Net.Http>, a <xref:System.Net.Http.Headers> obory názvů lze použít k vývoji aplikací pro Windows Store nebo desktopových aplikacích.</span><span class="sxs-lookup"><span data-stu-id="dee42-103">Classes in the <xref:System.Net>,  <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="dee42-104">Pokud se použije v aplikaci Windows Store, třídy v tyto obory názvů jsou ovlivněné součástí modelu zabezpečení aplikací používá při izolaci sítě [!INCLUDE[win8](../../../includes/win8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dee42-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by the [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span> <span data-ttu-id="dee42-105">Možnosti příslušné sítě musí být povolen v manifest aplikace pro aplikace pro Windows Store pro systém umožňující přístup k síti.</span><span class="sxs-lookup"><span data-stu-id="dee42-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="dee42-106">Kontrolní seznam pro izolaci sítě</span><span class="sxs-lookup"><span data-stu-id="dee42-106">Checklist for Network Isolation</span></span>  
 <span data-ttu-id="dee42-107">Kontrolní seznam použijte Ujistěte se, že izolace sítě je nakonfigurován pro aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="dee42-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1.  <span data-ttu-id="dee42-108">Určuje směr požadavků na přístup sítě vyžaduje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dee42-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="dee42-109">To může být odchozí požadavky iniciované klientem nebo nevyžádaných příchozích požadavků nebo jejich kombinaci těchto typů požadavku sítě může být.</span><span class="sxs-lookup"><span data-stu-id="dee42-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2.  <span data-ttu-id="dee42-110">Určuje typ síťové prostředky, které tuto aplikaci bude komunikovat se.</span><span class="sxs-lookup"><span data-stu-id="dee42-110">Determine the type of network resources that that app will communicate with.</span></span> <span data-ttu-id="dee42-111">Aplikace může vyžadovat ke komunikaci s důvěryhodné prostředky v síti domácí nebo pracovní.</span><span class="sxs-lookup"><span data-stu-id="dee42-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="dee42-112">Aplikace může být potřeba komunikovat s prostředky v Internetu.</span><span class="sxs-lookup"><span data-stu-id="dee42-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="dee42-113">Aplikace může vyžadovat přístup k oba typy síťových prostředků.</span><span class="sxs-lookup"><span data-stu-id="dee42-113">An app might need access to both types of network resources.</span></span>  
  
3.  <span data-ttu-id="dee42-114">Konfigurace možností sítě minimální požadovaná izolace v manifest aplikace.</span><span class="sxs-lookup"><span data-stu-id="dee42-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4.  <span data-ttu-id="dee42-115">Nasazení a spuštění aplikace otestovat pomocí nástrojů izolace sítě pro řešení potíží.</span><span class="sxs-lookup"><span data-stu-id="dee42-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
 <span data-ttu-id="dee42-116">Podrobnější informace o tom, jak konfigurovat možnosti sítě a nástroje pro izolaci používají k řešení potíží izolace sítě najdete v tématu [jak nakonfigurovat možnosti izolace sítě](http://go.microsoft.com/fwlink/?LinkID=228265) v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] vývojáře dokumentace.</span><span class="sxs-lookup"><span data-stu-id="dee42-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](http://go.microsoft.com/fwlink/?LinkID=228265) in the [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee42-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="dee42-117">See Also</span></span>  
 [<span data-ttu-id="dee42-118">Připojení k webové službě</span><span class="sxs-lookup"><span data-stu-id="dee42-118">Connecting to a web service</span></span>](http://go.microsoft.com/fwlink/?LinkID=245696)  
 [<span data-ttu-id="dee42-119">Pokyny a kontrolní seznam pro izolaci sítě</span><span class="sxs-lookup"><span data-stu-id="dee42-119">Guidelines and checklist for network isolation</span></span>](http://go.microsoft.com/fwlink/?LinkID=228265)  
 [<span data-ttu-id="dee42-120">Rychlý úvod: Připojení pomocí položky HttpClient</span><span class="sxs-lookup"><span data-stu-id="dee42-120">Quickstart: Connecting using HttpClient</span></span>](http://go.microsoft.com/fwlink/?LinkId=245697)  
 [<span data-ttu-id="dee42-121">Jak používat HttpClient obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="dee42-121">How to use HttpClient handlers</span></span>](http://go.microsoft.com/fwlink/?LinkId=245699)  
 [<span data-ttu-id="dee42-122">Jak zabezpečit připojení HttpClient</span><span class="sxs-lookup"><span data-stu-id="dee42-122">How to secure HttpClient connections</span></span>](http://go.microsoft.com/fwlink/?LinkId=245698)  
 [<span data-ttu-id="dee42-123">Ukázka HttpClient</span><span class="sxs-lookup"><span data-stu-id="dee42-123">HttpClient Sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=242550)
