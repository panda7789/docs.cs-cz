---
title: "IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 446137d28fdd64d7f9e5c84cc57e9ec967982430
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps – metoda
Upraví zadaný `AssemblyRef` strukturu metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `ar`  
 [v] Metadata token, který určuje `AssemblyRef` strukturu metadat má být změněn.  
  
 `pbPublicKeyOrToken`  
 [v] Veřejný klíč vydavatele odkazované sestavení.  
  
 `cbPublicKeyOrToken`  
 [v] Velikost v bajtech `pbPublicKeyOrToken`.  
  
 `szName`  
 [v] Čitelný text název sestavení.  
  
 `pMetaData`  
 [v] Ukazatel na instanci assemblymetadata –, který obsahuje informace o verzi, platformy a národní prostředí pro sestavení.  
  
 `pbHashValue`  
 [v] Ukazatel na hodnotu hash data přidružená k sestavení.  
  
 `cbHashValue`  
 [v] Velikost v bajtech `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [v] Bitovou kombinaci [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) hodnoty, které určují atributy odkazované sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit `AssemblyRef` strukturu metadat, použijte [imetadataassemblyemit::defineassemblyref –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
