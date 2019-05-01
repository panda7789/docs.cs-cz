---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: bd696752a287a78533d55c0fd3ad9986a32bd180
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052206"
---
# <a name="filterinputmessage"></a><span data-ttu-id="aee3a-102">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="aee3a-102">FilterInputMessage</span></span>
<span data-ttu-id="aee3a-103">Voláno rozhraním PresentationHost.exe pokaždé, když je přijata zpráva, pokud je vrácena E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="aee3a-103">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aee3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aee3a-104">Syntax</span></span>  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
## <a name="parameters"></a><span data-ttu-id="aee3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aee3a-105">Parameters</span></span>  
 `pMsg`  
  
 <span data-ttu-id="aee3a-106">[in] WM_INPUT zpráva odeslaná do okna, které dostává Nezpracovaný vstup.</span><span class="sxs-lookup"><span data-stu-id="aee3a-106">[in] The WM_INPUT message sent to the window that is getting raw input.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="aee3a-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aee3a-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="aee3a-108">HODNOTA HRESULT:</span><span class="sxs-lookup"><span data-stu-id="aee3a-108">HRESULT:</span></span>  
  
 <span data-ttu-id="aee3a-109">S_OK - filtr nemohl zpracovat zprávu a může dojít k dalšímu zpracování.</span><span class="sxs-lookup"><span data-stu-id="aee3a-109">S_OK - The filter did not process the message and further processing may occur.</span></span>  
  
 <span data-ttu-id="aee3a-110">S_FALSE - filtr zpracovat tuto zprávu a by mělo dojít k žádné další zpracování.</span><span class="sxs-lookup"><span data-stu-id="aee3a-110">S_FALSE - The filter processed this message and no further processing should occur.</span></span>  
  
 <span data-ttu-id="aee3a-111">E_NOTIMPL – Pokud je tato hodnota se vrátí, [filterinputmessage –](filterinputmessage.md) není volána znovu.</span><span class="sxs-lookup"><span data-stu-id="aee3a-111">E_NOTIMPL – If this value is returned, [FilterInputMessage](filterinputmessage.md) is not called again.</span></span> <span data-ttu-id="aee3a-112">To může být vrácena z hostitele aplikace, která interested pouze při poskytování vlastní pokrok a chyba uživatelských rozhraní k PresentationHost.exe není zajímá se předalo PresentationHost.exe nezpracované zprávy o zadávání.</span><span class="sxs-lookup"><span data-stu-id="aee3a-112">This might be returned from a host application that is only interested in providing custom progress and error user interfaces to PresentationHost.exe is not interested in being forwarded raw input messages from PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aee3a-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aee3a-113">Remarks</span></span>  
 <span data-ttu-id="aee3a-114">PresentationHost.exe je cílem různých nezpracovaná vstupní zařízení, včetně klávesnice, myš a dálková ovládání.</span><span class="sxs-lookup"><span data-stu-id="aee3a-114">PresentationHost.exe is the target of various raw input devices, including keyboard, mice, and remote controls.</span></span> <span data-ttu-id="aee3a-115">V některých případech je závislá na vstupu, který by jinak využívat PresentationHost.exe chování v hostitelské aplikaci.</span><span class="sxs-lookup"><span data-stu-id="aee3a-115">Sometimes, behavior in the host application is dependent on input that would otherwise be consumed by PresentationHost.exe.</span></span> <span data-ttu-id="aee3a-116">Například hostitelská aplikace může záviset na příjem některé vstupní zprávy k určení, jestli se mají zobrazit prvky konkrétní uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aee3a-116">For example, a host application may depend on receiving certain input messages to determine whether or not to display specific user interface elements.</span></span>  
  
 <span data-ttu-id="aee3a-117">Aby hostitelskou aplikaci pro příjem nezbytné vstupní zprávy k poskytování těchto projevů PresentationHost.exe předává odpovídající nezpracované zprávy o zadávání hostované aplikace voláním [filterinputmessage –](filterinputmessage.md).</span><span class="sxs-lookup"><span data-stu-id="aee3a-117">To allow the host application to receive the necessary input messages to provide these behaviors, PresentationHost.exe forwards appropriate raw input messages to the hosted application by calling [FilterInputMessage](filterinputmessage.md).</span></span>  
  
 <span data-ttu-id="aee3a-118">Hostované aplikace přijme nezpracované zprávy o zadávání tak, že zaregistrujete sadu nezpracovaná vstupní zařízení (lidské rozhraní) vrácený [getrawinputdevices –](getrawinputdevices.md).</span><span class="sxs-lookup"><span data-stu-id="aee3a-118">The hosted application receives raw input messages by registering with the set of raw input devices (Human Interface Devices) returned by [GetRawInputDevices](getrawinputdevices.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee3a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aee3a-119">See also</span></span>

- [<span data-ttu-id="aee3a-120">WM_INPUT zprávy</span><span class="sxs-lookup"><span data-stu-id="aee3a-120">WM_INPUT message</span></span>](/windows/desktop/inputdev/wm-input)
