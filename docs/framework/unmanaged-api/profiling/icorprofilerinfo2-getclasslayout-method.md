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
ms.openlocfilehash: 0ccc36231a2a554e523dbbef67996b7ad220cf2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602465"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout – metoda
Získá informace o rozvržení, v paměti, pole definovaná pomocí dané třídy. To znamená tato metoda načte posuny polí třídy.  
  
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
 [in] ID třídy, pro kterou budou načteny rozložení.  
  
 `rFieldOffset`  
 [out v] Pole [cor_field_offset –](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z nichž každý obsahuje tokeny a posuny polí třídy.  
  
 `cFieldOffset`  
 [in] Velikost `rFieldOffset` pole.  
  
 `pcFieldOffset`  
 [out] Ukazatel na celkový počet elementů k dispozici. Pokud `cFieldOffset` je 0, tato hodnota označuje počet prvků, které jsou potřeba.  
  
 `pulClassSize`  
 [out] Ukazatel na umístění, které obsahuje velikost v bajtech třídy.  
  
## <a name="remarks"></a>Poznámky  
 `GetClassLayout` Metoda vrátí pouze pole definovaná pomocí vlastní třídy. Pokud nadřazená třída třídy definoval také pole, musí volat profiler `GetClassLayout` na nadřazené třídu k získání těchto polí.  
  
 Pokud používáte `GetClassLayout` s třídami řetězce, metoda selže s kódem chyby E_INVALIDARG. Použití [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) a získat informace o rozložení řetězce. `GetClassLayout` také selže při volání s třídou pole.  
  
 Po `GetClassLayout` vrátí, musíte ověřit, že `rFieldOffset` vyrovnávací paměť je dostatečně velký, aby obsahovala všechny dostupné `COR_FIELD_OFFSET` struktury. K tomuto účelu porovnat hodnoty, které `pcFieldOffset` odkazuje na s velikostí `rFieldOffset` rozdělené podle velikosti `COR_FIELD_OFFSET` struktury. Pokud `rFieldOffset` není velký, přidělte větší `rFieldOffset` vyrovnávací paměti, aktualizujte `cFieldOffset` nové, větší velikosti a volání `GetClassLayout` znovu.  
  
 Alternativně můžete nejprve volat `GetClassLayout` s nulovou délkou `rFieldOffset` vyrovnávací paměť pro získání správné vyrovnávací paměť. Pak můžete nastavit velikost vyrovnávací paměti pro hodnotu vrácenou v `pcFieldOffset` a volat `GetClassLayout` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
