---
title: ICLRDataTarget3::GetExceptionContextRecord – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
ms.openlocfilehash: aed301fa136ff3d45269c82b46e4cad699074874
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785239"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::GetExceptionContextRecord – metoda
Volá se službami CLR (Common Language Runtime) k načtení záznamu kontextu přidruženého k cílovému procesu. Například pro cíl výpisu paměti by to byl ekvivalentem záznamu kontextu předaného pomocí argumentu `ExceptionParam` do funkce [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) v knihovně dbghelp (Windows ladění Help Library).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bufferSize`  
 pro Velikost vstupní vyrovnávací paměti (v bajtech). Tento postup musí být dostatečně velký, aby mohl být přizpůsoben záznamu kontextu.  
  
 `bufferUsed`  
 mimo Ukazatel na typ `ULONG32`, který přijímá počet bajtů, které jsou ve skutečnosti zapisovány do vyrovnávací paměti.  
  
 `buffer`  
 mimo Ukazatel na vyrovnávací paměť, která obdrží kopii záznamu kontextu. Záznam výjimky je vrácen jako typ [kontextu](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je `S_OK` při úspěchu nebo selhání `HRESULT` kódu při selhání. Kódy `HRESULT` mohou zahrnovat, ale nejsou omezeny na následující:  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|`S_OK`|Metoda byla úspěšná. Záznam kontextu byl zkopírován do výstupní vyrovnávací paměti.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|K cíli není přidružen žádný záznam kontextu.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|Velikost vstupní vyrovnávací paměti není dostatečně velká pro přizpůsobení záznamu kontextu.|  
  
## <a name="remarks"></a>Poznámky  
 [Kontext](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) je struktura specifická pro platformu definovaná v hlavičkách poskytnutých Windows SDK.  
  
 Tato metoda je implementována modulem pro ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget3 – rozhraní](iclrdatatarget3-interface.md)
- [GetExceptionRecord – metoda](iclrdatatarget3-getexceptionrecord-method.md)
- [GetExceptionThreadID – metoda](iclrdatatarget3-getexceptionthreadid-method.md)
