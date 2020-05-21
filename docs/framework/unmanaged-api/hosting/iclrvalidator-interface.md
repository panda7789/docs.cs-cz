---
title: ICLRValidator – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator
helpviewer_keywords:
- ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type:
- apiref
ms.openlocfilehash: e071f9cba7e991c59bf697647e0e4badea57573a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762029"
---
# <a name="iclrvalidator-interface"></a>ICLRValidator – rozhraní
Poskytuje metody pro ověřování přenosných spustitelných souborů (PE) a chyb ověřování sestav.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[FormatEventInfo – metoda](iclrvalidator-formateventinfo-method.md)|Získá podrobnou zprávu o zadané chybě ověřování.|  
|[Validate – metoda](iclrvalidator-validate-method.md)|Ověří v zadaném souboru přenositelné spustitelné soubory nebo jazyk MSIL (Microsoft Intermediate Language).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** IValidator. idl, IValidator. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRErrorReportingManager – rozhraní](iclrerrorreportingmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [CLRRuntimeHost – třída typu coclass](clrruntimehost-coclass.md)
