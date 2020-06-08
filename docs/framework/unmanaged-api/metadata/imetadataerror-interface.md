---
title: IMetaDataError – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
ms.openlocfilehash: 46370da4e61dc90f2386170745da4f95ac7de63b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492756"
---
# <a name="imetadataerror-interface"></a>IMetaDataError – rozhraní
Poskytuje mechanismus zpětného volání pro hlášení chyb během sloučení metadat.  
  
> [!NOTE]
> `IMetaDataError`Rozhraní musí být implementováno klientem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[OnError – metoda](imetadataerror-onerror-method.md)|Poskytuje oznámení o chybách, ke kterým došlo během sloučení metadat.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](metadata-interfaces.md)
