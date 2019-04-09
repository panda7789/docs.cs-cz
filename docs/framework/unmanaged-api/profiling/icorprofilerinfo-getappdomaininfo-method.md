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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83468e13e1e028b031c31791910c4dd2d792f232
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168763"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a>ICorProfilerInfo::GetAppDomainInfo – metoda
Přijímá identifikátor domény aplikace. Vrátí název domény aplikace a ID procesu, který jej obsahuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] ID domény aplikace.  
  
 `cchName`  
 [in] Délka ve znacích, nástroje `szName` návratové vyrovnávací paměti.  
  
 `pcchName`  
 [out] Ukazatel na celkový počet znaků názvu domény aplikace.  
  
 `szName`  
 [out] Pokud volající širokého znaku vyrovnávací paměti. Po návratu metody `szName` bude obsahovat název domény aplikace celé nebo jeho část.  
  
 `pProcessId`  
 [out] Ukazatel na ID procesu, která obsahuje doménu aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Po návratu tato metoda je nutné ověřit, `szName` vyrovnávací paměť je dostatečně velký, aby obsahovat úplný název domény aplikace. K tomuto účelu porovnat hodnoty, které `pcchName` odkazuje na hodnotu `cchName` parametru. Pokud `pcchName` odkazuje na hodnotu, která je větší než `cchName`, přidělte větší `szName` vyrovnávací paměti, aktualizujte `cchName` nové, větší velikosti a volání `GetAppDomainInfo` znovu.  
  
 Alternativně můžete nejprve volat `GetAppDomainInfo` s nulovou délkou `szName` vyrovnávací paměť pro získání správné vyrovnávací paměť. Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcchName` a volat `GetAppDomainInfo` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
