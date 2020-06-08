---
title: IMetaDataEmit2::SetGenericParamProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: 8feba8e67f3a90dd48fd957065a9c166c204b87c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492730"
---
# <a name="imetadataemit2setgenericparamprops-method"></a>IMetaDataEmit2::SetGenericParamProps – metoda
Nastaví hodnoty vlastností pro definici obecného parametru, na kterou odkazuje zadaný token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `gp`  
 pro Token pro definici obecného parametru, pro který chcete nastavit hodnoty.  
  
 `dwParamFlags`  
 pro Hodnota výčtu [CorGenericParamAttr –](corgenericparamattr-enumeration.md) , která popisuje typ obecného parametru.  
  
 `szName`  
 pro Volitelné. Název parametru, pro který chcete nastavit hodnoty.  
  
 `reserved`  
 pro Vyhrazeno pro budoucí rozšíření.  
  
 `rtkConstraints`  
 pro Volitelné. Pole s nulovým zakončením v poli omezení typu. Členy pole musí být `mdTypeDef` `mdTypeRef` token metadat, nebo `mdTypeSpec` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
