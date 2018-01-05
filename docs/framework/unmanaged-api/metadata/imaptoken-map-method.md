---
title: "IMapToken::Map – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMapToken.Map
api_location: mscoree.dll
api_type: COM
f1_keywords: IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe034d2bc6d70e820fa3ad5de8140afa9a19a6bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imaptokenmap-method"></a>IMapToken::Map – metoda
Mapuje vztah mezi sestavení pomocí metadat podpisy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tkImp`  
 [v] Metadata token, který představuje objekt importované kódu.  
  
 `tkEmit`  
 [v] Metadata token, který představuje objekt emitovaného kódu.  
  
## <a name="remarks"></a>Poznámky  
 Když tokenu znovu namapovat dojde během sloučení, původní token má obor v oboru metadata importované (zdroj) a nový token má obor v oboru metadata emitovaného (cíl).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMapToken – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
