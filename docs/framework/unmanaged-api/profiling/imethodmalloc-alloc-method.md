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
ms.openlocfilehash: af881d23ff77f05dadbbc745b973979e35ebe9f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447565"
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

 Přidělená paměť začne na adrese větší než základní adresa modulu, který je přidružen k tomuto přidělování. Jinými slovy, každý Alokátor se vytvoří pro určitý modul a pokusí se přidělit paměť s kladným posunem od základní adresy. Pokud se `Alloc` nedokáže přidělit požadovaný počet bajtů na adrese větší než základní adresa modulu, vrátí E_OUTOFMEMORY, a to bez ohledu na skutečnou velikost dostupného místa v paměti.

 Metoda `Alloc` by měla být použita ve spojení s metodou [ICorProfilerInfo:: SetILFunctionBody –](icorprofilerinfo-setilfunctionbody-method.md) .

## <a name="requirements"></a>Požadavky
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

 **Hlavička:** CorProf. idl, CorProf. h

 **Knihovna:** CorGuids. lib

 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [IMethodMalloc – rozhraní](imethodmalloc-interface.md)
