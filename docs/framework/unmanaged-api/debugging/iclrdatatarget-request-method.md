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
ms.openlocfilehash: dc79277c75118b11766e66137284bd5655eed091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request – metoda
Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup požádat o operaci podle definice implementace.  
  
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
 [v] Uživatelem definované.  
  
 `inBufferSize`  
 [v] Velikost vstupní vyrovnávací paměť, která se používá k příchozího požadavku.  
  
 `inBuffer`  
 [v] Vyrovnávací paměť obsahující žádosti.  
  
 `outBufferSize`  
 [v] Velikost výstupní vyrovnávací paměť, která se používá k odpovědi.  
  
 `outBuffer`  
 [out] Vyrovnávací paměť s odpovědí.  
  
## <a name="remarks"></a>Poznámky  
 `Request` Metoda usnadňuje přidání neurčené vlastní operace. To znamená tato metoda zajišťuje rozšiřitelnost bez nutnosti revizi definice rozhraní.  
  
 Tato metoda je implementována zapisovačem ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
