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
ms.openlocfilehash: 84cf5ac9eab5749d3bdc63670fe5c31bfb62abcd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490401"
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
 pro Velikost pole v různých znacích `pwzBuf` .  
  
 `pccBufSize`  
 mimo V poli se vrátil počet velkých znaků, včetně ukončovacího znaku null `pwzBuf` .  
  
## <a name="remarks"></a>Poznámky  
 `GetVersionString`Metoda získá vestavěnou verzi aktuálního oboru metadat. Pokud se obor nikdy neuložil, nebude mít vestavěnou verzi a vrátí se prázdný řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
