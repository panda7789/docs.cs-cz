---
title: ICorProfilerInfo3::GetRuntimeInformation – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: b8e503af11fa1d02aac2ec83edde0ffbd562d8e5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496396"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation – metoda
Poskytuje informace o verzi modulu CLR (Common Language Runtime), který je profilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `pClrInstanceId`  
 mimo ID zástupce běžící instance CLR v procesu. To je stejné jako u `ClrInstanceID` sestav událostí spuštění trasování událostí pro Windows (ETW).  
  
 `pRuntimeType`  
 mimo Typ modulu runtime. Tento parametr vrátí hodnotu `COR_PRF_DESKTOP_CLR` pro desktopovou verzi CLR nebo `COR_PRF_CORE_CLR` základní verzi CLR použitou v programu Silverlight.  
  
 `pMajorVersion`  
 mimo Hlavní číslo verze modulu CLR.  
  
 `pMinorVersion`  
 mimo Číslo dílčí verze modulu CLR.  
  
 `pBuildVersion`  
 mimo Číslo verze buildu modulu CLR.  
  
 `pQFEVersion`  
 mimo Číslo verze modulu CLR, který je spojen s aktualizací softwaru.  
  
 `cchVersionString`  
 pro Délka vyrovnávací paměti v znacích, `szVersionString` na kterou odkazuje.  
  
 `pcchVersionString`  
 mimo Délka v znacích `szVersionString` .  
  
 `szVersionString`  
 mimo Řetězec verze CLR.  
  
## <a name="remarks"></a>Poznámky  
 Pro libovolný parametr můžete předat hodnotu null. Nicméně `pcchVersionString` nemůže mít hodnotu null, pokud `szVersionString` není také null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
