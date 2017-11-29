---
title: IWpfHostSupport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 85d4ed09d6c5ca17e148d531e6aac483ff737d51
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="1ff9d-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="1ff9d-102">IWpfHostSupport</span></span>
<span data-ttu-id="1ff9d-103">Aplikace, které jsou hostiteli [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsahu prostřednictvím PresentationHost.exe implementace tohoto rozhraní nabízí bod integrace mezi hostitelem a PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="1ff9d-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ff9d-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ff9d-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]<span data-ttu-id="1ff9d-105">může být hostitelem aplikací, jako jsou webové prohlížeče [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsahu, včetně [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a ztrátě XAML.</span><span class="sxs-lookup"><span data-stu-id="1ff9d-105"> applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="1ff9d-106">K hostiteli [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsahu, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] vytvořit instanci aplikace [WebBrowser – ovládací prvek](http://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="1ff9d-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](http://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="1ff9d-107">Pro hostování, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] vytvoří instanci PresentationHost.exe, která poskytuje hostované [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsahu pro zobrazení v hostiteli [WebBrowser – ovládací prvek](http://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="1ff9d-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](http://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="1ff9d-108">Integrace ve povolené `IWpfHostSupport` umožňuje PresentationHost.exe na:</span><span class="sxs-lookup"><span data-stu-id="1ff9d-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
-   <span data-ttu-id="1ff9d-109">Vyhledejte a zaregistrujte se nezpracovaná vstupní zařízení (zařízení s lidským rozhraní), která je zajímá hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1ff9d-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
-   <span data-ttu-id="1ff9d-110">Přijímat vstupní zprávy z registrovaných nezpracovaná vstupní zařízení a předávání zpráv odpovídající hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1ff9d-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
-   <span data-ttu-id="1ff9d-111">Dotaz hostitelskou aplikaci pro vlastní uživatelská rozhraní průběh a chyby.</span><span class="sxs-lookup"><span data-stu-id="1ff9d-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ff9d-112">Toto rozhraní API je určen a podporovaných pro použití v místním klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="1ff9d-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="1ff9d-113">Členové</span><span class="sxs-lookup"><span data-stu-id="1ff9d-113">Members</span></span>  
  
|<span data-ttu-id="1ff9d-114">Člen</span><span class="sxs-lookup"><span data-stu-id="1ff9d-114">Member</span></span>|<span data-ttu-id="1ff9d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1ff9d-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ff9d-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="1ff9d-116">GetRawInputDevices</span></span>](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|<span data-ttu-id="1ff9d-117">Umožňuje PresentationHost.exe ke zjištění nezpracovaná vstupní zařízení (zařízení s lidským rozhraní), která je zajímá hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1ff9d-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="1ff9d-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="1ff9d-118">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|<span data-ttu-id="1ff9d-119">Voláno rozhraním PresentationHost.exe vždy, když je přijata zpráva, pokud je vrácen E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="1ff9d-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="1ff9d-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="1ff9d-120">GetCustomUI</span></span>](../../../../docs/framework/wpf/app-development/getcustomui.md)|<span data-ttu-id="1ff9d-121">Ve výchozím nastavení PresentationHost.exe poskytuje svou vlastní průběh nasazení a chyba nasazení uživatelského rozhraní, které se zobrazí při nasazení obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="1ff9d-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
