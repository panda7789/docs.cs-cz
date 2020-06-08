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
ms.openlocfilehash: f55af87e21b48430807166cb03e1d41271e830a1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503429"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef – metoda
Vyřeší <xref:System.Type> odkaz reprezentovaný zadaným tokenem TypeRef.  
  
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
 pro IID rozhraní, které se má vrátit `ppIScope` . Obvykle by to bylo IID_IMetaDataImport.  
  
 `ppIScope`  
 mimo Rozhraní pro obor modulu, ve kterém je definován odkazovaný typ.  
  
 `ptd`  
 mimo Ukazatel na token TypeDef, který představuje odkazovaný typ.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> Tuto metodu nepoužívejte, pokud je načteno více domén aplikace. Metoda nerespektuje hranice aplikační domény. Je-li načteno více verzí sestavení a obsahují stejný typ se stejným oborem názvů, metoda vrátí rozsah modulu prvního hledaného typu.  
  
 `ResolveTypeRef`Metoda hledá definici typu v jiných modulech. Pokud je nalezena definice typu, `ResolveTypeRef` vrátí rozhraní do tohoto oboru modulu a také token typedef pro typ.  
  
 Pokud odkaz na typ, který má být vyřešen, má obor rozlišení AssemblyRef, `ResolveTypeRef` metoda vyhledá shodu pouze v oborech metadat, které již byly otevřeny pomocí volání metody [IMetaDataDispenser:: OpenScope –](imetadatadispenser-openscope-method.md) nebo metody [IMetaDataDispenser:: OpenScopeOnMemory –](imetadatadispenser-openscopeonmemory-method.md) . Důvodem je `ResolveTypeRef` , že nelze určit pouze z oboru AssemblyRef, kde na disku nebo v globální mezipaměti sestavení (GAC) sestavení je uloženo.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
