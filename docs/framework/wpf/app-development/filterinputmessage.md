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
# <a name="filterinputmessage"></a>FilterInputMessage
Volá se PresentationHost. exe, když se přijme zpráva, pokud se nevrátí E_NOTIMPL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
## <a name="parameters"></a>Parametry  
 `pMsg`  
  
 pro Zpráva WM_INPUT odeslána do okna, které získává nezpracovaný vstup.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HRESULT  
  
 S_OK – filtr nezpracovává zprávu a může dojít k dalšímu zpracování.  
  
 S_FALSE – filtr zpracoval tuto zprávu a žádné další zpracování by neměl nastat.  
  
 E_NOTIMPL – Pokud se vrátí tato hodnota, [FilterInputMessage](filterinputmessage.md) se nevolá znovu. To může být vráceno z hostitelské aplikace, která se zajímá pouze o vlastní průběh a chybná uživatelská rozhraní PresentationHost. exe nemá zájem přecházet nezpracovanými vstupními zprávami z PresentationHost. exe.  
  
## <a name="remarks"></a>Poznámky  
 PresentationHost. exe je cílem různých nezpracovaných vstupních zařízení, včetně klávesnice, myši a dálkových ovládání. V některých případech je chování v hostitelské aplikaci závislé na vstupu, které by jinak bylo spotřebováno pomocí PresentationHost. exe. Například hostitelská aplikace může záviset na přijímání určitých vstupních zpráv, aby bylo možné určit, zda se mají zobrazovat konkrétní prvky uživatelského rozhraní.  
  
 Aby mohla hostitelská aplikace přijímat nezbytné vstupní zprávy pro poskytnutí tohoto chování, předává PresentationHost. exe příslušné nezpracované vstupní zprávy do hostované aplikace voláním [FilterInputMessage](filterinputmessage.md).  
  
 Hostovaná aplikace obdrží nezpracované vstupní zprávy registrací se sadou nezpracovaných vstupních zařízení (zařízení s lidskými rozhraními) vrácenými funkcí [GetRawInputDevices](getrawinputdevices.md).  
  
## <a name="see-also"></a>Viz také:

- [Zpráva WM_INPUT](/windows/desktop/inputdev/wm-input)
