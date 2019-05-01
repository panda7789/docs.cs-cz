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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62a8be1e330338043df50bd80576b5aa65447b9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951759"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly – metoda
Získá odkaz na sestavení, které neodkazují [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , který je vrácen z [ihostassemblymanager::getnonhoststoreassemblies –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). Common language runtime (CLR) zavolá `ProvideAssembly` pro každé sestavení, které nejsou uvedené v seznamu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Ukazatel na [assemblybindinfo –](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instanci, kterou hostitel používá k určení určité charakteristické vlastnosti vazby, včetně přítomnosti nebo nepřítomnosti všechny zásady správy verzí a sestavení, které svázat.  
  
 `pAssemblyId`  
 [out] Ukazatel na jedinečný identifikátor pro požadované sestavení pro tento `IStream`.  
  
 `pHostContext`  
 [out] Ukazatel na konkrétního hostitele data, která se používá k určení důkazy požadovaná sestavení bez nutnosti platformu vyvolání volání. `pHostContext` odpovídá <xref:System.Reflection.Assembly.HostContext%2A> vlastnost spravovaného <xref:System.Reflection.Assembly> třídy.  
  
 `ppStmAssemblyImage`  
 [out] Ukazatel na adresu `IStream` , který obsahuje image (PE portable executable) načíst, nebo hodnota null, pokud sestavení nebylo nalezeno.  
  
 `ppStmPDB`  
 [out] Ukazatel na adresu `IStream` , který obsahuje informace o ladění (PDB) programu, nebo hodnota null, pokud soubor PDB nebyl nalezen.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|Požadované sestavení nebyla nalezena.|  
|E_NOT_SUFFICIENT_BUFFER|Velikost vyrovnávací paměti určené `pAssemblyId` není dostatečně velký pro identifikátor, který chce vrátit hostitele.|  
  
## <a name="remarks"></a>Poznámky  
 Vrátí hodnotu identity pro `pAssemblyId` zadaná hostitelem. Identifikátory musí být jedinečné v rámci životního cyklu procesu. Modul CLR používá tuto hodnotu jako jedinečný identifikátor pro datový proud. Zkontroluje každou hodnotu s hodnotami pro `pAssemblyId` vrácený další volání `ProvideAssembly`. Pokud hostitel vrátí stejné `pAssemblyId` hodnota dalších `IStream`, CLR kontroluje, zda již byly namapovány obsah tohoto datového proudu. Pokud ano, načte modul runtime stávající bitovou místo mapování novou kopii.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
