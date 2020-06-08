---
title: IMetaDataImport::GetScopeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: 0916b6382bb9352616d85e21f423301dc6aa9fa9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490845"
---
# <a name="imetadataimportgetscopeprops-method"></a>IMetaDataImport::GetScopeProps – metoda
Získá název a volitelně identifikátor verze sestavení nebo modulu v aktuálním oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 mimo Vyrovnávací paměť pro název sestavení nebo modulu.  
  
 `cchName`  
 pro Velikost v různých znacích `szName` .  
  
 `pchName`  
 mimo Počet znaků vrácených v rámci `szName` .  
  
 `pmvid`  
 [out, volitelné] Ukazatel na identifikátor GUID, který jedinečně identifikuje verzi sestavení nebo modulu.  
  
## <a name="remarks"></a>Poznámky  
 Metoda [IMetaDataEmit:: SetModuleProps –](imetadataemit-setmoduleprops-method.md) slouží k nastavení těchto vlastností.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
