---
title: ICeeGen::AddSectionReloc – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8e270f45300bd5f8c2e6cd87f9b84f31ec42320
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722189"
---
# <a name="iceegenaddsectionreloc-method"></a>ICeeGen::AddSectionReloc – metoda
Přidá .reloc instrukce k základu kódu.  
  
 Tato metoda je zastaralý a neměl by se používat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `section`  
 [in] V části kódu v paměti, do které chcete přidat .reloc instrukce.  
  
 `offset`  
 [in] Posun oddílu.  
  
 `relativeTo`  
 [in] Oddíl, do které `offset` odkazuje.  
  
 `relocType`  
 [in] Jeden z [ceesectionreloctype –](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) hodnoty určující druh .reloc pokyny, jak přidat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICeeGen – rozhraní](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
