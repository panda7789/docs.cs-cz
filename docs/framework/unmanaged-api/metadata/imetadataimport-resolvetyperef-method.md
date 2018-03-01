---
title: "IMetaDataImport::ResolveTypeRef – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64a783297b27c9d1400670eecb7dfe4cb69c2b96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef – metoda
Přeloží <xref:System.Type> odkaz reprezentována zadaný odkaz TypeRef token.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tr`  
 [v] Token metadata Odkaz TypeRef k vrácení informací odkazovaného typu pro.  
  
 `riid`  
 [v] Identifikátory IID rozhraní se vrátit v `ppIScope`. Obvykle to může být IID_IMetaDataImport.  
  
 `ppIScope`  
 [out] Rozhraní modulu oboru, ve kterém je definovaný odkazovaného typu.  
  
 `ptd`  
 [out] Ukazatel na TypeDef token, který představuje odkazovaného typu.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Tato metoda nepoužívejte, pokud se načtou více domén aplikací. Metoda nedodržuje hranice domény aplikace. Pokud se načtou více verzí sestavení a obsahují stejného typu se o stejný obor názvů, vrátí metoda rozsah modulu první typu, které najde.  
  
 `ResolveTypeRef` Metoda vyhledá definici typu v dalších modulů. Pokud se najde definici typu `ResolveTypeRef` vrátí do oboru tohoto modulu a také token TypeDef pro typ rozhraní.  
  
 Pokud má odkaz na typ na možné přeložit na odkaz AssemblyRef, rozsah řešení `ResolveTypeRef` metoda vyhledá shodu pouze v obory metadat, která již byla otevřena pomocí volání buď [imetadatadispenser::openscope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)metoda nebo [imetadatadispenser::openscopeonmemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metoda. Důvodem je, že `ResolveTypeRef` nemůže zjistit z pouze odkaz AssemblyRef oboru na disk nebo do globální mezipaměti sestavení sestavení se uloží.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
