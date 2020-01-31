---
title: ICorProfilerInfo::GetAssemblyInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
ms.openlocfilehash: 1e08d246136b33ffaaea91367d428e0bf2db99c1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864125"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a>ICorProfilerInfo::GetAssemblyInfo – metoda
Přijímá ID sestavení a vrací název sestavení a ID jeho modulu manifestu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a>Parametry  
 `assemblyId`  
 pro Identifikátor sestavení  
  
 `cchName`  
 pro Délka `szName`znaků.  
  
 `pcchName`  
 mimo Ukazatel na celkovou délku znaku v názvu sestavení.  
  
 `szName`  
 mimo Vyrovnávací paměť pro velký znak poskytnutá volajícímu. Když funkce vrátí, bude obsahovat název sestavení.  
  
 `pAppDomainId`  
 mimo Ukazatel na ID domény aplikace, která obsahuje sestavení.  
  
 `pModuleId`  
 mimo Ukazatel na ID modulu manifestu sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Po návratu této metody je nutné ověřit, zda byla vyrovnávací paměť `szName` dostatečně velká, aby obsahovala úplný název sestavení. To provedete tak, že porovnáte hodnotu, na kterou `pcchName` odkazuje, hodnotou `cchName` parametru. Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší vyrovnávací paměť `szName`, aktualizujte `cchName` novou, větší velikostí a zavolejte `GetAssemblyInfo` znovu.  
  
 Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetAssemblyInfo` s nulovou délkou `szName` vyrovnávací paměti. Velikost vyrovnávací paměti pak můžete upravit na základě hodnoty vrácené v `pcchName` a volat `GetAssemblyInfo` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
