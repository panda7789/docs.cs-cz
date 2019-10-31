---
title: IHostAssemblyManager::GetNonHostStoreAssemblies – metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
ms.openlocfilehash: eb715e1a4f9a210a1440874a9a8cea2d85345d33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124580"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a>IHostAssemblyManager::GetNonHostStoreAssemblies – metoda
Získá ukazatel rozhraní na [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , který představuje seznam sestavení, která hostitel očekává načtení modulu CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppReferenceList`  
 mimo Ukazatel na adresu `ICLRAssemblyReferenceList`, která obsahuje seznam odkazů na sestavení, která hostitel očekává načtení CLR.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetNonHostStoreAssemblies` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Není k dispozici dostatek paměti pro vytvoření seznamu odkazů pro požadovaný `ICLRAssemblyReferenceList`.|  
  
## <a name="remarks"></a>Poznámky  
 CLR vyřeší odkazy pomocí následující sady pokynů:  
  
- Nejprve se poraďte se seznamem odkazů na sestavení vrácených `GetNonHostStoreAssemblies`.  
  
- Pokud se v seznamu objeví sestavení, CLR se k němu váže normálně.  
  
- Pokud se sestavení v seznamu nezobrazí a hostitel zavedl implementaci [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), CLR volá [IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) , aby hostitel mohl poskytnout sestavení pro svázání.  
  
- V opačném případě se modul CLR nemůže připojit k sestavení.  
  
 Pokud se `ppReferenceList` hostitelů nastaví na hodnotu null, modul CLR nejprve testuje globální mezipaměť sestavení (GAC), zavolá `ProvideAssembly`a pak vyhledá základ aplikace, aby vyřešil odkaz na sestavení.  
  
> [!NOTE]
> Po inicializaci CLR volá `GetNonHostStoreAssemblies` pouze jednou. Metoda není volána znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
