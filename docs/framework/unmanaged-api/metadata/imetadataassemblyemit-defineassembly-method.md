---
title: IMetaDataAssemblyEmit::DefineAssembly – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 17c91200730431c4c6e230b8c1561ce7c4863868
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008180"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly – metoda
Vytvoří `Assembly` strukturu obsahující metadata pro zadané sestavení a vrátí přidružený token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKey`  
 pro Veřejný klíč, který identifikuje vydavatele sestavení, nebo hodnotu NULL, pokud sestavení není silně pojmenováno.  
  
 `cbPublicKey`  
 pro Velikost v bajtech `pbPublicKey` .  
  
 `uHashAlgId`  
 pro Identifikátor algoritmu hash, který má být použit k zašifrování souborů v sestavení, nebo hodnota NULL pro určení algoritmu SHA-1.  
  
 `szName`  
 pro Textový název sestavení čitelný lidmi Tato hodnota nesmí překročit 1024 znaků.  
  
 `pMetaData`  
 pro Ukazatel na instanci AssemblyMetadata –, která obsahuje informace o verzi, platformě a národním prostředí pro sestavení.  
  
 `dwAssemblyFlags`  
 pro Kombinace hodnot [CorAssemblyFlags –](corassemblyflags-enumeration.md) popisujících funkce sestavení.  
  
 `pmda`  
 mimo Ukazatel na token metadat.  
  
## <a name="remarks"></a>Poznámky  
 `Assembly`V rámci manifestu lze definovat pouze jednu strukturu metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
