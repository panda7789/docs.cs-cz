---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 4fc7a5021f9f8d9e6badcd3e13266fb8f4bfe7a4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991750"
---
# <a name="getrawinputdevices"></a><span data-ttu-id="b1a0a-102">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="b1a0a-102">GetRawInputDevices</span></span>
<span data-ttu-id="b1a0a-103">Umožňuje PresentationHost. exe zjistit nezpracované vstupní zařízení (zařízení s lidskými rozhraními), na které hostitelská aplikace zajímá.</span><span class="sxs-lookup"><span data-stu-id="b1a0a-103">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1a0a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1a0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1a0a-105">Parameters</span></span>  
 `ppEnum`  
  
 <span data-ttu-id="b1a0a-106">mimo Ukazatel na [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) pro vytvoření výčtu nezpracovaných vstupních zařízení.</span><span class="sxs-lookup"><span data-stu-id="b1a0a-106">[out] A pointer to an [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) for enumerating the raw input devices.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b1a0a-107">Hodnota vlastnosti / návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b1a0a-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="b1a0a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1a0a-108">HRESULT:</span></span>  
  
 <span data-ttu-id="b1a0a-109">S_OK- [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) bude použit pouze pomocí PresentationHost. exe, pokud je vráceno S_OK.</span><span class="sxs-lookup"><span data-stu-id="b1a0a-109">S_OK - [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) will only be used by PresentationHost.exe if S_OK is returned.</span></span>  
  
 <span data-ttu-id="b1a0a-110">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b1a0a-110">E_NOTIMPL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1a0a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1a0a-111">Remarks</span></span>  
 <span data-ttu-id="b1a0a-112">Nezpracované vstupní zařízení jsou sada vstupních zařízení, která zahrnují klávesnice, myši a méně tradiční zařízení jako vzdálené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="b1a0a-112">Raw input devices are the set of input devices that includes keyboards, mice, and less traditional devices like remote controls.</span></span>  
  
 <span data-ttu-id="b1a0a-113">Po načtení seznamu nezpracovaných vstupních zařízení se PresentationHost. exe registruje na zařízení, aby přijímala zprávy s oznámením WM_INPUT.</span><span class="sxs-lookup"><span data-stu-id="b1a0a-113">Once the list of raw input devices has been retrieved, PresentationHost.exe registers with the devices to receive WM_INPUT notification messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a0a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1a0a-114">See also</span></span>

- [<span data-ttu-id="b1a0a-115">GetRawInputDeviceList</span><span class="sxs-lookup"><span data-stu-id="b1a0a-115">GetRawInputDeviceList</span></span>](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [<span data-ttu-id="b1a0a-116">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="b1a0a-116">FilterInputMessage</span></span>](filterinputmessage.md)
