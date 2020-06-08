---
title: IMetaDataTables::GetBlob – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
ms.openlocfilehash: ff97e419c5309fa7cb820cb7e82db96fee34f30c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501271"
---
# <a name="imetadatatablesgetblob-method"></a>IMetaDataTables::GetBlob – metoda
Získá ukazatel na binární rozsáhlý objekt (BLOB) v zadaném indexu sloupce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ixBlob`  
 pro Adresa paměti, ze které se má získat `ppData` .  
  
 `pcbData`  
 mimo Ukazatel na velikost (v bajtech) `ppData` .  
  
 `ppData`  
 mimo Ukazatel na ukazatel na načtená binární data.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataTables – rozhraní](imetadatatables-interface.md)
- [IMetaDataTables2 – rozhraní](imetadatatables2-interface.md)
