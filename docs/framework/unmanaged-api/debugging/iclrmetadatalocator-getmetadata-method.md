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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74a54da0bc4257ccc50d2d99177a17b796380fb3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481427"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata – metoda
Volá se službami common language runtime (CLR) přístup k datům pro načtení metadat bitovou kopii.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Řetězec, který určuje cestu k souboru bitové kopie.  
  
 `imageTimestamp`  
 [in] Časové razítko souboru bitové kopie.  
  
 `imageSize`  
 [in] Velikost souboru obrázku.  
  
 `mvid`  
 [in] Globálně jedinečný identifikátor používaného obrázku.  
  
 `mdRva`  
 [in] Relativní virtuální adresu (RVA) metadat. Adresa je relativní vzhledem k základní adrese image.  
  
 `flags`  
 [in] Vyhrazeno pro budoucí použití.  
  
 `bufferSize`  
 [in] Velikost vyrovnávací paměti, do které se má umístit metadata.  
  
 `buffer`  
 [out] Vyrovnávací paměť, ve které chcete umístit metadata.  
  
 `dataSize`  
 [out] Velikost metadat, která je vrácena.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je implementováno tvůrci ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRMetadataLocator – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
