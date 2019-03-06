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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a676989bdc6866f85fabe3e15b1e6b7b8b5a9a9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351252"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc – metoda

Pokusí se přidělit zadanou velikost paměti pro nové tělo funkce Microsoft intermediate language (MSIL).

## <a name="syntax"></a>Syntaxe

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>Parametry

`cb`\
[in] Počet bajtů k přidělení pro tělo metody.

## <a name="remarks"></a>Poznámky

 Přidělená paměť se začne na adrese větší než základní adresy modulu, který je přidružený k této alokátoru. Jinými slovy každý alokátoru pro konkrétního modulu se vytvoří a se pokusí o přidělení paměti na kladné posunu od jeho základní adresa. Pokud `Alloc` se nepodařilo přidělit požadovaný počet bajtů na adrese větší než základní adresy modulu, vrátí E_OUTOFMEMORY, bez ohledu na skutečné množství paměti k dispozici.

 `Alloc` Metoda byste měli použít ve spojení s [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) metody.

## <a name="requirements"></a>Požadavky
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

 **Záhlaví:** CorProf.idl, CorProf.h

 **Knihovna:** CorGuids.lib

 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [IMethodMalloc – rozhraní](imethodmalloc-interface.md)