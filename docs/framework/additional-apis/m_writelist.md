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
# <a name="connectionm_writelist-field"></a><span data-ttu-id="63086-102">Connection. m\_pole WriteList</span><span class="sxs-lookup"><span data-stu-id="63086-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="63086-103">`Connection.m_WriteList` je <xref:System.Collections.ArrayList> objektů <xref:System.Net.HttpWebRequest>, které jsou zařazeny do fronty, aby byly odesílány prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="63086-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="63086-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63086-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="63086-105">Pole `Connection.m_WriteList` je soukromé a není určeno pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="63086-105">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="63086-106">Společnost Microsoft v žádné situaci nepodporuje použití tohoto pole v produkční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="63086-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="63086-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63086-107">Requirements</span></span>

<span data-ttu-id="63086-108">**Obor názvů:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="63086-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="63086-109">**Sestavení:** Systém (v System. dll)</span><span class="sxs-lookup"><span data-stu-id="63086-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="63086-110">**Verze .NET Framework:** K dispozici od verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="63086-110">**.NET Framework versions:** Available since 2.0.</span></span>
