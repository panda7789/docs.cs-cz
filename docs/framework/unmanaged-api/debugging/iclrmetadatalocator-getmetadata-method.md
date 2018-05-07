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
ms.openlocfilehash: 4338619414c9c9ac8c5fe85479562410d1678698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata – metoda
Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup pro načtení metadat bitové kopie.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `imagePath`  
 [v] Řetězec, který určuje cestu k souboru bitové kopie.  
  
 `imageTimestamp`  
 [v] Časové razítko souboru bitové kopie.  
  
 `imageSize`  
 [v] Velikost souboru bitové kopie.  
  
 `mvid`  
 [v] Globálně jedinečný identifikátor bitové kopie.  
  
 `mdRva`  
 [v] Relativní virtuální adresy (RVA) metadata. Adresa je relativní vzhledem k základní adresu bitové kopie.  
  
 `flags`  
 [v] Vyhrazeno pro budoucí použití.  
  
 `bufferSize`  
 [v] Velikost vyrovnávací paměti, do níž umístíte metadata.  
  
 `buffer`  
 [out] Vyrovnávací paměť, do níž umístíte metadata.  
  
 `dataSize`  
 [out] Velikost metadat, která je vrácena.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je implementována zapisovačem ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRMetadataLocator – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
