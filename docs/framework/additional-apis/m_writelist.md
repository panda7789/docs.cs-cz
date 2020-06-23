---
title: Connection. m_WriteList – pole
description: Získat informace o připojení. m_WriteList pole v .NET. Toto pole ArrayList obsahuje objekty HttpWebRequest, které jsou zařazeny do fronty k odeslání prostřednictvím protokolu HTTP.
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
ms.openlocfilehash: a627cb062036e3ab098c2d6e97f9a77ebfa75a33
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989597"
---
# <a name="connectionm_writelist-field"></a>Pole Connection. m \_ WriteList

`Connection.m_WriteList`je <xref:System.Collections.ArrayList> <xref:System.Net.HttpWebRequest> objekty, které jsou zařazeny do fronty k odeslání prostřednictvím protokolu HTTP.

## <a name="syntax"></a>Syntax
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> `Connection.m_WriteList`Pole je soukromé a není určeno pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
