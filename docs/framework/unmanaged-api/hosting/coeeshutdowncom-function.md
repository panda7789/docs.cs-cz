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
ms.openlocfilehash: 3eb8bffee9d30a89c39a900e600ebf171456b9f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616785"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM – funkce
Vynutí modul CLR (Common Language Runtime), aby uvolnil všechny ukazatele rozhraní, které se nachází uvnitř za běhu volat obálky (RCW). To má vliv na uvolnění všech mezipamětí RCW cache. Tato globální funkce je zastaralá v .NET Framework 4. Místo toho použijte vstupní bod konkrétního modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Poznámky  
 `CoEEShutDownCOM`Funkce nejprve uvolní všechny RCW ve všech kontextech a ve všech mezipamětích a následně odebere všechna oznámení, která jsou v instalaci existující. Nedochází k uvolnění knihovny DLL.  
  
> [!CAUTION]
> Tato funkce má vliv na všechny moduly runtime, které jsou načteny do procesu.  
  
 Počínaje .NET Framework 4 volejte vstupní bod pro tuto funkci pro konkrétní modul runtime, který chcete ovlivnit. Chcete-li získat vstupní bod, zavolejte metodu [ICLRRuntimeInfo:: GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) a zadejte "CoEEShutDownCOM –".  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Globální statické funkce pro metadata](../metadata/metadata-global-static-functions.md)
