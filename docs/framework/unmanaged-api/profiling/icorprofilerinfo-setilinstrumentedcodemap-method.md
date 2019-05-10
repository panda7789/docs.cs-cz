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
ms.openlocfilehash: 1ec0f986efe24b0b69df9d2ecd93335f7ac5db28
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606638"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap – metoda
Nastaví mapu kódu pro zadanou funkci pomocí zadané položky mapování Microsoft intermediate language (MSIL).  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 2.0, volání `SetILInstrumentedCodeMap` na `FunctionID` , představuje obecnou funkci v určité domény aplikace bude mít vliv na všechny instance této funkce v doméně aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] ID funkce, pro kterou chcete nastavit mapu kódu.  
  
 `fStartJit`  
 [in] Logická hodnota, která určuje, zda volání `SetILInstrumentedCodeMap` metody je první pro konkrétní `FunctionID`. Nastavit `fStartJit` k `true` v prvním volání `SetILInstrumentedCodeMap` pro dané `FunctionID`a získat `false` po tomto datu.  
  
 `cILMapEntries`  
 [in] Počet prvků v `cILMapEntries` pole.  
  
 `rgILMapEntries`  
 [in] Pole struktur cor_il_map –, z nichž každý Určuje prodlevu jazyka MSIL.  
  
## <a name="remarks"></a>Poznámky  
 Profiler často vloží příkazy ve zdrojovém kódu metody k instrumentaci metody (například upozornit, když je dosaženo dané zdrojový řádek). `SetILInstrumentedCodeMap` Umožňuje profileru mapování původní instrukce jazyka MSIL do nového umístění. Profiler může použít [icorprofilerinfo::getiltonativemapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metodu k získání původní posun jazyka MSIL pro danou nativní posun.  
  
 Ladicí program bude předpokládat, že každý staré posun odkazuje na jazyka MSIL posun v rámci původní verzí bez úprav kódu MSIL a, že každý nový posun odkazuje na MSIL posun v rámci nové instrumentované kódu. Na mapě by měly být seřazeny vzestupně v pořadí. Pro krokování fungovalo správně, postupujte podle následujících pokynů:  
  
- Nemění pořadí instrumentované kód jazyka MSIL.  
  
- Neodebírejte původní kód jazyka MSIL.  
  
- Zahrnete položky pro všechny body posloupnosti ze souboru databáze (PDB) programu na mapě. Mapa není interpolovat chybějící položky. Ano uvedené následující mapování:  
  
     (0 staré, 0 nové)  
  
     (5 staré, 10 nové)  
  
     (9 staré, 20 nové)  
  
    - Staré posun 0, 1, 2, 3 nebo 4 se namapují na nové posun 0.  
  
    - Posun staré 5, 6, 7 nebo 8 se namapují na nové posun 10.  
  
    - Staré posun 9 nebo vyšší se namapují na nové posun 20.  
  
    - Nové posun 0, 1, 2, 3, 4, 5, 6, 7, 8 a 9 se namapují na staré posun 0.  
  
    - Nové posun 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 se namapují na staré posun 5.  
  
    - Nové posun 20 nebo vyšší se namapují na staré posun 9.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
