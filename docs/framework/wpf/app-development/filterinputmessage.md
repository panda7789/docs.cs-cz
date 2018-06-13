---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 69bc1e973b690454bcf91487c12dc4ce0ac46a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548402"
---
# <a name="filterinputmessage"></a>FilterInputMessage
Voláno rozhraním PresentationHost.exe vždy, když je přijata zpráva, pokud je vrácen E_NOTIMPL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMsg`  
  
 [v] Zpráva WM_INPUT odeslána do okna, který je získávání nezpracovaná vstup.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HRESULT:  
  
 S_OK - filtr nemohl zpracovat zprávu a může dojít k dalšímu zpracování.  
  
 S_FALSE - filtr zpracovat tuto zprávu a mělo dojít k žádné další zpracování.  
  
 E_NOTIMPL – Pokud je tato hodnota se vrátí, [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md) není volán znovu. To může být vrácena z hostitelskou aplikaci, která je jenom zajímá poskytování vlastních průběh a chyby uživatelského rozhraní pro PresentationHost.exe není zajímá předávaná nezpracovaná vstupní zprávy ze PresentationHost.exe.  
  
## <a name="remarks"></a>Poznámky  
 PresentationHost.exe je cílem různé nezpracovaná vstupní zařízení, včetně klávesnice, myš a vzdálené ovládací prvky. V některých případech je závislá na vstupu, které by jinak spotřebovat PresentationHost.exe chování v hostitelskou aplikaci. Hostitelskou aplikaci může například závisí na příjem určité vstupní zprávy a určete, zda se má zobrazit konkrétní prvky rozhraní.  
  
 Povolit hostitelskou aplikaci pro příjem nezbytné vstupní zpráv k poskytování těchto chování, PresentationHost.exe předává odpovídající nezpracovaná vstupní zprávy do aplikace hostované voláním [FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md).  
  
 Aplikace hostované přijímá nezpracovaná vstupní zprávy pomocí registrace sady nezpracovaná vstupní zařízení (zařízení standardu HID) vrácený [GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).  
  
## <a name="see-also"></a>Viz také  
 [WM_INPUT oznámení](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
