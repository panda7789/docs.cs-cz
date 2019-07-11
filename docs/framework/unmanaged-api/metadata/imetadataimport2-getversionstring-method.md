---
title: IMetaDataImport2::GetVersionString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d500584afd608f79e41e932be259d29ae51db2db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781574"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString – metoda
Získá číslo verze modulu runtime, která byla použita k vytvoření sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzBuf`  
 [out] Pole pro uložení řetězce, který určuje verzi.  
  
 `ccBufSize`  
 [in] Velikost v širokých znaků, z `pwzBuf` pole.  
  
 `pccBufSize`  
 [out] Vrátí počet širokých znaků, včetně null zakončení, v `pwzBuf` pole.  
  
## <a name="remarks"></a>Poznámky  
 `GetVersionString` Metoda získá vytvořené pro verzi aktuální obor metadat. Pokud obor nebyl uložen, nebude mít vytvořené pro verzi a bude vrácen prázdný řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
