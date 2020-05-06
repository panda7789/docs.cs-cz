---
title: ICLRMetadataLocator::GetMetadata – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
ms.openlocfilehash: ad309290319396ff4e74e30d572effeffe802d1d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859875"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata – metoda
Volá se službami CLR (Common Language Runtime) k načtení metadat obrázku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `imagePath`  
 pro Řetězec, který určuje cestu k souboru obrázku.  
  
 `imageTimestamp`  
 pro Časové razítko souboru obrázku.  
  
 `imageSize`  
 pro Velikost souboru obrázku  
  
 `mvid`  
 pro Globálně jedinečný identifikátor obrázku.  
  
 `mdRva`  
 pro Relativní virtuální adresa (RVA) metadat. Adresa je relativní vzhledem k základní adrese obrázku.  
  
 `flags`  
 pro Vyhrazeno pro budoucí použití.  
  
 `bufferSize`  
 pro Velikost vyrovnávací paměti, do které se mají umístit metadata  
  
 `buffer`  
 mimo Vyrovnávací paměť, do které se mají umístit metadata  
  
 `dataSize`  
 mimo Velikost vrácených metadat.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je implementována modulem pro ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRMetadataLocator – rozhraní](iclrmetadatalocator-interface.md)
