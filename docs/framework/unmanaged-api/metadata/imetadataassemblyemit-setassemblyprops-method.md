---
title: IMetaDataAssemblyEmit::SetAssemblyProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: 7c6adcbcfe64f63048078b4ccba6727a58531033
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008102"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps – metoda
Upraví zadanou `Assembly` strukturu metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pma`  
 pro Token metadat, který určuje `Assembly` strukturu metadat, která má být upravena.  
  
 `pbPublicKey`  
 pro Ukazatel na veřejný klíč vydavatele sestavení.  
  
 `cbPublicKey`  
 pro Velikost v bajtech `pbPublicKey` .  
  
 `ulHashAlgId`  
 pro Identifikátor algoritmu hash, který slouží k hashování souborů sestavení.  
  
 `szName`  
 pro Textový název sestavení čitelný lidmi  
  
 `pMetaData`  
 pro Ukazatel na AssemblyMetadata –, který obsahuje informace o verzi, platformě a národním prostředí pro sestavení.  
  
 `dwAssemblyFlags`  
 pro Bitová kombinace hodnot [AssemblyFlags –](assemblyflags-enumeration.md) , které určují různé atributy sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit `Assembly` strukturu metadat, použijte metodu [IMetaDataAssemblyEmit::D efineassembly](imetadataassemblyemit-defineassembly-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
