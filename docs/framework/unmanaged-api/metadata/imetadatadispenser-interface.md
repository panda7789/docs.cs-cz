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
ms.openlocfilehash: 2bdfe65dbf923ec61d91a259b5257d892fef53da
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007335"
---
# <a name="imetadatadispenser-interface"></a>IMetaDataDispenser – rozhraní
Poskytuje metody pro vytvoření nového oboru metadat nebo otevření existujícího.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[DefineScope – metoda](imetadatadispenser-definescope-method.md)|Vytvoří novou oblast v paměti, kde můžete vytvořit nová metadata.|  
|[OpenScope – metoda](imetadatadispenser-openscope-method.md)|Otevře existující soubor na disku a namapuje jeho metadata do paměti.|  
|[OpenScopeOnMemory – metoda](imetadatadispenser-openscopeonmemory-method.md)|Otevře oblast paměti, která obsahuje existující metadata. To znamená, že tato metoda otevře zadanou oblast paměti, ve které jsou stávající data považována za metadata.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataDispenserEx – rozhraní](imetadatadispenserex-interface.md)
- [Rozhraní pro metadata](metadata-interfaces.md)
