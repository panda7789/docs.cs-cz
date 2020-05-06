---
title: ICLRDataTarget3::GetExceptionRecord – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
ms.openlocfilehash: 0ea4546dcde4afa0a9db2e64ae34415d0973391b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860434"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a>ICLRDataTarget3::GetExceptionRecord – metoda
Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem. Například pro cíl výpisu paměti by to byl ekvivalentem záznamu výjimky předaného přes `ExceptionParam` argument do funkce [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) v knihovně dbghelp (ladění v nápovědě systému Windows).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bufferSize`  
 pro Velikost vstupní vyrovnávací paměti (v bajtech). Tato proměnná musí být rovna `sizeof(` [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.  
  
 `bufferUsed`  
 mimo Ukazatel na `ULONG32` typ, který přijímá počet bajtů, které jsou ve skutečnosti zapisovány do vyrovnávací paměti.  
  
 `buffer`  
 mimo Ukazatel na vyrovnávací paměť, která obdrží kopii záznamu výjimky. Záznam výjimky je vrácen jako typ [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) .  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je `S_OK` při úspěchu nebo při selhání kódu chyby `HRESULT` . `HRESULT` Kódy mohou zahrnovat, ale nejsou omezeny na následující:  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|`S_OK`|Metoda byla úspěšná. Záznam výjimky byl zkopírován do výstupní vyrovnávací paměti.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|K cíli není přidružen žádný záznam výjimky.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Velikost vstupní vyrovnávací paměti není rovna `sizeof(MINIDUMP_EXCEPTION)`.|  
  
## <a name="remarks"></a>Poznámky  
 [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) je struktura definovaná v rámci Windows SDK dbghelp. h a Imagehlp. h.  
  
 Tato metoda je implementována modulem pro ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRDataTarget3 – rozhraní](iclrdatatarget3-interface.md)
- [GetExceptionContextRecord – metoda](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [GetExceptionThreadID – metoda](iclrdatatarget3-getexceptionthreadid-method.md)
