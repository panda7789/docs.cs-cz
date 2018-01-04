---
title: "ICorProfilerInfo::GetCodeInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetCodeInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd05f1ed64e32c4b451f3e60d856be0e99e302b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo – metoda
Získá rozsah nativní kód spojený s ID zadanou funkci.  
  
 Tato metoda je zastaralá. Použití [ICorProfilerInfo2::getcodeinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, ke kterému je přiřazeno nativního kódu.  
  
 `pStart`  
 [out] Ukazatel na pole bajtů, které tvoří nativní kód funkce.  
  
 `pcSize`  
 [out] Ukazatel na celé číslo, které určuje velikost v bajtech nativního kódu.  
  
## <a name="remarks"></a>Poznámky  
 Za účelem optimalizace výkonu modulu runtime v rozhraní .NET Framework verze 2.0 rozdělí kód předkompilovaných, nativní funkce do několika oblastí. V důsledku toho `GetCodeInfo` metoda je zastaralé v rozhraní .NET Framework 2.0, protože se nepodařilo zpracovat rozsah nativního kódu funkce. Profilery musí přejít k používání další Obecné `ICorProfilerInfo2::GetCodeInfo2` metoda místo.  
  
 Tato funkce využívá volající přidělené vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.0  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
