---
title: "ICLRDataTarget3::GetExceptionRecord – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetExceptionRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e78131eda9d10646a881dbbd4e3f7a4aaf8f607
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a>ICLRDataTarget3::GetExceptionRecord – metoda
Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem. Například pro výpis cíl, by to bylo ekvivalentní předaný prostřednictvím záznam výjimka `ExceptionParam` argument [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) funkce v knihovně k Windows ladění pomoci (DbgHelp).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bufferSize`  
 [v] Vstupní vyrovnávací paměť velikost v bajtech. Toto musí být roven `sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.  
  
 `bufferUsed`  
 [out] Ukazatel `ULONG32` typ, který obdrží počet bajtů ve skutečnosti zapsat do vyrovnávací paměti.  
  
 `buffer`  
 [out] Ukazatel na vyrovnávací paměť, která obdrží kopii záznam výjimka. Výjimka záznam se vrátí jako [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) typu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kód při selhání. `HRESULT` Kódy může zahrnovat, avšak nejsou omezeny na následující:  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|`S_OK`|Metoda byla úspěšná. Výjimka záznam byl zkopírován do výstupní vyrovnávací paměť.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Žádný záznam výjimka je přidružený k cíli.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Velikost vstupní vyrovnávací paměť není rovno `sizeof(MINIDUMP_EXCEPTION)`.|  
  
## <a name="remarks"></a>Poznámky  
 [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) je struktura definované v dbghelp.h a imagehlp.h ve Windows SDK.  
  
 Tato metoda je implementována zapisovačem ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRDataTarget3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [GetExceptionContextRecord – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [GetExceptionThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
