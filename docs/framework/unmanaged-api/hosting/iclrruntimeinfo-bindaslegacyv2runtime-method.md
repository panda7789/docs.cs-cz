---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: 4390f379e5092cc59d123631f5e6d8da82e2bd7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703889"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime – metoda
Váže aktuální modul runtime pro všechna starší verze modulu CLR (Common Language Runtime) verze 2 – rozhodnutí zásad aktivace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT:  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Buď byla vazba úspěšná, nebo tento modul runtime již byl svázán jako starší modul runtime zásad aktivace CLR verze 2.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Jiný modul runtime již byl svázán se staršími zásadami aktivace CLR verze 2.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je aktuální modul runtime již vázán pro všechna starší rozhodnutí zásad aktivace CLR verze 2 (například pomocí `useLegacyV2RuntimeActivationPolicy` atributu při [ \< spuštění> elementu](../../configure-apps/file-schema/startup/startup-element.md) v konfiguračním souboru), tato metoda nevrátí výsledek chyby; namísto toho je výsledek S_OK stejným způsobem, jako by byla metoda úspěšně vázaná na starší Zásady aktivace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRRuntimeInfo – rozhraní](iclrruntimeinfo-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hostování](index.md)
- [\<spouštěcí> – element](../../configure-apps/file-schema/startup/startup-element.md)
