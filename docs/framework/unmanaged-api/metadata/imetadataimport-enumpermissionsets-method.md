---
title: IMetaDataImport::EnumPermissionSets – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 990910b8b30e9794550d71cf9eaf8cd53639f696
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492241"
---
# <a name="imetadataimportenumpermissionsets-method"></a>IMetaDataImport::EnumPermissionSets – metoda
Vytvoří výčet oprávnění pro objekty v oboru Zadaná metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,   
   [in]      mdToken       tk,   
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out v] Ukazatel na enumerátor. První volání této metody musí mít hodnotu NULL.  
  
 `tk`  
 [in] Token metadat, který omezuje obor vyhledávání, nebo hodnota NULL pro hledání oboru nejširší možné.  
  
 `dwActions`  
 [in] Příznaky představující <xref:System.Security.Permissions.SecurityAction> hodnoty pro zahrnutí `rPermission`, nebo nula, která vrátí všechny akce.  
  
 `rPermission`  
 [out] Pole pro ukládání tokenů oprávnění.  
  
 `cMax`  
 [in] Maximální velikost `rPermission` pole.  
  
 `pcTokens`  
 [out] Počet tokenů oprávnění vrácené v `rPermission`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumPermissionSets` bylo úspěšně vráceno.|  
|`S_FALSE`|Neexistují žádné tokeny se vytvořit výčet. V takovém případě `pcTokens` je nula.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
