---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: e3edd7f7080562d03453898dba7a9326561803b5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124192"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="7a098-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="7a098-102">IWpfHostSupport</span></span>
<span data-ttu-id="7a098-103">Aplikace, které hostují obsah [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] přes PresentationHost. exe, implementují toto rozhraní, aby poskytovaly bod integrace mezi hostitelem a PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="7a098-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a098-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a098-104">Remarks</span></span>  
 <span data-ttu-id="7a098-105">Aplikace Win32, jako jsou například webové prohlížeče, mohou hostovat obsah WPF, včetně aplikací prohlížeče XAML (XBAP) a volně XAML.</span><span class="sxs-lookup"><span data-stu-id="7a098-105">Win32 applications such as Web browsers can host WPF content, including XAML browser applications (XBAPs) and loose XAML.</span></span> <span data-ttu-id="7a098-106">Pro hostování obsahu WPF aplikace Win32 vytvoří instanci [ovládacího prvku WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="7a098-106">To host WPF content, Win32 applications create an instance of the [WebBrowser control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span> <span data-ttu-id="7a098-107">Aby bylo možné hostovat, WPF vytvoří instanci PresentationHost. exe, která poskytne hostovanému obsahu WPF na hostitele pro zobrazení v [ovládacím prvku WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="7a098-107">To be hosted, WPF creates an instance of PresentationHost.exe, which provides the hosted WPF content to the host for display in the [WebBrowser control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span>  
  
 <span data-ttu-id="7a098-108">Integrace povolená nástrojem `IWpfHostSupport` umožňuje PresentationHost. exe:</span><span class="sxs-lookup"><span data-stu-id="7a098-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="7a098-109">Vyhledejte a zaregistrujte se nezpracovanými vstupními zařízeními (zařízení s lidskými rozhraními), na které má hostitelská aplikace zájem.</span><span class="sxs-lookup"><span data-stu-id="7a098-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="7a098-110">Přijímat vstupní zprávy z registrovaných nezpracovaných vstupních zařízení a předají příslušné zprávy do hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a098-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="7a098-111">Dotazování hostitelské aplikace na vlastní průběh a chybná uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7a098-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a098-112">Toto rozhraní API je zamýšlené a podporované jenom pro použití v místním klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="7a098-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="7a098-113">Členové</span><span class="sxs-lookup"><span data-stu-id="7a098-113">Members</span></span>  
  
|<span data-ttu-id="7a098-114">Člen</span><span class="sxs-lookup"><span data-stu-id="7a098-114">Member</span></span>|<span data-ttu-id="7a098-115">Popis</span><span class="sxs-lookup"><span data-stu-id="7a098-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a098-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="7a098-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="7a098-117">Umožňuje PresentationHost. exe zjistit nezpracované vstupní zařízení (zařízení s lidskými rozhraními), na které hostitelská aplikace zajímá.</span><span class="sxs-lookup"><span data-stu-id="7a098-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="7a098-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="7a098-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="7a098-119">Volá se PresentationHost. exe při každém přijetí zprávy, pokud se nevrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="7a098-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="7a098-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="7a098-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="7a098-121">Ve výchozím nastavení poskytuje PresentationHost. exe vlastní průběh nasazení a uživatelská rozhraní chyby nasazení, která se zobrazí při nasazení obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="7a098-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
