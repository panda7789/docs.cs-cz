---
title: "ICorProfilerInfo::SetILInstrumentedCodeMap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetILInstrumentedCodeMap
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 35c87b98a8e0c02ab6f4bca7a4f7a16ff6839c6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap – metoda
Nastaví mapu kódu pro zadanou funkci pomocí zadané položek mapy (MSIL intermediate language) společnosti Microsoft.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 2.0, volání `SetILInstrumentedCodeMap` na `FunctionID` , představuje obecný fungovat v určité domény aplikace bude mít vliv na všechny instance této funkce v doméně aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, pro kterou chcete nastavit Mapa kódu.  
  
 `fStartJit`  
 [v] Logická hodnota, která určuje, zda volání `SetILInstrumentedCodeMap` metoda je první pro konkrétní `FunctionID`. Nastavit `fStartJit` k `true` v prvním volání `SetILInstrumentedCodeMap` pro danou `FunctionID`a `false` po tomto datu.  
  
 `cILMapEntries`  
 [v] Počet elementů ve `cILMapEntries` pole.  
  
 `rgILMapEntries`  
 [v] Pole cor_il_map – struktury, z nichž každý určuje posun MSIL.  
  
## <a name="remarks"></a>Poznámky  
 Profileru často vloží příkazů v rámci zdrojový kód metody za účelem instrumentace dané metody (například upozornit, když je dosaženo zadaná zdrojová řádku). `SetILInstrumentedCodeMap`Umožňuje profileru mapovat původní pokynů MSIL do nového umístění. Můžete použít profileru [icorprofilerinfo::getiltonativemapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metoda získat původní MSIL posunutí pro daný nativní posun.  
  
 Ladicí program bude předpokládat, že každý staré posun odkazuje na MSIL posun v rámci kód MSIL původní, beze změny a že každý nový posun odkazuje na MSIL posun v rámci kód nové, instrumentovaného. Mapy by měly být seřazeny ve vzestupném pořadí. Pro krokování s fungovalo správně, postupujte podle následujících pokynů:  
  
-   Není uspořádat instrumentovaného MSIL kód.  
  
-   Neodebírejte původní MSIL kód.  
  
-   Zahrnete položky pro všechny body sekvence ze souboru databáze (PDB) program v mapě. Mapy není interpolovat položky. Ano danou následující mapa:  
  
     (0 starý, 0 nové)  
  
     (5 starý, 10 nové)  
  
     (9 starý, 20 nové)  
  
    -   Původní posun 0, 1, 2, 3 nebo 4 budou mapována na nový posunu 0.  
  
    -   Původní posun 5, 6, 7 nebo 8 budou mapována na nový posun 10.  
  
    -   Původní posun 9 nebo vyšší budou mapována na nový posun 20.  
  
    -   Nové posun 0, 1, 2, 3, 4, 5, 6, 7, 8 nebo 9 budou mapována na staré posunu 0.  
  
    -   Nové posun 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 budou mapována na staré posun 5.  
  
    -   Nové posun 20 nebo vyšší budou mapována na staré posun 9.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icorprofilerinfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
