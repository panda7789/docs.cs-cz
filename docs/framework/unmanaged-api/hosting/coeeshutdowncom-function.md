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
ms.openlocfilehash: 4e85a9a98bf0550fa906f8b905c73890948f4ac1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124943"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM – funkce
Vynutí modul CLR (Common Language Runtime), aby uvolnil všechny ukazatele rozhraní, které se nachází uvnitř za běhu volat obálky (RCW). To má vliv na uvolnění všech mezipamětí RCW cache. Tato globální funkce je zastaralá v .NET Framework 4. Místo toho použijte vstupní bod konkrétního modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Funkce `CoEEShutDownCOM` nejprve uvolní všechny RCW ve všech kontextech a ve všech mezipamětích a pak odebere všechna oznámení, která byla v instalačním programu existující. Nedochází k uvolnění knihovny DLL.  
  
> [!CAUTION]
> Tato funkce má vliv na všechny moduly runtime, které jsou načteny do procesu.  
  
 Počínaje .NET Framework 4 volejte vstupní bod pro tuto funkci pro konkrétní modul runtime, který chcete ovlivnit. Chcete-li získat vstupní bod, zavolejte metodu [ICLRRuntimeInfo:: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) a zadejte "CoEEShutDownCOM –".  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
