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
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176068"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map – metoda
Mapuje vztah mezi sestaveními pomocí podpisů metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tkImp`  
 [v] Token metadat, který představuje importovaný objekt kódu.  
  
 `tkEmit`  
 [v] Token metadat, který představuje objekt emitovaného kódu.  
  
## <a name="remarks"></a>Poznámky  
 Když dojde k opětovnému mapování tokenu během sloučení, původní token je vymezen v oboru importovaného (zdrojového) metadat a nový token je vymezen v oboru emitovaných (cílových) metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMapToken – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
