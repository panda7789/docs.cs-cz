---
title: CoEEShutDownCOM – funkce
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a28b9d6e41d0572d423576f5b4024a60a70216c
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456864"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM – funkce
Vynutí common language runtime (CLR) uvolnit všechny ukazatele rozhraní, které obsahuje uvnitř obálek volatelných za běhu (RCW). To má za následek uvolnění všech RCW mezipamětí. Tato globální funkce je zastaralá ve [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Místo toho použijte vstupní bod pro konkrétní prostředí runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Poznámky  
 `CoEEShutDownCOM` Funkce nejprve uvolní všechny RCW ve všech kontextech a všechny mezipaměti a pak taky odebere všechna oznámení vše existující v instalačním programu. Vyvolá se žádná uvolnění knihovny DLL.  
  
> [!CAUTION]
>  Tuto funkci ovlivňuje všechny moduly runtime, která jsou načtena do procesu.  
  
 Od verze rozhraní .NET Framework 4, volání vstupní bod pro tuto funkci na konkrétní modul runtime, který chcete ovlivnit. Získání vstupního bodu, zavolejte [iclrruntimeinfo::GetProcAddress –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metodu a zadejte "Coeeshutdowncom –".  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
