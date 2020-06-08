---
title: IMetaDataFilter – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: 821936d20a421739e8eb3d5df228888df7f022e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503780"
---
# <a name="imetadatafilter-interface"></a>IMetaDataFilter – rozhraní
Poskytuje metody pro označování a filtrování tokenů metadat, aby nedocházelo k opakujícím se akcím, které již byly provedeny.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[IsTokenMarked – metoda](imetadatafilter-istokenmarked-method.md)|Získá hodnotu, která označuje, zda byl zpracován zadaný token metadat.|  
|[MarkToken – metoda](imetadatafilter-marktoken-method.md)|Nastaví hodnotu označující, že zadaný token metadat byl zpracován.|  
|[UnmarkAll – metoda](imetadatafilter-unmarkall-method.md)|Odstraní značky zpracování ze všech tokenů v aktuálním oboru metadat.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](metadata-interfaces.md)
