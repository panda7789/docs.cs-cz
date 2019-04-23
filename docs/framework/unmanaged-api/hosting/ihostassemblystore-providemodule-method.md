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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e07e2c3f2c6000f5a081b13316c269f322b1ef8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078335"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule – metoda
Přeloží do souboru prostředků modulu v sestavení nebo propojená (ale nikoli vložené).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBindInfo`  
 [in] Ukazatel [modulebindinfo –](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instanci, která popisuje požadovaný modul <xref:System.AppDomain>, sestavení a název modulu.  
  
 `pdwModuleId`  
 [out] Ukazatel na jedinečný identifikátor `IStream` obsahující načteného modulu.  
  
 `ppStmModuleImage`  
 [out] Ukazatel na adresu `IStream` objekt, který obsahuje image (PE portable executable) mají být načteny, nebo hodnota null, pokud modul nebyl nalezen.  
  
 `ppStmPDB`  
 [out] Ukazatel na adresu `IStream` objekt, který obsahuje informace o ladění (PDB) programu požadované pro modul, nebo hodnota null, pokud soubor PDB nebyl nalezen.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ProvideModule` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|Požadované sestavení nebo propojeného prostředku nebyla nalezena.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` není dostatečně velký, aby obsahovat identifikátor, který chce vrátit hostitele.|  
  
## <a name="remarks"></a>Poznámky  
 Vrátí hodnotu identity pro `pdwModuleId` zadaná hostitelem. Identifikátory musí být jedinečné v rámci životního cyklu procesu. Modul CLR používá tuto hodnotu jako jedinečný identifikátor pro přidružené datového proudu. Zkontroluje každou hodnotu s hodnotami pro `pAssemblyId` vrácený volání [provideassembly –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) a s hodnotami pro `pdwModuleId` vrácený další volání `ProvideModule`. Pokud hostitel vrátí stejnou hodnotu identifikátoru dalších `IStream`, CLR kontroluje, zda již byly namapovány obsah tohoto datového proudu. Pokud ano, načte modul CLR stávající bitovou místo mapování novou kopii. Proto nesmí identifikátor také překrývat s identifikátory sestavení vrácená `ProvideAssembly`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
