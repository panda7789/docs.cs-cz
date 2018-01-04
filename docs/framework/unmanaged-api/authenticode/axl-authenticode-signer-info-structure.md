---
title: Struktura AXL_AUTHENTICODE_SIGNER_INFO
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a952dd8ae31cadad250111d9bbcd4c42466547e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="axlauthenticodesignerinfo-structure"></a>Struktura AXL_AUTHENTICODE_SIGNER_INFO
Definuje informace podepisující osoba Authenticode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`cbSize`|Velikost tuto strukturu.|  
|`dwError`|Kód chyby|  
|`algHash`|Algoritmus hash.|  
|`pwszHash`|Hodnota hash.|  
|`pwszDescription`|Popis.|  
|`pwszDescriptionUrl`|Adresa URL popis.|  
|`pChainContext`|Kontext řetězu autora podpisu. Najdete v článku [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) struktury.|  
  
## <a name="see-also"></a>Viz také  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
