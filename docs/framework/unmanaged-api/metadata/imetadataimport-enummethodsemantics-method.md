---
title: "IMetaDataImport::EnumMethodSemantics – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 883505076fa9ff4f335c08b069e801ebda1ebb2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics – metoda
Vytvoří výčet vlastností a změnu vlastnosti události, ke kterým je související zadanou metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phEnum`  
 [ve out] Ukazatel na enumerátor. Toto musí mít hodnotu NULL pro první volání této metody.  
  
 `mb`  
 [v] MethodDef token, který omezuje obor výčtu.  
  
 `rEventProp`  
 [out] Pole používá k ukládání událostí nebo vlastnosti.  
  
 `cMax`  
 [v] Maximální velikost `rEventProp` pole.  
  
 `pcEventProp`  
 [out] Počet událostí nebo vlastnosti, vrátí se v `rEventProp`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`úspěšně vrácena.|  
|`S_FALSE`|Nejsou žádné události nebo vlastnosti, které chcete vytvořit výčet. V takovém případě `pcEventProp` je nulová.|  
  
## <a name="remarks"></a>Poznámky  
 Definování mnoho běžných typů runtime jazyka *vlastnost* `Changed` události a `On` *vlastnost* `Changed` metody související s jejich vlastnosti. Například <xref:System.Windows.Forms.Control?displayProperty=nameWithType> definuje typ <xref:System.Windows.Forms.Control.Font%2A> vlastnost, <xref:System.Windows.Forms.Control.FontChanged> události a <xref:System.Windows.Forms.Control.OnFontChanged%2A> metoda. Metody přistupující objekt set <xref:System.Windows.Forms.Control.Font%2A> vlastnost volání <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodu, která zase vyvolá <xref:System.Windows.Forms.Control.FontChanged> událostí. By volání `EnumMethodSemantics` pomocí MethodDef pro <xref:System.Windows.Forms.Control.OnFontChanged%2A> získat odkazy na <xref:System.Windows.Forms.Control.Font%2A> vlastnost a <xref:System.Windows.Forms.Control.FontChanged> událostí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
