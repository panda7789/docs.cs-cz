---
title: "ICLRProbingAssemblyEnum::Get – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRProbingAssemblyEnum.Get
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd54558eeb49ebf7a2a2e9304830b09a08d1038e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
 [v] Index založený na nule identity sestavení vrátit.  
  
 `pwzBuffer`  
 [out] Vyrovnávací paměť obsahující data identit sestavení.  
  
 `pcchBufferSize`  
 [ve out] Velikost `pwzBuffer` vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`Get`úspěšně vrácena.|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer`je příliš malá.|  
|ERROR_NO_MORE_ITEMS|Výčet neobsahuje žádné další položky.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu. Následující volání žádné hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Identita indexem 0 je identity, které jsou specifické pro architekturu procesoru. Identita indexem 1 je architektura jazykově neutrální sestavení pro Microsoft (MSIL intermediate language). Identity na pozici 2 neobsahuje informace o architektuře.  
  
 `Get`obvykle nazývá dvakrát. První volání poskytuje hodnotu null pro `pwzBuffer`a nastaví `pcchBufferSize` vhodné pro velikost `pwzBuffer`. Druhé volání poskytuje správně velikostí `pwzBuffer`a obsahuje identifikační údaje kanonický sestavení po dokončení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRProbingAssemblyEnum – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
