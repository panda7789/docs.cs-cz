---
title: IMetaDataAssemblyImport::FindExportedTypeByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
ms.openlocfilehash: ac6de9a16fad6ba9d14f3960ddd28c42c111f254
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009389"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a>IMetaDataAssemblyImport::FindExportedTypeByName – metoda
Získá ukazatel na exportovaný typ, který je dán názvem a nadřazeným typem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 pro Název exportovaného typu.  
  
 `mdtExportedType`  
 pro Token metadat pro ohraničující třídu exportovaného typu Tato hodnota je `mdExportedTypeNil` , pokud požadovaný exportovaný typ není vnořený typ.  
  
 `ptkExportedType`  
 mimo Ukazatel na `mdExportedType` token, který představuje exportovaný typ.  
  
## <a name="remarks"></a>Poznámky  
 `FindExportedTypeByName`Metoda používá ke zjišťování odkazů standardní pravidla zaměstnaná modulem CLR (Common Language Runtime).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyImport – rozhraní](imetadataassemblyimport-interface.md)
- [Jak běhové prostředí vyhledává sestavení](../../deployment/how-the-runtime-locates-assemblies.md)
