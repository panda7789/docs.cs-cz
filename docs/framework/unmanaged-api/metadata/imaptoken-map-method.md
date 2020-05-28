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
ms.openlocfilehash: 027694cee1b3e4d990796ba31300918f6d859679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008193"
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
 pro Token metadat, který reprezentuje objekt importovaného kódu.  
  
 `tkEmit`  
 pro Token metadat, který reprezentuje objekt emitovaného kódu.  
  
## <a name="remarks"></a>Poznámky  
 Když dojde ke změně tokenu během sloučení, původní token se zaznamená v importovaném (zdrojovém) oboru metadat a nový token je vymezen v oboru metadat emited (Targeting).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMapToken – rozhraní](imaptoken-interface.md)
