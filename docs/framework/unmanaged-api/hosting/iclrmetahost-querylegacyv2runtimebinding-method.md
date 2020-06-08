---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
ms.openlocfilehash: b270a6691d4e4ee4a5d0b42f424694eb7993e4e7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504144"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding – metoda
Vrátí rozhraní, které představuje modul runtime, ke kterému byly navázány starší verze zásad aktivace, například pomocí `useLegacyV2RuntimeActivationPolicy` atributu u položky konfiguračního souboru [ \<startup> elementu](../../configure-apps/file-schema/startup/startup-element.md) , přímým použitím starší verze aktivačních rozhraní API nebo voláním metody [ICLRRuntimeInfo:: bindaslegacyv2runtime –](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 pro Požadováno. aktuálně jediná platná hodnota pro tento parametr je `IID_ICLRRuntimeInfo` .  
  
 `ppUnk`  
 mimo Požadovanou. Až tato metoda vrátí, obsahuje ukazatel na rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , které představuje modul runtime, který je svázán se staršími zásadami aktivace.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Metoda se úspěšně dokončila a vrátila modul runtime, který se váže k zásadám aktivace starší verze.|  
|S_FALSE|Metoda se úspěšně dokončila, ale starší verze modulu runtime ještě není vázaná.|  
|E_NOINTERFACE|Metoda našla modul runtime, který byl svázán se staršími zásadami aktivace, ale není `riid` podporován modulem runtime.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRMetaHost – rozhraní](iclrmetahost-interface.md)
- [Hosting](index.md)
