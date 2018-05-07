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
ms.openlocfilehash: f0b30cc2c499644ffc97a734e1554e4e352b34af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM – funkce
Vynutí modul CLR (CLR) Chcete-li uvolnit všechny ukazatele rozhraní, které uchovává uvnitř běhové obálky s možností (RCW). To má za následek uvolnění všech RCW mezipamětí. Globální funkce je ve zastaralá [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Místo toho použijte vstupní bod pro konkrétní modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Poznámky  
 `CoEEShutDownCOM` Funkce nejprve uvolní všechny RCWs v všechny kontexty a všechny mezipaměti a pak odebere všechna oznámení rozbalovací úplné stávající v instalačním programu. Dojde k žádné uvolnění knihovny DLL.  
  
> [!CAUTION]
>  Tato funkce ovlivňuje všechny moduly runtime, která jsou načtena do procesu.  
  
 Od verze [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], volání vstupní bod pro tuto funkci na konkrétní runtime chcete ovlivnit. Chcete-li získat vstupního bodu, zavolejte [iclrruntimeinfo::GetProcAddress –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metoda a zadejte "Coeeshutdowncom –".  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
