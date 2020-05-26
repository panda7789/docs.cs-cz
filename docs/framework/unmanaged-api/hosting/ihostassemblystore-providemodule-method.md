---
title: IHostAssemblyStore::ProvideModule – metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
ms.openlocfilehash: 002f4177f19c2aae99e91e3fe1029b81e17481dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805003"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule – metoda
Vyřeší modul v rámci sestavení nebo propojeného (ale ne vloženého) souboru prostředků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBindInfo`  
 pro Ukazatel na instanci [modulebindinfo –](modulebindinfo-structure.md) , která popisuje požadovaný modul <xref:System.AppDomain> , sestavení a název modulu.  
  
 `pdwModuleId`  
 mimo Ukazatel na jedinečný identifikátor pro `IStream` obsahující načtený modul.  
  
 `ppStmModuleImage`  
 mimo Ukazatel na adresu `IStream` objektu, který obsahuje přenos přenosného spustitelného souboru (PE), který má být načten, nebo hodnotu null, pokud modul nebyl nalezen.  
  
 `ppStmPDB`  
 mimo Ukazatel na adresu `IStream` objektu, který obsahuje informace o programovém ladění (PDB) pro požadovaný modul nebo hodnotu null, pokud nebyl nalezen soubor. pdb.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ProvideModule`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|Požadované sestavení nebo propojený prostředek se nepovedlo najít.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId`není dostatečně velká, aby obsahoval identifikátor, který chce hostitel vrátit.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota identity vrácená pro `pdwModuleId` je určena hostitelem. Identifikátory musí být jedinečné v rámci životnosti procesu. CLR používá tuto hodnotu jako jedinečný identifikátor pro přidružený datový proud. Kontroluje každou hodnotu oproti hodnotám `pAssemblyId` vráceným voláními [ProvideAssembly –](ihostassemblystore-provideassembly-method.md) a proti hodnotám `pdwModuleId` vráceným jinými voláními `ProvideModule` . Pokud hostitel vrátí stejnou hodnotu identifikátoru pro jiný `IStream` , CLR zkontroluje, zda obsah tohoto datového proudu již byl namapován. Pokud ano, modul CLR načte existující kopii obrázku místo mapování nového. Proto se identifikátor nesmí ani překrývat s identifikátory sestavení vrácenými z `ProvideAssembly` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRAssemblyReferenceList – rozhraní](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](ihostassemblymanager-interface.md)
- [IHostAssemblyStore – rozhraní](ihostassemblystore-interface.md)
