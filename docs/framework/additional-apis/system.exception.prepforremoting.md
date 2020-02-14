---
title: Exception. PrepForRemoting – metoda (System)
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: ce1c24578690a1643b7f5af0e44eaae95ed7b0a2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214888"
---
# <a name="exceptionprepforremoting-method"></a>Exception.PrepForRemoting – metoda

Zachovává trasování zásobníku na straně serveru tím, že ho připojí ke zprávě předtím, než se výjimka znovu vyvolá na webu klientského volání.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Vrací

<xref:System.Exception>  
Tato <xref:System.Exception> instance.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Metoda `Exception.PrepForRemoting` je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System>

**Sestavení:** mscorlib. dll (v mscorlib. dll)

**Verze .NET Framework:** K dispozici od verze 1,0.
