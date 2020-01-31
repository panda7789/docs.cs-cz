---
title: ICorProfilerInfo::GetAppDomainInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 0407b7057753f7fdee6ea6b1d05144b135b6378a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864086"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a>ICorProfilerInfo::GetAppDomainInfo – metoda
Přijímá ID domény aplikace. Vrátí název domény aplikace a ID procesu, který jej obsahuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a>Parametry  
 `appDomainId`  
 pro ID domény aplikace  
  
 `cchName`  
 pro Délka `szName` návratové vyrovnávací paměti ve znacích.  
  
 `pcchName`  
 mimo Ukazatel na celkovou délku znaku názvu domény aplikace.  
  
 `szName`  
 mimo Vyrovnávací paměť pro velký znak poskytnutá volajícímu. Když se metoda vrátí, `szName` bude obsahovat úplný nebo částečný název domény aplikace.  
  
 `pProcessId`  
 mimo Ukazatel na ID procesu, který obsahuje doménu aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Po návratu této metody je nutné ověřit, zda byla vyrovnávací paměť `szName` dostatečně velká, aby obsahovala úplný název domény aplikace. To provedete tak, že porovnáte hodnotu, na kterou `pcchName` odkazuje, hodnotou `cchName` parametru. Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší vyrovnávací paměť `szName`, aktualizujte `cchName` novou, větší velikostí a zavolejte `GetAppDomainInfo` znovu.  
  
 Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetAppDomainInfo` s nulovou délkou `szName` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcchName` a volat `GetAppDomainInfo` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
