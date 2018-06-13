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
ms.openlocfilehash: 112ddcf51a5637bb89df9479850c2a4a70d2e1d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448723"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString – metoda
Získá číslo verze modulu runtime, který byl použit k vytvoření sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzBuf`  
 [out] Pole pro uložení řetězec, který určuje verzi.  
  
 `ccBufSize`  
 [v] Velikost v široké znaky z `pwzBuf` pole.  
  
 `pccBufSize`  
 [out] Počet široké znaky, včetně zakončením hodnotu null, vrátí se v `pwzBuf` pole.  
  
## <a name="remarks"></a>Poznámky  
 `GetVersionString` Metoda získá vytvořené pro verzi aktuální obor metadat. Pokud ještě nebyla uložena oboru, nebude mít vytvořené pro verzi a vrátí prázdný řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
