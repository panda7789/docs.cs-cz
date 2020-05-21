---
title: ICLRStrongName2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
ms.openlocfilehash: 9715369f4cf1b2a7078be14a2fc597f735ab6fd3
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763160"
---
# <a name="iclrstrongname2-interface"></a>ICLRStrongName2 – rozhraní
Poskytuje možnost vytvářet silné názvy pomocí skupiny SHA-2 algoritmů Secure Hash (SHA-256, SHA-384 a SHA-512).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[StrongNameGetPublicKeyEx – metoda](strongnamegetpublickeyex-method.md)|Získá veřejný klíč z páru veřejného a privátního klíče a určí algoritmus hash a algoritmus podpisu.|  
|[StrongNameSignatureVerificationEx2 – metoda](strongnamesignatureverificationex2-method.md)|Ověří podpis silně pojmenovaného sestavení a poskytuje mapování z klíče ECMA na skutečný klíč.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
