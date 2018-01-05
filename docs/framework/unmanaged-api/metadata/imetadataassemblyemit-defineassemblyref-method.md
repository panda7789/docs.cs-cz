---
title: "IMetaDataAssemblyEmit::DefineAssemblyRef – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssemblyRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 123bd37d189477eade72e3b0e74f923fecce57a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef – metoda
Vytvoří `AssemblyRef` struktura obsahující metadata pro sestavení, které toto sestavení odkazuje a vrátí token přidružených metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbPublicKeyOrToken`  
 [v] Veřejný klíč vydavatele odkazované sestavení. Pomocné funkce [strongnametokenfromassembly –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) můžete použít k získání hodnota hash veřejného klíče předat jako tento parametr.  
  
 `cbPublicKeyOrToken`  
 [v] Velikost v bajtech `pbPublicKeyOrToken`.  
  
 `szName`  
 [v] Čitelný text název sestavení. Tato hodnota nesmí být delší než 1024 znaků.  
  
 `pMetaData`  
 [v] Assemblymetadata – instance, který obsahuje informace o verzi, platformy a národní prostředí odkazované sestavení.  
  
 `pbHashValue`  
 [v] Hodnota hash data související s odkazované sestavení. Volitelné.  
  
 `cbHashValue`  
 [v] Velikost v bajtech `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [v] Bitovou kombinaci [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty, které ovlivňují chování objektu modul provádění.  
  
 `pmdar`  
 [out] Ukazatel na vrácený `AssemblyRef` metadata token.  
  
## <a name="remarks"></a>Poznámky  
 Jeden `AssemblyRef` strukturu metadat musí být definovaná pro každé sestavení, které odkazuje toto sestavení.  
  
 V době běhu podrobnosti o odkazované sestavení předaný překladač sestavení s údajem, že představují údaje "tak, jak vytvořené". Překladač sestavení potom platí zásady.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
