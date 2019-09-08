---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9aaa0258b53b6b39874c8c99c71ecf53cbdb8f97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787075"
---
# <a name="axl_authenticode_signer_info-structure"></a>Struktura AXL_AUTHENTICODE_SIGNER_INFO
Definuje přihlašovací údaje Authenticode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`cbSize`|Velikost této struktury|  
|`dwError`|Kód chyby|  
|`algHash`|Algoritmus hash.|  
|`pwszHash`|Hodnota hash|  
|`pwszDescription`|Popis.|  
|`pwszDescriptionUrl`|Adresa URL popisu|  
|`pChainContext`|Kontext řetězce podepsaného. Podívejte se na strukturu [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .|  
  
## <a name="see-also"></a>Viz také:

- [Authenticode](index.md)
