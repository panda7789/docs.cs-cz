---
title: ICorProfilerInfo2::GetClassLayout – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b826e9c30fbf7007ac6b0093608ab7d926cc499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459150"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout – metoda
Získá informace o rozložení, v paměti pro pole definovaná v zadané třídě. To znamená tato metoda získá posun třída polí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 `classID`  
 [v] ID třídy, pro kterou bude načten rozložení.  
  
 `rFieldOffset`  
 [ve out] Pole [cor_field_offset –](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z nichž každý obsahuje tokenů a posuny polí třídu.  
  
 `cFieldOffset`  
 [v] Velikost `rFieldOffset` pole.  
  
 `pcFieldOffset`  
 [out] Ukazatel na celkový počet elementů k dispozici. Pokud `cFieldOffset` je 0, tato hodnota označuje počet elementů potřeby.  
  
 `pulClassSize`  
 [out] Ukazatel na umístění, které obsahuje velikost v bajtech třídy.  
  
## <a name="remarks"></a>Poznámky  
 `GetClassLayout` Metoda vrátí pouze pole definované vlastní třídy. Pokud třída nadřazené třídy, který definuje také pole, musí volat profileru `GetClassLayout` na nadřazené třídy k získání těchto polí.  
  
 Pokud používáte `GetClassLayout` s třídami řetězce, metoda selže s kódem chyby E_INVALIDARG. Použití [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) se získat informace o rozložení řetězce. `GetClassLayout` selžou i při volání s třídu pole.  
  
 Po `GetClassLayout` vrátí, musíte ověřit, že `rFieldOffset` vyrovnávací paměť byla dostatečně velký, aby se tak, aby obsahovala všechny dostupné `COR_FIELD_OFFSET` struktury. K tomuto účelu porovnat hodnotu, `pcFieldOffset` body s velikostí `rFieldOffset` dělený velikost `COR_FIELD_OFFSET` struktury. Pokud `rFieldOffset` není velký, přidělit větší `rFieldOffset` vyrovnávací paměti, aktualizujte `cFieldOffset` s novou, větší velikost a volání `GetClassLayout` znovu.  
  
 Alternativně můžete nejdřív volat `GetClassLayout` s nulovou délkou `rFieldOffset` vyrovnávací paměti se získat velikost správné vyrovnávací paměti. Velikost vyrovnávací paměti pak můžete nastavit na hodnotu, vrátí se v `pcFieldOffset` a volání `GetClassLayout` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
