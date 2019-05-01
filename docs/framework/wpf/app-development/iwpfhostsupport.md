---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 074167111b78edc517dda019465260d0acd54737
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006691"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="cb347-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="cb347-102">IWpfHostSupport</span></span>
<span data-ttu-id="cb347-103">Aplikace, které hostují [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsahu prostřednictvím PresentationHost.exe implementace tohoto rozhraní stanovit bodů integrace mezi hostitelem a PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="cb347-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb347-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb347-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] <span data-ttu-id="cb347-105">může být hostitelem aplikací, jako jsou webové prohlížeče [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsah, včetně [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a volný XAML.</span><span class="sxs-lookup"><span data-stu-id="cb347-105">applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="cb347-106">K hostiteli [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsah, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikace vytvořit instanci [ovládací prvek WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="cb347-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="cb347-107">Zajistit také jejich hostování, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] vytvoří instanci PresentationHost.exe, která poskytuje hostovanou [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] hostitele pro zobrazení v obsahu [ovládací prvek WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="cb347-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="cb347-108">Integrace zajišťuje `IWpfHostSupport` umožňuje PresentationHost.exe na:</span><span class="sxs-lookup"><span data-stu-id="cb347-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="cb347-109">Zjistit a zaregistrovat nezpracovaná vstupní zařízení (lidské rozhraní), které je hostitelskou aplikaci zájem.</span><span class="sxs-lookup"><span data-stu-id="cb347-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="cb347-110">Přijímá vstupní zprávy z registrovaných nezpracovaná vstupní zařízení a předávání zpráv příslušné hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="cb347-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="cb347-111">Dotaz na hostitelskou aplikaci pro vlastní uživatelská rozhraní průběhu a chyba.</span><span class="sxs-lookup"><span data-stu-id="cb347-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb347-112">Toto rozhraní API je určen a podporovaných pro použití v místním klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="cb347-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="cb347-113">Členové</span><span class="sxs-lookup"><span data-stu-id="cb347-113">Members</span></span>  
  
|<span data-ttu-id="cb347-114">Člen</span><span class="sxs-lookup"><span data-stu-id="cb347-114">Member</span></span>|<span data-ttu-id="cb347-115">Popis</span><span class="sxs-lookup"><span data-stu-id="cb347-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb347-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="cb347-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="cb347-117">Umožňuje PresentationHost.exe zjišťování zařízení nezpracovaná vstupní (lidské rozhraní zařízení), které hostitelskou aplikaci zájem.</span><span class="sxs-lookup"><span data-stu-id="cb347-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="cb347-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="cb347-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="cb347-119">Voláno rozhraním PresentationHost.exe pokaždé, když je přijata zpráva, pokud je vrácena E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="cb347-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="cb347-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="cb347-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="cb347-121">Ve výchozím nastavení PresentationHost.exe poskytuje vlastní průběh nasazení a chyba nasazení uživatelská rozhraní, které se zobrazují při nasazení obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="cb347-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
