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
ms.openlocfilehash: 6c58a0726e0869178838999c6b000e0ad975f145
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140615"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob – struktura
Představuje v binárním formátu veřejný klíč páru veřejného a privátního klíče.  
  
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
|`SigAlgId`|Identifikátor algoritmu podpisu (typu `ALG_ID`, jak je definován v WinCrypt. h) veřejného klíče.|  
|`HashAlgId`|Identifikátor algoritmu hash (typu `ALG_ID`, jak je definován v WinCrypt. h) veřejného klíče.|  
|`cbPublicKey`|Délka klíče v bajtech|  
|`PublicKey`|Bajtové pole s proměnlivou délkou, které obsahuje hodnotu klíče ve formátu vráceném rozhraním CryptoAPI.|  
  
## <a name="remarks"></a>Poznámky  
 `PublicKeyBlob` struktura se používá v [StrongNameGetPublicKey –](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration –](strongnamesignaturegeneration-function.md)a dalších funkcích se silným názvem, které reprezentují veřejný klíč páru veřejného a privátního klíče.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** StrongName. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [StrongNameGetPublicKey – funkce](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration – funkce](strongnamesignaturegeneration-function.md)
