---
title: InitDbgTransportManager – funkce
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
ms.openlocfilehash: e18ceb25b9c58a9710ef967cb071e3ef55beea8c
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421043"
---
# <a name="initdbgtransportmanager-function"></a>InitDbgTransportManager – funkce
Inicializuje správce přenosu pro připojení ke vzdálenému cíli pro proces a výčet za běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěch.  
  
 E_OUTOFMEMORY  
 Funkce nemohla přidělit paměť pro správce přenosu.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Další chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Knihovna:** mscordbi_macx86. dll  
  
 **Verze .NET Framework:** 3,5 SP1
