---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 1453946766e33843ae9e56f7a7f4dbf1678b81b5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991389"
---
# <a name="filterinputmessage"></a><span data-ttu-id="5a736-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="5a736-102">FilterInputMessage</span></span>
<span data-ttu-id="5a736-103">Volá se PresentationHost. exe, když se přijme zpráva, pokud se nevrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="5a736-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a736-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a736-104">Syntax</span></span>  
  
```cpp  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a736-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a736-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="5a736-106">pro Zpráva WM_INPUT odeslána do okna, které získává nezpracovaný vstup.</span><span class="sxs-lookup"><span data-stu-id="5a736-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="5a736-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5a736-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="5a736-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a736-108">HRESULT:</span></span>  
  
 <span data-ttu-id="5a736-109">S_OK – filtr nezpracovává zprávu a může dojít k dalšímu zpracování.</span><span class="sxs-lookup"><span data-stu-id="5a736-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="5a736-110">S_FALSE – filtr zpracoval tuto zprávu a žádné další zpracování by neměl nastat.</span><span class="sxs-lookup"><span data-stu-id="5a736-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="5a736-111">E_NOTIMPL – Pokud se vrátí tato hodnota, [FilterInputMessage](filterinputmessage.md) se nevolá znovu.</span><span class="sxs-lookup"><span data-stu-id="5a736-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="5a736-112">To může být vráceno z hostitelské aplikace, která se zajímá pouze o vlastní průběh a chybná uživatelská rozhraní PresentationHost. exe nemá zájem přecházet nezpracovanými vstupními zprávami z PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="5a736-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a736-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a736-113">Remarks</span></span>  
 <span data-ttu-id="5a736-114">PresentationHost. exe je cílem různých nezpracovaných vstupních zařízení, včetně klávesnice, myši a dálkových ovládání.</span><span class="sxs-lookup"><span data-stu-id="5a736-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="5a736-115">V některých případech je chování v hostitelské aplikaci závislé na vstupu, které by jinak bylo spotřebováno pomocí PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="5a736-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="5a736-116">Například hostitelská aplikace může záviset na přijímání určitých vstupních zpráv, aby bylo možné určit, zda se mají zobrazovat konkrétní prvky uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5a736-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="5a736-117">Aby mohla hostitelská aplikace přijímat nezbytné vstupní zprávy pro poskytnutí tohoto chování, předává PresentationHost. exe příslušné nezpracované vstupní zprávy do hostované aplikace voláním [FilterInputMessage](filterinputmessage.md).</span><span class="sxs-lookup"><span data-stu-id="5a736-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="5a736-118">Hostovaná aplikace obdrží nezpracované vstupní zprávy registrací se sadou nezpracovaných vstupních zařízení (zařízení s lidskými rozhraními) vrácenými funkcí [GetRawInputDevices](getrawinputdevices.md).</span><span class="sxs-lookup"><span data-stu-id="5a736-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a736-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a736-119">See also</span></span>

- [<span data-ttu-id="5a736-120">Zpráva WM_INPUT</span><span class="sxs-lookup"><span data-stu-id="5a736-120">WM_INPUT message</span></span>](/windows/desktop/inputdev/wm-input)
