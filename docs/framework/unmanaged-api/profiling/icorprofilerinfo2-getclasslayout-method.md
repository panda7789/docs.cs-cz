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
ms.openlocfilehash: 37400e3b69b3884e31479fd7cdfccb473408bfbf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433389"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout – metoda
Načte informace o rozložení v paměti polí definovaných specifikovanou třídou. To znamená, že tato metoda získá posuny polí třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `classID`  
 pro ID třídy, pro kterou bude rozložení načteno.  
  
 `rFieldOffset`  
 [in, out] Pole struktur [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) , z nichž každá obsahuje tokeny a posuny polí třídy.  
  
 `cFieldOffset`  
 pro Velikost pole `rFieldOffset`.  
  
 `pcFieldOffset`  
 mimo Ukazatel na celkový počet dostupných prvků. Pokud je `cFieldOffset` 0, tato hodnota označuje potřebný počet prvků.  
  
 `pulClassSize`  
 mimo Ukazatel na umístění, které obsahuje velikost (v bajtech) třídy.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetClassLayout` vrátí pouze pole, která jsou definována samotný třídou. Pokud má nadřazená třída třídy definována také pole, musí Profiler volat `GetClassLayout` v nadřazené třídě, aby tato pole získal.  
  
 Použijete-li `GetClassLayout` s řetězcovými třídami, metoda bude neúspěšná s kódem chyby E_INVALIDARG. K získání informací o rozložení řetězce použijte [ICorProfilerInfo2:: GetStringLayout –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) . `GetClassLayout` také selže při volání s třídou Array.  
  
 Jakmile `GetClassLayout` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `rFieldOffset` dostatečně velká, aby obsahovala všechny dostupné `COR_FIELD_OFFSET` struktury. Provedete to tak, že porovnáte hodnotu, na kterou `pcFieldOffset` odkazuje, na velikost `rFieldOffset` dělenou velikostí `COR_FIELD_OFFSET` struktury. Pokud `rFieldOffset` není dostatečně velká, přidělte větší vyrovnávací paměť `rFieldOffset`, aktualizujte `cFieldOffset` o novou, větší velikost a zavolejte `GetClassLayout` znovu.  
  
 Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetClassLayout` s nulovou délkou `rFieldOffset` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcFieldOffset` a volat `GetClassLayout` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
