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
ms.openlocfilehash: ac35b18ce8c45c95bb2fb8e820423470ca1b75bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497150"
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
 [in, out] Pole struktur [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) , z nichž každá obsahuje tokeny a posuny polí třídy.  
  
 `cFieldOffset`  
 pro Velikost `rFieldOffset` pole.  
  
 `pcFieldOffset`  
 mimo Ukazatel na celkový počet dostupných prvků. Pokud `cFieldOffset` je 0, tato hodnota označuje potřebný počet prvků.  
  
 `pulClassSize`  
 mimo Ukazatel na umístění, které obsahuje velikost (v bajtech) třídy.  
  
## <a name="remarks"></a>Poznámky  
 `GetClassLayout`Metoda vrátí pouze pole, která jsou definována samotný třídou. Pokud má nadřazená třída třídy definována také pole, musí Profiler zavolat `GetClassLayout` na nadřazenou třídu, aby tato pole získala.  
  
 Použijete `GetClassLayout` -li s řetězcovými třídami, metoda se nezdaří s kódem chyby E_INVALIDARG. K získání informací o rozložení řetězce použijte [ICorProfilerInfo2:: GetStringLayout –](icorprofilerinfo2-getstringlayout-method.md) . `GetClassLayout`selže také při volání s třídou Array.  
  
 Po `GetClassLayout` návratu je nutné ověřit, zda `rFieldOffset` byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny dostupné `COR_FIELD_OFFSET` struktury. Chcete-li to provést, porovnejte hodnotu, na kterou odkazuje, na `pcFieldOffset` Velikost `rFieldOffset` dělené velikostí `COR_FIELD_OFFSET` struktury. Pokud `rFieldOffset` není dostatečně velká, přidělte větší `rFieldOffset` vyrovnávací paměť, aktualizujte `cFieldOffset` novou, větší velikost a zavolejte `GetClassLayout` znovu.  
  
 Případně můžete `GetClassLayout` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `rFieldOffset` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti na hodnotu vrácenou v `pcFieldOffset` a volat `GetClassLayout` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
