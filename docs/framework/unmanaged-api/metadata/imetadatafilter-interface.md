---
title: "IMetaDataFilter – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter
helpviewer_keywords: IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7c0afbb9be9af3ffe69ddfcac85b70de53a391ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatafilter-interface"></a>IMetaDataFilter – rozhraní
Poskytuje metody pro označování a filtrování tokenů metadat, aby se zabránilo opakující se akce, které již byla přijata.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Istokenmarked – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|Získá hodnotu označující, zda je zadaná metadata token byla zpracována.|  
|[Marktoken – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|Nastaví hodnotu, která určuje, že token Zadaná metadata byla zpracována.|  
|[Unmarkall – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|Odebere všechny tokeny, které jsou v aktuálním oboru metadata značky ve zpracování.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
