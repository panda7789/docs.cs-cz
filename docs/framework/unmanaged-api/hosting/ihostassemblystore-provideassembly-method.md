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
ms.openlocfilehash: 162def0d703ea81efc3df3ea5ee08b58e34822e6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501570"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly – metoda
Získá odkaz na sestavení, na které se neodkazuje [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , který se vrací z [IHostAssemblyManager:: GetNonHostStoreAssemblies –](ihostassemblymanager-getnonhoststoreassemblies-method.md). Modul CLR (Common Language Runtime) volá `ProvideAssembly` pro každé sestavení, které se v seznamu nezobrazí.  
  
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
 pro Ukazatel na instanci [assemblybindinfo –](assemblybindinfo-structure.md) , kterou hostitel používá k určení určitých vlastností vazby, včetně přítomnosti nebo nepřítomnosti jakékoli zásady správy verzí a sestavení, ke kterému se má vytvořit vazba.  
  
 `pAssemblyId`  
 mimo Ukazatel na jedinečný identifikátor pro požadované sestavení `IStream` .  
  
 `pHostContext`  
 mimo Ukazatel na data specifická pro hostitele, která se používají k určení legitimace požadovaného sestavení bez nutnosti vyvolání volání platformy. `pHostContext`odpovídá <xref:System.Reflection.Assembly.HostContext%2A> vlastnosti spravované <xref:System.Reflection.Assembly> třídy.  
  
 `ppStmAssemblyImage`  
 mimo Ukazatel na adresu obsahující `IStream` přenos přenosného spustitelného souboru (PE), který má být načten, nebo hodnotu null, pokud nebylo nalezeno sestavení.  
  
 `ppStmPDB`  
 mimo Ukazatel na adresu obsahující `IStream` informace o programovém ladění (PDB) nebo hodnotu null, pokud soubor. pdb nebyl nalezen.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|Požadované sestavení nebylo nalezeno.|  
|E_NOT_SUFFICIENT_BUFFER|Velikost vyrovnávací paměti určená parametrem není `pAssemblyId` dostatečně velká pro uložení identifikátoru, který chce hostitel vrátit.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota identity vrácená pro `pAssemblyId` je určena hostitelem. Identifikátory musí být jedinečné v rámci životnosti procesu. CLR používá tuto hodnotu jako jedinečný identifikátor pro datový proud. Kontroluje každou hodnotu oproti hodnotám `pAssemblyId` vráceným jinými voláními `ProvideAssembly` . Pokud hostitel vrátí stejnou `pAssemblyId` hodnotu pro jiný `IStream` , CLR zkontroluje, zda obsah tohoto datového proudu již byl namapován. Pokud ano, modul runtime načte existující kopii obrázku místo mapování nového.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAssemblyReferenceList – rozhraní](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](ihostassemblymanager-interface.md)
- [IHostAssemblyStore – rozhraní](ihostassemblystore-interface.md)
