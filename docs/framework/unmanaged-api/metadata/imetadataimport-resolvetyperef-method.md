---
title: IMetaDataImport::ResolveTypeRef – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c69c67c5c9d996bd746d82ea86caf4a396c0b10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625234"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef – metoda
Řeší <xref:System.Type> odkaz reprezentována zadaný token TypeRef.  
  
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
 [in] Token TypeRef metadat nevrátil informace odkazovaného typu pro.  
  
 `riid`  
 [in] Identifikátor IID rozhraní vrátit v `ppIScope`. Obvykle by to IID_IMetaDataImport.  
  
 `ppIScope`  
 [out] Rozhraní pro rozsah modulu, ve kterém odkazovaný typ je definován.  
  
 `ptd`  
 [out] Ukazatel na token TypeDef, který představuje odkazovaného typu.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Nepoužívejte tuto metodu, pokud jsou načteny více domén aplikace. Metoda nerespektuje hranice aplikační domény. Pokud jsou načteno více verzí sestavení a obsahují stejný typ s stejný obor názvů, metoda vrátí rozsah modulu první typu, které nalezne.  
  
 `ResolveTypeRef` Metoda vyhledá do definice typu v dalších modulů. Pokud se najde definici typu `ResolveTypeRef` vrátí rozsah tohoto modulu, jakož i token TypeDef pro typ rozhraní.  
  
 Pokud má rozlišení oboru odkaz AssemblyRef, které je potřeba vyřešit odkaz na typ `ResolveTypeRef` metoda vyhledá shodu pouze v obory metadat, které již byly otevřeny pomocí volání na buď [imetadatadispenser::openscope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)metoda nebo [imetadatadispenser::openscopeonmemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metody. Důvodem je, že `ResolveTypeRef` nelze určit ze pouze odkaz AssemblyRef obor na disk nebo do globální mezipaměti sestavení sestavení se mají ukládat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
