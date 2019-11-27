---
title: IMetaDataImport::GetPermissionSetProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
ms.openlocfilehash: a020a0343eecceb4a85ebbddffe323c7f7bdca3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437112"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a>IMetaDataImport::GetPermissionSetProps – metoda
Získá metadata přidružená k <xref:System.Security.PermissionSet?displayProperty=nameWithType> reprezentované zadaným tokenem oprávnění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pm`  
 pro Token metadat oprávnění, který představuje sadu oprávnění k získání vlastností metadat pro.  
  
 `pdwAction`  
 mimo Ukazatel na sadu oprávnění.  
  
 `ppvPermission`  
 mimo Ukazatel na binární podpis metadat sady oprávnění.  
  
 `pcbPermission`  
 mimo Velikost v bajtech `ppvPermission`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.PermissionSet>
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
