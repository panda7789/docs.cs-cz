---
title: IMetaDataAssemblyEmit::DefineFile – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: 0b7ca6f9878ed2fa2d90ea93e5101f0a66ec2d5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440203"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile – metoda
Vytvoří `File` strukturu metadat obsahující metadata pro sestavení, na které odkazuje toto sestavení, a vrátí přidružený token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 pro Název souboru, který se má spotřebovat  
  
 `pbHashValue`  
 pro Ukazatel na data algoritmu hash přidružená k sestavení.  
  
 `cbHashValue`  
 pro Velikost v bajtech `pbHashValue`.  
  
 `dwFileFlags`  
 pro Bitová kombinace hodnot `FileFlags`, které určují nastavení vlastností.  
  
 `pmdf`  
 mimo Ukazatel na vrácený token `File`.  
  
## <a name="remarks"></a>Poznámky  
 Pro každý soubor, který byl součástí tohoto sestavení v době, kdy bylo sestavení sestaveno, je třeba definovat jednu `File` strukturu metadat, a to s výjimkou souboru, který obsahuje metadata.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
