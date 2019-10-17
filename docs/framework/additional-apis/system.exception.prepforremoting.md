---
title: Exception. PrepForRemoting – metoda (System)
author: mairaw
ms.author: mairaw
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 057390d64f70d3cb8eba7d4b29b94570fdca77e3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72405030"
---
# <a name="exceptionprepforremoting-method"></a>Exception. PrepForRemoting – metoda

Zachovává trasování zásobníku na straně serveru tím, že ho připojí ke zprávě předtím, než se výjimka znovu vyvolá na webu klientského volání.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Vrací

<xref:System.Exception>  
Tato instance <xref:System.Exception>.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `Exception.PrepForRemoting` je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System>

**Sestavení:** mscorlib. dll (v mscorlib. dll)

**Verze .NET Framework:** K dispozici od verze 1,0.
