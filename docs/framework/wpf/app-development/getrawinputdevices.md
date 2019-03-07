---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 763767514f5f157c676f2e5c86ff9b1e4e64f233
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495244"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="b099b-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="b099b-102">GetRawInputDevices</span></span>
<span data-ttu-id="b099b-103">Umožňuje PresentationHost.exe zjišťování zařízení nezpracovaná vstupní (lidské rozhraní zařízení), které hostitelskou aplikaci zájem.</span><span class="sxs-lookup"><span data-stu-id="b099b-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b099b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b099b-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b099b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b099b-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="b099b-106">[out] Ukazatel [ienumrawinputdevice –](ienumrawinputdevice.md) pro vytvoření výčtu nezpracovaná vstupní zařízení.</span><span class="sxs-lookup"><span data-stu-id="b099b-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b099b-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b099b-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="b099b-108">HODNOTA HRESULT:</span><span class="sxs-lookup"><span data-stu-id="b099b-108">HRESULT:</span></span>  
  
 <span data-ttu-id="b099b-109">S_OK - [ienumrawinputdevice –](ienumrawinputdevice.md) pouze použije PresentationHost.exe Pokud vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="b099b-109">S_OK - [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="b099b-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b099b-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b099b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b099b-111">Remarks</span></span>  
 <span data-ttu-id="b099b-112">Nezpracovaná vstupní zařízení jsou sadu vstupní zařízení, která zahrnuje klávesnice, myš a méně tradiční zařízeními, jako je vzdálené řízení.</span><span class="sxs-lookup"><span data-stu-id="b099b-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="b099b-113">Jakmile se načíst seznam nezpracovaná vstupní zařízení, PresentationHost.exe zaregistruje zařízení pro příjem zpráv s oznámením WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="b099b-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b099b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b099b-114">See also</span></span>
- [<span data-ttu-id="b099b-115">GetRawInputDeviceList</span><span class="sxs-lookup"><span data-stu-id="b099b-115">GetRawInputDeviceList</span></span>](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [<span data-ttu-id="b099b-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="b099b-116">FilterInputMessage</span></span>](filterinputmessage.md)
