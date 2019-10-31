---
title: Connection. m_WriteList – pole
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9760e301e25bc6e69ab22b563894cb079a8d58bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120030"
---
# <a name="connectionm_writelist-field"></a>Connection. m\_pole WriteList

`Connection.m_WriteList` je <xref:System.Collections.ArrayList> objektů <xref:System.Net.HttpWebRequest>, které jsou zařazeny do fronty, aby byly odesílány prostřednictvím protokolu HTTP.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> Pole `Connection.m_WriteList` je soukromé a není určeno pro použití přímo v kódu.
> 
> Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Net>

**Sestavení:** Systém (v System. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
