---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d669ae15c01a560f2cefb6e361ca32411652fbc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732970"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a>ISymUnmanagedWriter4::GetDebugInfoWithPadding – metoda
Funguje stejně jako [GetDebugInfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) s tím rozdílem, že řetězec cesty doplněno nulami po ukončujícího znaku null na pevnou velikost, aby se data řetězce `MAX_PATH`. Odsazení je uveden pouze pokud je délka řetězec cesty, samotný menší než `MAX_PATH`.  
  
 Díky tomu je snazší psát nástroje tento rozdíl PE soubory.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedWriter4 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
