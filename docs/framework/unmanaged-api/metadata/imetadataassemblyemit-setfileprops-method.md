---
title: IMetaDataAssemblyEmit::SetFileProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 106ffeee521f69a73628b1fb6a611abc733583f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431869"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a>IMetaDataAssemblyEmit::SetFileProps – metoda
Upraví zadanou `File` strukturu metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `file`  
 pro Token metadat, který určuje `File` strukturu metadat, která se má upravit.  
  
 `pbHashValue`  
 pro Ukazatel na data algoritmu hash přidružená k souboru.  
  
 `cbHashValue`  
 pro Velikost v bajtech `pbHashValue`.  
  
 `dwFileFlags`  
 pro Bitová kombinace hodnot [CorFileFlags –](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) , které určují různé atributy souboru.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit `File` struktury metadat, použijte metodu [IMetaDataAssemblyEmit::D efinefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
