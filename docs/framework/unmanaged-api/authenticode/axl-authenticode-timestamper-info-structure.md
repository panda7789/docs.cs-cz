---
title: Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae7879e1f6598108d839287792ed441391764ae2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776655"
---
# <a name="axl_authenticode_timestamper_info-structure"></a>Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO
Definuje informace o časovém razítku technologie Authenticode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`cbSize`|Velikost této struktury|  
|`dwError`|Kód chyby|  
|`algHash`|Algoritmus hash.|  
|`ftTimestamp`|Čas časového razítka.|  
|`pChainContext`|Kontext řetězu časového razítka.  Podívejte se na strukturu [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .|  
  
## <a name="see-also"></a>Viz také:

- [Authenticode](index.md)
