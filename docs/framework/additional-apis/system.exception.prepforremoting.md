---
title: Exception. PrepForRemoting – metoda (System)
description: Přečtěte si metodu Exception. PrepForRemoting v rozhraní .NET. Metoda přidá do zprávy trasování zásobníku na straně serveru před tím, než je výjimka znovu vyvolána v klientovi.
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105263"
---
# <a name="exceptionprepforremoting-method"></a>Exception.PrepForRemoting – metoda

Zachovává trasování zásobníku na straně serveru tím, že ho připojí ke zprávě předtím, než se výjimka znovu vyvolá na webu klientského volání.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Návraty

<xref:System.Exception>  
Tato <xref:System.Exception> instance.

## <a name="remarks"></a>Poznámky

> [!WARNING]
> `Exception.PrepForRemoting`Metoda je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této metody v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System>

**Assembly:** mscorlib.dll (v mscorlib.dll)

**Verze .NET Framework:** K dispozici od verze 1,0.
