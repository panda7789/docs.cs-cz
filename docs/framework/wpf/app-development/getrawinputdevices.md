---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 3531ff9f42289a3ad3b029f090f2dd4987e5886c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947911"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="e4c73-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="e4c73-102">GetRawInputDevices</span></span>
<span data-ttu-id="e4c73-103">Umožňuje PresentationHost.exe zjišťování zařízení nezpracovaná vstupní (lidské rozhraní zařízení), které hostitelskou aplikaci zájem.</span><span class="sxs-lookup"><span data-stu-id="e4c73-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4c73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4c73-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4c73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4c73-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="e4c73-106">[out] Ukazatel [ienumrawinputdevice –](ienumrawinputdevice.md) pro vytvoření výčtu nezpracovaná vstupní zařízení.</span><span class="sxs-lookup"><span data-stu-id="e4c73-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e4c73-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e4c73-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="e4c73-108">HODNOTA HRESULT:</span><span class="sxs-lookup"><span data-stu-id="e4c73-108">HRESULT:</span></span>  
  
 <span data-ttu-id="e4c73-109">S_OK - [ienumrawinputdevice –](ienumrawinputdevice.md) pouze použije PresentationHost.exe Pokud vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="e4c73-109">S_OK - [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="e4c73-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e4c73-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4c73-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4c73-111">Remarks</span></span>  
 <span data-ttu-id="e4c73-112">Nezpracovaná vstupní zařízení jsou sadu vstupní zařízení, která zahrnuje klávesnice, myš a méně tradiční zařízeními, jako je vzdálené řízení.</span><span class="sxs-lookup"><span data-stu-id="e4c73-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="e4c73-113">Jakmile se načíst seznam nezpracovaná vstupní zařízení, PresentationHost.exe zaregistruje zařízení pro příjem zpráv s oznámením WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="e4c73-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c73-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4c73-114">See also</span></span>

- [<span data-ttu-id="e4c73-115">GetRawInputDeviceList</span><span class="sxs-lookup"><span data-stu-id="e4c73-115">GetRawInputDeviceList</span></span>](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [<span data-ttu-id="e4c73-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="e4c73-116">FilterInputMessage</span></span>](filterinputmessage.md)
