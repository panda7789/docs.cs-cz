---
title: CoreResponseData. m_ResponseHeaders – pole
description: Porozumět poli CoreResponseData. m_ResponseHeaders v .NET. Toto pole je typ WebHeaderCollection, který obsahuje hlavičky přidružené k odpovědi serveru.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 7c7b896193cb81e9fc9e3ec28110359003a36728
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989788"
---
# <a name="coreresponsedatam_responseheaders-field"></a>CoreResponseData. m \_ ResponseHeaders hostitele – pole

`CoreResponseData.m_ResponseHeaders`je hlavičkou, která je <xref:System.Net.WebHeaderCollection> přidružená k odpovědi serveru.

## <a name="syntax"></a>Syntax
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> Toto rozhraní API není určeno k použití přímo v kódu. Místo toho byste měli použít <xref:System.Diagnostics.DiagnosticSource> k zavěšení síťového kódu. Viz [uživatelská příručka pro DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
>
> Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
