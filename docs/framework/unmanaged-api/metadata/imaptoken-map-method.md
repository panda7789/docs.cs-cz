---
title: IMapToken::Map – metoda
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31c18061ad5f21e26665cd0d6883b0eb26afd1d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557472"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map – metoda
Mapuje vztah mezi sestaveními, používání metadat podpisů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tkImp`  
 [in] Token metadat, který představuje kód importovaný objekt.  
  
 `tkEmit`  
 [in] Token metadat, který představuje objekt emitovaný kód.  
  
## <a name="remarks"></a>Poznámky  
 Když tokenu přemapovat spadá sloučení, původní token má obor v oboru metadata importované (zdroj) a nový token působí v rámci metadata emitovaný (cíl).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMapToken – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
