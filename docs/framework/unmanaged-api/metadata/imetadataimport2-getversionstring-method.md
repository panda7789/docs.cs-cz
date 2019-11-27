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
ms.openlocfilehash: 0c9f667edf30feb23e1cdaa28950503283fce42e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445222"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString – metoda
Získá číslo verze modulu runtime, který byl použit k sestavení sestavení.  
  
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
 mimo Pole pro uložení řetězce, který určuje verzi.  
  
 `ccBufSize`  
 pro Velikost pole `pwzBuf` v různých znacích  
  
 `pccBufSize`  
 mimo Počet velkých znaků, včetně ukončovacího znaku null, vrácený v poli `pwzBuf`.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetVersionString` získá vestavěnou verzi aktuálního oboru metadat. Pokud se obor nikdy neuložil, nebude mít vestavěnou verzi a vrátí se prázdný řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
