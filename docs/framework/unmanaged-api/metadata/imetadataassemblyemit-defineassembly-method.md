---
title: "IMetaDataAssemblyEmit::DefineAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35bc85cdc4380ee112b7095866c05e5d7639200b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly – metoda
Vytvoří `Assembly` struktury obsahující metadata pro zadaného sestavení a vrátí token přidružených metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `pbPublicKey`  
 [v] Veřejný klíč, který identifikuje vydavatele sestavení, nebo hodnota NULL, pokud sestavení nemá silný název.  
  
 `cbPublicKey`  
 [v] Velikost v bajtech `pbPublicKey`.  
  
 `uHashAlgId`  
 [v] Identifikátor algoritmu hash, který chcete použít k šifrování souborů v sestavení nebo NULL. Chcete-li určit algoritmus SHA-1.  
  
 `szName`  
 [v] Čitelný text název sestavení. Tato hodnota nesmí být delší než 1024 znaků.  
  
 `pMetaData`  
 [v] Ukazatel na instanci assemblymetadata –, který obsahuje informace o verzi, platformy a národní prostředí pro sestavení.  
  
 `dwAssemblyFlags`  
 [v] Kombinace [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty, které popisují funkce sestavení.  
  
 `pmda`  
 [out] Ukazatel na token metadat.  
  
## <a name="remarks"></a>Poznámky  
 Pouze jeden `Assembly` v manifestu je možné definovat strukturu metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
