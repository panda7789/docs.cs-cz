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
ms.openlocfilehash: e3d167be9a4091ae57a3283424186142e90ca7a1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868548"
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
 mimo ID zástupce běžící instance CLR v procesu. To je totéž jako `ClrInstanceID`, které sestavy událostí při spuštění trasování událostí pro Windows (ETW).  
  
 `pRuntimeType`  
 mimo Typ modulu runtime. Tento parametr vrátí `COR_PRF_DESKTOP_CLR` verze modulu CLR pro plochu nebo `COR_PRF_CORE_CLR` základní verzi CLR použitou v programu Silverlight.  
  
 `pMajorVersion`  
 mimo Hlavní číslo verze modulu CLR.  
  
 `pMinorVersion`  
 mimo Číslo dílčí verze modulu CLR.  
  
 `pBuildVersion`  
 mimo Číslo verze buildu modulu CLR.  
  
 `pQFEVersion`  
 mimo Číslo verze modulu CLR, který je spojen s aktualizací softwaru.  
  
 `cchVersionString`  
 pro Délka vyrovnávací paměti v znacích, na kterou `szVersionString` odkazuje.  
  
 `pcchVersionString`  
 mimo Délka `szVersionString`znaků.  
  
 `szVersionString`  
 mimo Řetězec verze CLR.  
  
## <a name="remarks"></a>Poznámky  
 Pro libovolný parametr můžete předat hodnotu null. `pcchVersionString` však nesmí mít hodnotu null, pokud `szVersionString` není také null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
