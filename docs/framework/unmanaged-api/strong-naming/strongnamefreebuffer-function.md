---
title: StrongNameFreeBuffer – funkce
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: 50e3cc6e677de45be9256a2a818ebd6ed7d8b843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176913"
---
# <a name="strongnamefreebuffer-function"></a>StrongNameFreeBuffer – funkce
Uvolní paměť, která byla přidělena s předchozím voláním funkce silného názvu, jako je [například StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)nebo [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).  
  
 Tato funkce byla zastaralá. Místo toho použijte metodu [ICLRStrongName::StrongNameFreeBuffer.](../hosting/iclrstrongname-strongnamefreebuffer-method.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbMemory`  
 [v] Ukazatel na paměť k uvolnění.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameFreeBuffer – metoda](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
