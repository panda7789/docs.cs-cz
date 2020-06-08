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
ms.openlocfilehash: 5e5510ec098b2c1aa3b768830b812328287fd31a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503026"
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
 Po návratu této metody je nutné ověřit, zda `szName` byla vyrovnávací paměť dostatečně velká, aby obsahovala úplný název domény aplikace. Provedete to tak, že porovnáte hodnotu, `pcchName` na kterou odkazuje, s hodnotou `cchName` parametru. Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName` , přidělte větší `szName` vyrovnávací paměť, aktualizujte `cchName` novou, větší velikost a zavolejte `GetAppDomainInfo` znovu.  
  
 Případně můžete `GetAppDomainInfo` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `szName` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcchName` a volat `GetAppDomainInfo` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
