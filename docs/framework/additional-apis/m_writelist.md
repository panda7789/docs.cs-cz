---
title: Connection.m_WriteList pole
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
author: guardrex
ms.author: mairaw
ms.openlocfilehash: d145f6fd21989ada49a581ebf2694dcd56d94351
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743157"
---
# <a name="connectionmwritelist-field"></a>Connection.m\_WriteList pole

`Connection.m_WriteList` je <xref:System.Collections.ArrayList> z <xref:System.Net.HttpWebRequest> objekty, které jsou zařazeny do fronty v odesílání prostřednictvím protokolu HTTP.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> `Connection.m_WriteList` Pole je privátní a nejsou určeny pro použití přímo v kódu.
> 
> Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.

## <a name="requirements"></a>Požadavky

**Namespace:** <xref:System.Net>

**Sestavení:** systému (v System.dll)

**Verze rozhraní .NET framework:** dostupné od verze 2.0.
