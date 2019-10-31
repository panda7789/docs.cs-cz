---
title: ICLRMetaHostPolicy – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
ms.openlocfilehash: 277c13895374116eb67f6515f45df638f61b0453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140854"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy – rozhraní
Poskytuje metodu [GetRequestedRuntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) , která vrací ukazatel na rozhraní modulu CLR (Common Language Runtime) na základě kritérií zásad, spravovaného sestavení, verze a konfiguračního souboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetRequestedRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|Poskytuje preferované rozhraní CLR na základě kritérií zásad, spravovaného sestavení, verze a konfiguračního souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete získat odkaz na toto rozhraní voláním funkce [CLRCreateInstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) , jak je znázorněno v následujícím kódu:  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> Toto rozhraní ve skutečnosti nenačítá nebo neaktivuje modul CLR, ale jednoduše vrátí preferovanou verzi CLR na základě dostupných verzí, které jsou nainstalovány nebo načteny.  
  
 Rozhraní API pro .NET Framework 4 konsoliduje zásady, aby hostitelé s konkrétními požadavky mohli používat základní funkce, aniž by museli vymezit nezamýšlené pokuty. Například mnohé z exportů MSCorEE. dll se budou navazovat na konkrétní CLR, i když ji metoda nemusí logicky vyžadovat. Výčet [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) poskytuje zásady vazeb, které jsou společné pro většinu hostitelů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
