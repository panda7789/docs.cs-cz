---
title: HttpWebRequest. _CoreResponse – pole
description: Přečtěte si o poli HttpWebRequest. _CoreResponse v .NET. Toto pole je objekt CoreResponseData nebo Exception, který obsahuje výsledek analýzy odpovědi HTTP.
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 5093ec7ed2c3b94931dcd622ae9ccdb42feffa18
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989747"
---
# <a name="httpwebrequest_coreresponse-field"></a>HttpWebRequest. \_ Pole CoreResponse

`HttpWebRequest._CoreResponse`je objekt (buď [CoreResponseData](coreresponsedata.md) nebo a <xref:System.Exception> ), který obsahuje výsledek analýzy odpovědi HTTP.

## <a name="syntax"></a>Syntax
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> Toto rozhraní API není určeno k použití přímo v kódu. Místo toho byste měli použít <xref:System.Diagnostics.DiagnosticSource> k zavěšení síťového kódu. Viz [uživatelská příručka pro DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
>
> Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
