---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 0cb1184ddc3e8051a68dfed12367dea65a06b623
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50034486"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="56ef6-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="56ef6-102">GetRawInputDevices</span></span>
<span data-ttu-id="56ef6-103">Umožňuje PresentationHost.exe zjišťování zařízení nezpracovaná vstupní (lidské rozhraní zařízení), které hostitelskou aplikaci zájem.</span><span class="sxs-lookup"><span data-stu-id="56ef6-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ef6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56ef6-104">Syntax</span></span>  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56ef6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56ef6-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="56ef6-106">[out] Ukazatel [ienumrawinputdevice –](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) pro vytvoření výčtu nezpracovaná vstupní zařízení.</span><span class="sxs-lookup"><span data-stu-id="56ef6-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="56ef6-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="56ef6-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="56ef6-108">HODNOTA HRESULT:</span><span class="sxs-lookup"><span data-stu-id="56ef6-108">HRESULT:</span></span>  
  
 <span data-ttu-id="56ef6-109">S_OK - [ienumrawinputdevice –](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) pouze použije PresentationHost.exe Pokud vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="56ef6-109">S_OK - [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="56ef6-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="56ef6-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56ef6-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56ef6-111">Remarks</span></span>  
 <span data-ttu-id="56ef6-112">Nezpracovaná vstupní zařízení jsou sadu vstupní zařízení, která zahrnuje klávesnice, myš a méně tradiční zařízeními, jako je vzdálené řízení.</span><span class="sxs-lookup"><span data-stu-id="56ef6-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="56ef6-113">Jakmile se načíst seznam nezpracovaná vstupní zařízení, PresentationHost.exe zaregistruje zařízení pro příjem zpráv s oznámením WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="56ef6-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ef6-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="56ef6-114">See Also</span></span>  
 [<span data-ttu-id="56ef6-115">GetRawInputDeviceList</span><span class="sxs-lookup"><span data-stu-id="56ef6-115">GetRawInputDeviceList</span></span>](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)  
 [<span data-ttu-id="56ef6-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="56ef6-116">FilterInputMessage</span></span>](../../../../docs/framework/wpf/app-development/filterinputmessage.md)
