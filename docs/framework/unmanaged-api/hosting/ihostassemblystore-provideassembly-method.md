---
title: IHostAssemblyStore::ProvideAssembly – metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
ms.openlocfilehash: a93d700c9c398076d87156cd2eb9c6d0d08cccfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124489"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly – metoda
Získá odkaz na sestavení, na které se neodkazuje [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , který se vrací z [IHostAssemblyManager:: GetNonHostStoreAssemblies –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). Modul CLR (Common Language Runtime) `ProvideAssembly` volá pro každé sestavení, které se nezobrazí v seznamu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBindInfo`  
 pro Ukazatel na instanci [assemblybindinfo –](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) , kterou hostitel používá k určení určitých vlastností vazby, včetně přítomnosti nebo nepřítomnosti jakékoli zásady správy verzí a sestavení, ke kterému se má vytvořit vazba.  
  
 `pAssemblyId`  
 mimo Ukazatel na jedinečný identifikátor pro požadované sestavení pro tento `IStream`.  
  
 `pHostContext`  
 mimo Ukazatel na data specifická pro hostitele, která se používají k určení legitimace požadovaného sestavení bez nutnosti vyvolání volání platformy. `pHostContext` odpovídá vlastnosti <xref:System.Reflection.Assembly.HostContext%2A> spravované třídy <xref:System.Reflection.Assembly>.  
  
 `ppStmAssemblyImage`  
 mimo Ukazatel na adresu `IStream` obsahující přenosné spustitelné soubory (PE), které mají být načteny, nebo hodnotu null, pokud nebylo nalezeno sestavení.  
  
 `ppStmPDB`  
 mimo Ukazatel na adresu `IStream`, který obsahuje informace o ladění programu (PDB), nebo hodnotu null, pokud se nepovedlo najít soubor. pdb.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|Požadované sestavení nebylo nalezeno.|  
|E_NOT_SUFFICIENT_BUFFER|Velikost vyrovnávací paměti určená `pAssemblyId` není dostatečně velká pro uložení identifikátoru, který chce hostitel vrátit.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota identity vrácená pro `pAssemblyId` je určena hostitelem. Identifikátory musí být jedinečné v rámci životnosti procesu. CLR používá tuto hodnotu jako jedinečný identifikátor pro datový proud. Kontroluje každou hodnotu proti hodnotám `pAssemblyId` vrácených jinými voláními `ProvideAssembly`. Pokud hostitel vrátí stejnou `pAssemblyId` hodnotu pro jiný `IStream`, CLR zkontroluje, zda obsah tohoto datového proudu již byl namapován. Pokud ano, modul runtime načte existující kopii obrázku místo mapování nového.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
