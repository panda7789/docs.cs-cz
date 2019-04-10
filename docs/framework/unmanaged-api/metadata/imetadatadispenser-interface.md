---
title: IMetaDataDispenser – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dda284fc86f0a82472c59d6bab08fd4a87364723
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225973"
---
# <a name="imetadatadispenser-interface"></a>IMetaDataDispenser – rozhraní
Poskytuje metody pro vytvoření nového oboru metadat, nebo otevřete existující.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DefineScope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|Vytvoří nové oblasti v paměti, kde můžete vytvořit nová metadata.|  
|[OpenScope – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|Otevření existujícího souboru na disku a mapuje jeho metadata do paměti.|  
|[OpenScopeOnMemory – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|Otevře se oblast paměti, která obsahuje existující metadata. To znamená, že tato metoda otevře oblastí paměti, ve kterém existujících dat je považován za metadat.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [Rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
