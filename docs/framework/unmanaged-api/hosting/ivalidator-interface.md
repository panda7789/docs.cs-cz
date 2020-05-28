---
title: IValidator – rozhraní
ms.date: 03/30/2017
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
ms.openlocfilehash: d8e5ab607f9310341ded482b35f02f3845926328
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008557"
---
# <a name="ivalidator-interface"></a>IValidator – rozhraní
Poskytuje metody pro ověřování přenosných spustitelných souborů (PE) a chyb ověřování sestav.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|Ověření|Ověří zadané soubory PE nebo jazyka MSIL (Microsoft Intermediate Language).|  
|Formateventinfo –|Načte chybovou zprávu odpovídající zadané chybě ověřování.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** IValidator. idl, IValidator. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro hostování](hosting-interfaces.md)
- [CorRuntimeHost – třída typu coclass](corruntimehost-coclass.md)
