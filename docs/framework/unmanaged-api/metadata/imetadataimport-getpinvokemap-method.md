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
ms.openlocfilehash: 8409e56b5ec4dbe47035a0555b6b7ce175b517ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490975"
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
 mimo Ukazatel na příznaky použité pro mapování. Tato hodnota je Bitová maska z výčtu [CorPinvokeMap –](corpinvokemap-enumeration.md) .  
  
 `szImportName`  
 mimo Název nespravované cílové knihovny DLL.  
  
 `cchImportName`  
 pro Velikost v různých znacích `szImportName` .  
  
 `pchImportName`  
 mimo Počet znaků vrácených v rámci `szImportName` .  
  
 `pmrImportDLL`  
 mimo Ukazatel na token Odkaz ModuleRef, který představuje knihovnu nespravovaného cílového objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
