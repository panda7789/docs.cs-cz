---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: fb381a872cbeb787da0c6920f2cdeef434fb33ea
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008089"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda
Upraví zadanou `AssemblyRef` strukturu metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ar`  
 pro Token metadat, který určuje `AssemblyRef` strukturu metadat, která má být upravena.  
  
 `pbPublicKeyOrToken`  
 pro Veřejný klíč vydavatele odkazovaného sestavení.  
  
 `cbPublicKeyOrToken`  
 pro Velikost v bajtech `pbPublicKeyOrToken` .  
  
 `szName`  
 pro Textový název sestavení čitelný lidmi  
  
 `pMetaData`  
 pro Ukazatel na instanci AssemblyMetadata –, která obsahuje informace o verzi, platformě a národním prostředí pro sestavení.  
  
 `pbHashValue`  
 pro Ukazatel na data algoritmu hash přidružená k sestavení.  
  
 `cbHashValue`  
 pro Velikost v bajtech `pbHashValue` .  
  
 `dwAssemblyRefFlags`  
 pro Bitová kombinace hodnot [AssemblyRefFlags –](assemblyrefflags-enumeration.md) , které určují atributy odkazovaného sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit `AssemblyRef` strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::D efineassemblyref](imetadataassemblyemit-defineassemblyref-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
