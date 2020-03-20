---
title: PublicKeyBlob – struktura
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176952"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob – struktura
Představuje v binárním formátu veřejný klíč dvojice veřejného a soukromého klíče.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`SigAlgId`|Identifikátor podpisového algoritmu (typu `ALG_ID`, jak je definován ve wincrypt.h) veřejného klíče.|  
|`HashAlgId`|Identifikátor algoritmu hash (typu `ALG_ID`, jak je definován ve wincrypt.h) veřejného klíče.|  
|`cbPublicKey`|Délka klíče v bajtů.|  
|`PublicKey`|Pole bajtů s proměnnou délkou, které obsahuje hodnotu klíče ve formátu vráceném rozhraním CryptoAPI.|  
  
## <a name="remarks"></a>Poznámky  
 Struktura `PublicKeyBlob` je používána [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)a další funkce silného názvu představují veřejný klíč dvojice veřejného a soukromého klíče.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [StrongNameGetPublicKey – funkce](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration – funkce](strongnamesignaturegeneration-function.md)
