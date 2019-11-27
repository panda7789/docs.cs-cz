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
ms.openlocfilehash: 800b15bb75e74898cee9d838900ea14b60620940
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431468"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef – metoda
Vyřeší odkaz na <xref:System.Type> reprezentovaný zadaným tokenem TypeRef.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tr`  
 pro Token metadat TypeRef, pro který se mají vrátit odkazované informace o typu pro.  
  
 `riid`  
 pro IID rozhraní, které se má vrátit v `ppIScope`. Obvykle by to bylo IID_IMetaDataImport.  
  
 `ppIScope`  
 mimo Rozhraní pro obor modulu, ve kterém je definován odkazovaný typ.  
  
 `ptd`  
 mimo Ukazatel na token TypeDef, který představuje odkazovaný typ.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> Tuto metodu nepoužívejte, pokud je načteno více domén aplikace. Metoda nerespektuje hranice aplikační domény. Je-li načteno více verzí sestavení a obsahují stejný typ se stejným oborem názvů, metoda vrátí rozsah modulu prvního hledaného typu.  
  
 Metoda `ResolveTypeRef` vyhledá definici typu v jiných modulech. Pokud je nalezena definice typu, `ResolveTypeRef` vrátí rozhraní do tohoto oboru modulu a také token TypeDef pro typ.  
  
 Pokud odkaz na typ, který má být vyřešen, má obor rozlišení AssemblyRef, metoda `ResolveTypeRef` vyhledá shodu pouze v oborech metadat, které již byly otevřeny pomocí volání metody [IMetaDataDispenser:: OpenScope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) nebo metody [IMetaDataDispenser:: OpenScopeOnMemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) . Důvodem je, že `ResolveTypeRef` nelze určit pouze z oboru AssemblyRef, kde na disku nebo v globální mezipaměti sestavení (GAC) je sestavení uloženo.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
