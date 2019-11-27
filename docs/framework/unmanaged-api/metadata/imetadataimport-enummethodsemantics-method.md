---
title: IMetaDataImport::EnumMethodSemantics – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: ff6932b6040a19e0ccda2f8d2140fa131cdd9224
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450073"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics – metoda
Vytvoří výčet vlastností a událostí změny vlastností, na které se vztahuje zadaná metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [in, out] Ukazatel na enumerátor. Pro první volání této metody musí mít hodnotu NULL.  
  
 `mb`  
 pro Token MethodDef omezující obor výčtu.  
  
 `rEventProp`  
 mimo Pole, které se používá k uložení událostí nebo vlastností.  
  
 `cMax`  
 pro Maximální velikost `rEventProp` pole  
  
 `pcEventProp`  
 mimo Počet událostí nebo vlastností vrácených v `rEventProp`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` byla úspěšně vrácena.|  
|`S_FALSE`|Neexistují žádné události ani vlastnosti k zobrazení výčtu. V takovém případě je `pcEventProp` nula.|  
  
## <a name="remarks"></a>Poznámky  
 Mnoho typů modulu CLR (Common Language Runtime) definuje *vlastnosti*`Changed` události a `On`*vlastností*`Changed` metod souvisejících s jejich vlastnostmi. Například typ <xref:System.Windows.Forms.Control?displayProperty=nameWithType> definuje vlastnost <xref:System.Windows.Forms.Control.Font%2A>, událost <xref:System.Windows.Forms.Control.FontChanged> a metodu <xref:System.Windows.Forms.Control.OnFontChanged%2A>. Metoda set přistupující objekt vlastnosti <xref:System.Windows.Forms.Control.Font%2A> volá metodu <xref:System.Windows.Forms.Control.OnFontChanged%2A>, která zase vyvolá událost <xref:System.Windows.Forms.Control.FontChanged>. Chcete-li získat odkazy na vlastnost <xref:System.Windows.Forms.Control.Font%2A> a událost <xref:System.Windows.Forms.Control.FontChanged>, zavolejte `EnumMethodSemantics` pomocí vlastnosti MethodDef pro <xref:System.Windows.Forms.Control.OnFontChanged%2A>.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
