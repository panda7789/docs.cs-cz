---
title: "IMetaDataImport2::GetVersionString – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetVersionString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccf168473c1182e4b7d57d52930d90084eaa2dd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
