---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: acaa3a2ff0f08f60956caedba60c996e01a6eff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546784"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="c4b73-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="c4b73-102">GetRawInputDevices</span></span>
<span data-ttu-id="c4b73-103">Umožňuje PresentationHost.exe ke zjištění nezpracovaná vstupní zařízení (zařízení s lidským rozhraní), která je zajímá hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c4b73-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4b73-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4b73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4b73-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="c4b73-106">[out] Ukazatel na [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) pro vytvoření výčtu nezpracovaná vstupní zařízení.</span><span class="sxs-lookup"><span data-stu-id="c4b73-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c4b73-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c4b73-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="c4b73-108">HRESULT:</span><span class="sxs-lookup"><span data-stu-id="c4b73-108">HRESULT:</span></span>  
  
 <span data-ttu-id="c4b73-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) pouze použije PresentationHost.exe S_OK je vrácen.</span><span class="sxs-lookup"><span data-stu-id="c4b73-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="c4b73-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c4b73-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4b73-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4b73-111">Remarks</span></span>  
 <span data-ttu-id="c4b73-112">Nezpracovaná vstupní zařízení jsou sada vstupní zařízení, která zahrnuje klávesnice, myš a méně tradiční zařízeními, jako je vzdálené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c4b73-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="c4b73-113">Po načtení seznamu nezpracovaná vstupní zařízení PresentationHost.exe registruje zařízení pro příjem zpráv s oznámením WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="c4b73-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b73-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4b73-114">See Also</span></span>  
 [http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputfunctions/getrawinputdevicelist.asp)  
 [<span data-ttu-id="c4b73-115">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="c4b73-115">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
