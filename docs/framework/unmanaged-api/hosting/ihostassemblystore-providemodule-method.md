---
title: "IHostAssemblyStore::ProvideModule – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8b29f19933ae985d15627d1eba2622f350a52e72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule – metoda
Přeloží souboru prostředků modulu v sestavení nebo spojen (ale nikoli vložené).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBindInfo`  
 [v] Ukazatel [modulebindinfo –](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instanci, která popisuje požadovaný modul <xref:System.AppDomain>, sestavení a název modulu.  
  
 `pdwModuleId`  
 [out] Ukazatel na jedinečný identifikátor `IStream` obsahující načíst modul.  
  
 `ppStmModuleImage`  
 [out] Ukazatel na adresu `IStream` objektu, který obsahuje bitovou kopii přenosné spustitelný soubor (PE) mají být načteny, nebo hodnota null, pokud modul nebyl nalezen.  
  
 `ppStmPDB`  
 [out] Ukazatel na adresu `IStream` objektu, který obsahuje informace o ladění (PDB) program pro požadovaný modul, nebo hodnota null, pokud na soubor .pdb nebyl nalezen.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ProvideModule`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0X80070002)|Nelze najít požadovaný sestavení nebo propojeného prostředku.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId`není dostatečně velký, aby se tak, aby obsahovala identifikátor, který chce vrátit hostitele.|  
  
## <a name="remarks"></a>Poznámky  
 Vrátí hodnotu identity pro `pdwModuleId` je zadán pro hostitele. Identifikátory musí být jedinečný v rámci životnosti procesu. Modul CLR používá tuto hodnotu jako jedinečný identifikátor pro přidružené datového proudu. Zkontroluje s hodnotami pro každou hodnotu `pAssemblyId` vrácený volání [provideassembly –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) a s hodnotami pro `pdwModuleId` vrácený další volání `ProvideModule`. Pokud hostitel vrací stejnou hodnotu, identifikátor pro jinou `IStream`, modul CLR kontroluje, zda jste již namapována obsah tohoto datového proudu. Pokud ano, modulu CLR načte existující kopii místo mapování novou. Proto nesmí identifikátor také překrývat s identifikátory sestavení vrácená z `ProvideAssembly`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
