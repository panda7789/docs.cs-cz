---
title: ICLRDataTarget::Request – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77bd3bc239d0101f02cd515b0ec2a8bec3372882
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596901"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request – metoda
Voláno rozhraním common language runtime (CLR) data access services požádat o operaci, jak je definováno implementací.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `reqCode`  
 [in] Uživatelem definované.  
  
 `inBufferSize`  
 [in] Velikost vstupní vyrovnávací paměti, který se používá pro tento požadavek.  
  
 `inBuffer`  
 [in] Vyrovnávací paměť obsahující žádost.  
  
 `outBufferSize`  
 [in] Velikost výstupní vyrovnávací paměť, která se používá pro odpověď.  
  
 `outBuffer`  
 [out] Vyrovnávací paměť s odpovědí.  
  
## <a name="remarks"></a>Poznámky  
 `Request` Metoda usnadňuje přidávání neurčené vlastní operace. To znamená, že tato metoda poskytuje rozšiřitelnost bez nutnosti revize definici rozhraní.  
  
 Tato metoda je implementováno tvůrci ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
