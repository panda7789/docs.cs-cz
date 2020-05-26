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
ms.openlocfilehash: 0dc2f625da7f4e37583f198c8d6dba86f6dcdb10
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805057"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a>IHostAssemblyManager::GetNonHostStoreAssemblies – metoda
Získá ukazatel rozhraní na [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , který představuje seznam sestavení, která hostitel očekává načtení modulu CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppReferenceList`  
 mimo Ukazatel na adresu obsahující `ICLRAssemblyReferenceList` seznam odkazů na sestavení, která hostitel očekává načtení CLR.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetNonHostStoreAssemblies`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Není k dispozici dostatek paměti pro vytvoření seznamu odkazů pro požadovaný počet `ICLRAssemblyReferenceList` .|  
  
## <a name="remarks"></a>Poznámky  
 CLR vyřeší odkazy pomocí následující sady pokynů:  
  
- Nejprve se poraďte se seznamem odkazů na sestavení vrácených `GetNonHostStoreAssemblies` .  
  
- Pokud se v seznamu objeví sestavení, CLR se k němu váže normálně.  
  
- Pokud se sestavení v seznamu nezobrazí a hostitel zavedl implementaci [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), CLR volá [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) , aby hostitel mohl poskytnout sestavení pro svázání.  
  
- V opačném případě se modul CLR nemůže připojit k sestavení.  
  
 Pokud hostitel nastaví `ppReferenceList` hodnotu null, modul CLR nejprve testuje globální mezipaměť sestavení (GAC), zavolá `ProvideAssembly` a pak vyhledá základ aplikace, aby vyřešil odkaz na sestavení.  
  
> [!NOTE]
> Po inicializaci vyvolá CLR `GetNonHostStoreAssemblies` pouze jednou. Metoda není volána znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRAssemblyReferenceList – rozhraní](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](ihostassemblymanager-interface.md)
- [IHostAssemblyStore – rozhraní](ihostassemblystore-interface.md)
