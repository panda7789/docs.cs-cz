---
title: ICorProfilerInfo::SetILInstrumentedCodeMap – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65eee2e834251817b461f1cd1debf212696d5a5f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855691"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap – metoda

Nastaví mapu kódu pro určenou funkci pomocí zadaných položek mapování jazyka MSIL (Microsoft Intermediate Language).

> [!NOTE]
> V .NET Framework verze 2,0 bude volání `SetILInstrumentedCodeMap` `FunctionID` na, které představuje obecnou funkci v konkrétní doméně aplikace, ovlivnit všechny instance této funkce v doméně aplikace.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a>Parametry

`functionId`\
pro ID funkce, pro kterou chcete nastavit mapu kódu.

`fStartJit`\
pro Logická hodnota, která označuje, zda je volání `SetILInstrumentedCodeMap` metody prvním pro konkrétní. `FunctionID` Nastavte `fStartJit` `SetILInstrumentedCodeMap` na `true` při prvním volání na pro daný `FunctionID`a potom na `false` .

`cILMapEntries`\
pro Počet prvků v `cILMapEntries` poli.

`rgILMapEntries`\
pro Pole struktur COR_IL_MAP, z nichž každý Určuje posun MSIL.

## <a name="remarks"></a>Poznámky

Profiler často vkládá příkazy v rámci zdrojového kódu metody pro instrumentaci této metody (například pro oznámení, když je dosaženo daného řádku zdroje). `SetILInstrumentedCodeMap`umožňuje profileru mapovat původní instrukce jazyka MSIL na jejich nová umístění. Profiler může pomocí metody [ICorProfilerInfo:: GetILToNativeMapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) získat původní posun MSIL pro daný nativní posun.

Ladicí program předpokládá, že každý starý posun odkazuje na posun MSIL v rámci původního, neupraveného kódu MSIL a že každý nový posun odkazuje na posun MSIL v rámci nového, instrumentované kódu. Mapa by se měla seřadit ve vzestupném pořadí. Chcete-li, aby krokování fungovalo správně, postupujte podle těchto pokynů:

- Neměňte pořadí načítacího kódu MSIL.

- Neodstraňujte původní kód MSIL.

- Zahrnout položky pro všechny body sekvence ze souboru databáze programu (PDB) na mapě. Mapa neinterpoluje chybějící položky. Proto s ohledem na následující mapu:

  (0 Old, 0 novinek)

  (5 Old, 10 nových)

  (9 Old, 20 novinek)

  - Starý posun 0, 1, 2, 3 nebo 4 se namapuje na nový posun 0.

  - Starý posun z 5, 6, 7 nebo 8 se namapuje na nový posun 10.

  - Původní posun 9 nebo vyšší se namapuje na nový posun 20.

  - Nové odsazení 0, 1, 2, 3, 4, 5, 6, 7, 8 nebo 9 bude namapováno na starý posun 0.

  - Nové posuny 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 budou namapovány na starý posun 5.

  - Nový posun o hodnotě 20 nebo vyšší bude mapován na starý posun 9.

V .NET Framework 3,5 a předchozích verzích přidělíte `rgILMapEntries` pole voláním metody [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) . Vzhledem k tomu, že modul runtime převezme vlastnictví této paměti, Profiler by se neměl pokoušet o uvolnění.

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlaviček** CorProf.idl, CorProf.h

**Knihovna** CorGuids.lib

**Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
