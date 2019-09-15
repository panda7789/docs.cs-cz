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
# <a name="getrawinputdevices"></a>GetRawInputDevices
Umožňuje PresentationHost. exe zjistit nezpracované vstupní zařízení (zařízení s lidskými rozhraními), na které hostitelská aplikace zajímá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
  
 mimo Ukazatel na [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) pro vytvoření výčtu nezpracovaných vstupních zařízení.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HRESULT  
  
 S_OK- [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) bude použit pouze pomocí PresentationHost. exe, pokud je vráceno S_OK.  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>Poznámky  
 Nezpracované vstupní zařízení jsou sada vstupních zařízení, která zahrnují klávesnice, myši a méně tradiční zařízení jako vzdálené ovládací prvky.  
  
 Po načtení seznamu nezpracovaných vstupních zařízení se PresentationHost. exe registruje na zařízení, aby přijímala zprávy s oznámením WM_INPUT.  
  
## <a name="see-also"></a>Viz také:

- [GetRawInputDeviceList](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [FilterInputMessage](filterinputmessage.md)
