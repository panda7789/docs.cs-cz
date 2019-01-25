---
title: ICLRProbingAssemblyEnum::Get – metoda
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54d0f4582805b140aafd5825e34c429992e9bbcc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707736"
---
# <a name="iclrprobingassemblyenumget-method"></a>ICLRProbingAssemblyEnum::Get – metoda
Získá identitu sestavení v zadaném indexu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwIndex`  
 [in] Index založený na nule Identita sestavení vrátit.  
  
 `pwzBuffer`  
 [out] Vyrovnávací paměť obsahující data identity sestavení.  
  
 `pcchBufferSize`  
 [out v] Velikost `pwzBuffer` vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`Get` bylo úspěšně vráceno.|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` je příliš malá.|  
|ERROR_NO_MORE_ITEMS|Výčet neobsahuje žádné další položky.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání jakékoli hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Identita na pozici 0 je specifické pro architekturu procesoru identity. Identita na indexu 1 je sestavení nezávislá na architekturu pro jazyk Microsoft intermediate language (MSIL). Identita na pozici 2 neobsahuje žádné informace o architektuře.  
  
 `Get` je obvykle volána dvakrát. První volání je zadán pro hodnotu null `pwzBuffer`a nastaví `pcchBufferSize` vhodné pro velikost `pwzBuffer`. Druhém volání je zadán odpovídající velikosti `pwzBuffer`a obsahuje data identit canonical sestavení po dokončení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRProbingAssemblyEnum – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
