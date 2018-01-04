---
title: "ICorProfilerInfo2::GetStringLayout – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetStringLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ad91829fab31b47a1dd51bb6cc9118c2ebe4c3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout – metoda
Získá informace o rozložení objektu řetězce. Tato metoda je zastaralá ve [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]a je nahrazena [icorprofilerinfo3::getstringlayout2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBufferLengthOffset`  
 [out] Ukazatel na posun umístění relativně k `ObjectID` ukazatele, který ukládá délka řetězce. Délka se ukládají jako `DWORD`.  
  
> [!NOTE]
>  Tento parametr vrátí délku řetězce samostatně, není délka vyrovnávací paměti. Délka vyrovnávací paměti je již k dispozici.  
  
 `PStringLengthOffset`  
 [out] Ukazatel na posun umístění relativně k `ObjectID` ukazatele, uchovávající délky řetězce sám sebe. Délka se ukládají jako `DWORD`.  
  
 `pBufferOffset`  
 [out] Ukazatel na posun vyrovnávací paměti, relativně k `ObjectID` ukazatele, který ukládá řetězec široké znaky.  
  
## <a name="remarks"></a>Poznámky  
 `GetStringLayout` Metoda získá posun, vzhledem k `ObjectID` ukazatele, umístění, ve kterých se ukládají následující:  
  
-   Délka vyrovnávací paměti řetězec.  
  
-   Délka řetězce sám sebe.  
  
-   Vyrovnávací paměť, která obsahuje konkrétní řetězec široké znaky.  
  
 Řetězce může být ukončené hodnotou null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
