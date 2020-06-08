---
title: IMethodMalloc::Alloc – metoda
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: a82a2150f32b1b335da083ca235ed9d2966a0b6e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494199"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc – metoda

Pokusí se přidělit určenou velikost paměti pro nové tělo funkce jazyka MSIL (Microsoft Intermediate Language).

## <a name="syntax"></a>Syntaxe

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>Parametry

`cb`\
pro Počet bajtů, které se mají přidělit pro tělo metody

## <a name="remarks"></a>Poznámky

 Přidělená paměť začne na adrese větší než základní adresa modulu, který je přidružen k tomuto přidělování. Jinými slovy, každý Alokátor se vytvoří pro určitý modul a pokusí se přidělit paměť s kladným posunem od základní adresy. Pokud `Alloc` se nepovede přidělit požadovaný počet bajtů v adrese, která je větší než základní adresa modulu, vrátí E_OUTOFMEMORY, a to bez ohledu na skutečnou velikost dostupného místa v paměti.

 `Alloc`Metoda by měla být použita ve spojení s metodou [ICorProfilerInfo:: SetILFunctionBody –](icorprofilerinfo-setilfunctionbody-method.md) .

## <a name="requirements"></a>Požadavky
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Hlavička:** CorProf. idl, CorProf. h

 **Knihovna:** CorGuids. lib

 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [IMethodMalloc – rozhraní](imethodmalloc-interface.md)
