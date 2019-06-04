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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 426d77114d3deeff94c39e2f5fc1f2e56e753641
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490272"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy – rozhraní
Poskytuje [getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodu, která vrací ukazatel na obecné rozhraní language runtime (CLR) na základě kritérií zásad, spravované sestavení, verzi a konfiguračnímu souboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetRequestedRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|Poskytuje preferovaným rozhraním CLR na základě kritérií zásad, spravované sestavení, verzi a konfiguračnímu souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Odkaz na toto rozhraní můžete získat voláním [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fungovat tak, jak je znázorněno v následujícím kódu:  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  Toto rozhraní není ve skutečnosti načíst nebo aktivovat CLR, ale jednoduše vrátí upřednostňovanou verzi CLR na základě dostupné verze, které jsou nainstalovány nebo načtena.  
  
 Rozhraní .NET Framework 4, který je hostitelem rozhraní API konsoliduje zásady tak, aby hostitelé s konkrétním potřebám mohou používat základní funkce bez dalších nákladů na nežádoucí následky. Například řadu exporty MSCorEE.dll vytvoří vazbu na konkrétní CLR, i když metody nemusí stačit logicky ho. [Metahost_policy_flags –](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) výčet poskytuje zásady vazby, které jsou společné pro většinu hostitele.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
