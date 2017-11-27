---
title: "IHostAssemblyStore::ProvideAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore.ProvideAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cda88c2e93b4f90844ad3dec2ed0fa4366dba6d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly – metoda
Získá odkaz na sestavení, které se odkazuje [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , je vrácena z [ihostassemblymanager::getnonhoststoreassemblies –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). Modul CLR (CLR) volá `ProvideAssembly` pro každé sestavení, který se nenachází v seznamu.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pBindInfo`  
 [v] Ukazatel na [assemblybindinfo –](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance, který hostitel používá k určení určité charakteristické vlastnosti vazby, včetně existenci nebo neexistenci těchto všechny zásady správy verzí a které sestavení pro vazbu.  
  
 `pAssemblyId`  
 [out] Ukazatel na jedinečný identifikátor pro požadovaný sestavení pro tento `IStream`.  
  
 `pHostContext`  
 [out] Ukazatel na konkrétním hostiteli data, která se používá k určení důkaz požadovaný sestavení bez nutnosti platformy vyvolat volání. `pHostContext`odpovídá <xref:System.Reflection.Assembly.HostContext%2A> vlastnost spravovaný <xref:System.Reflection.Assembly> třídy.  
  
 `ppStmAssemblyImage`  
 [out] Ukazatel na adresu `IStream` obsahující přenosné spustitelný soubor (PE) obrázek, který má být načten nebo hodnota null, pokud je sestavení nebyl nalezen.  
  
 `ppStmPDB`  
 [out] Ukazatel na adresu `IStream` obsahující informace o ladění (PDB) programu, nebo hodnota null, pokud na soubor .pdb nebyl nalezen.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0X80070002)|Požadovaný sestavení nelze najít.|  
|E_NOT_SUFFICIENT_BUFFER|Zadaná velikost vyrovnávací paměti podle `pAssemblyId` není dostatečně velký pro uložení identifikátor, který chce vrátit hostitele.|  
  
## <a name="remarks"></a>Poznámky  
 Vrátí hodnotu identity pro `pAssemblyId` je zadán pro hostitele. Identifikátory musí být jedinečný v rámci životnosti procesu. Modul CLR používá tuto hodnotu jako jedinečný identifikátor pro datový proud. Zkontroluje s hodnotami pro každou hodnotu `pAssemblyId` vrácený další volání `ProvideAssembly`. Pokud hostitel vrátí stejné `pAssemblyId` hodnotu pro jinou `IStream`, modul CLR kontroluje, zda jste již namapována obsah tohoto datového proudu. Pokud ano, načte modul runtime existující kopii místo mapování novou.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iclrassemblyreferencelist – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Ihostassemblymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [Ihostassemblystore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
