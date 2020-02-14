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
ms.openlocfilehash: 22f939d13cceac4d1c0b39e9e8fe20cdc0ab9387
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214902"
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
