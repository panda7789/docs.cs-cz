---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 994e5146e9cf49a9b31396d0b51e7be83bbb3cfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964787"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="96b48-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="96b48-102">IWpfHostSupport</span></span>
<span data-ttu-id="96b48-103">Aplikace, které [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] hostují obsah prostřednictvím PresentationHost. exe, implementují toto rozhraní, aby poskytovaly bod integrace mezi hostitelem a PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="96b48-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96b48-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96b48-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]<span data-ttu-id="96b48-105">aplikace, jako jsou například webové prohlížeče [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] , mohou hostovat [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] obsah, včetně a volného kódu XAML.</span><span class="sxs-lookup"><span data-stu-id="96b48-105">applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="96b48-106">Pro hostování [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] obsahu aplikace vytvoří instanci [ovládacího prvku WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="96b48-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="96b48-107">Pro hostování [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] vytvoří instanci PresentationHost. exe, která poskytuje hostovanému [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsahu hostitele pro zobrazení v [ovládacím prvku WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="96b48-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="96b48-108">Integrace povolená pomocí `IWpfHostSupport` nástroje umožňuje PresentationHost. exe:</span><span class="sxs-lookup"><span data-stu-id="96b48-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="96b48-109">Vyhledejte a zaregistrujte se nezpracovanými vstupními zařízeními (zařízení s lidskými rozhraními), na které má hostitelská aplikace zájem.</span><span class="sxs-lookup"><span data-stu-id="96b48-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="96b48-110">Přijímat vstupní zprávy z registrovaných nezpracovaných vstupních zařízení a předají příslušné zprávy do hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="96b48-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="96b48-111">Dotazování hostitelské aplikace na vlastní průběh a chybná uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="96b48-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96b48-112">Toto rozhraní API je zamýšlené a podporované jenom pro použití v místním klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="96b48-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="96b48-113">Členové</span><span class="sxs-lookup"><span data-stu-id="96b48-113">Members</span></span>  
  
|<span data-ttu-id="96b48-114">Člen</span><span class="sxs-lookup"><span data-stu-id="96b48-114">Member</span></span>|<span data-ttu-id="96b48-115">Popis</span><span class="sxs-lookup"><span data-stu-id="96b48-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="96b48-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="96b48-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="96b48-117">Umožňuje PresentationHost. exe zjistit nezpracované vstupní zařízení (zařízení s lidskými rozhraními), na které hostitelská aplikace zajímá.</span><span class="sxs-lookup"><span data-stu-id="96b48-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="96b48-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="96b48-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="96b48-119">Volá se PresentationHost. exe, když se přijme zpráva, pokud se nevrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="96b48-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="96b48-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="96b48-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="96b48-121">Ve výchozím nastavení poskytuje PresentationHost. exe vlastní průběh nasazení a uživatelská rozhraní chyby nasazení, která se zobrazí při nasazení obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="96b48-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
