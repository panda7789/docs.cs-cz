---
title: IMetaDataImport::GetPinvokeMap – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
ms.openlocfilehash: c458fef77b49f522ca21dd5487731f4d43588cea
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437096"
---
# <a name="imetadataimportgetpinvokemap-method"></a>IMetaDataImport::GetPinvokeMap – metoda
Získá token Odkaz ModuleRef představující cílové sestavení volání PInvoke.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 pro FieldDef nebo MethodDef token pro získání metadat mapování PInvoke pro.  
  
 `pdwMappingFlags`  
 mimo Ukazatel na příznaky použité pro mapování. Tato hodnota je Bitová maska z výčtu [CorPinvokeMap –](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) .  
  
 `szImportName`  
 mimo Název nespravované cílové knihovny DLL.  
  
 `cchImportName`  
 pro Velikost v různých znacích `szImportName`.  
  
 `pchImportName`  
 mimo Počet velkých znaků vrácených v `szImportName`.  
  
 `pmrImportDLL`  
 mimo Ukazatel na token Odkaz ModuleRef, který představuje knihovnu nespravovaného cílového objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
