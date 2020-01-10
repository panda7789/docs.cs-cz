---
title: HttpWebRequest. _CoreResponse – pole
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
ms.openlocfilehash: d16936f6984e73a886f5f48e05b53501ced63c1b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740445"
---
# <a name="httpwebrequest_coreresponse-field"></a>HttpWebRequest.\_pole CoreResponse

`HttpWebRequest._CoreResponse` je objekt (buď [CoreResponseData](coreresponsedata.md) nebo <xref:System.Exception>), který obsahuje výsledek analýzy odpovědi HTTP.

## <a name="syntax"></a>Syntaxe
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> Toto rozhraní API není určeno k použití přímo v kódu. Místo toho byste k připojení síťového kódu měli použít <xref:System.Diagnostics.DiagnosticSource>. Viz [uživatelská příručka pro DiagnosticSource](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).
> 
> Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.

## <a name="requirements"></a>Požadavky

**Obor názvů:** <xref:System.Net>

**Sestavení:** Systém (v System. dll)

**Verze .NET Framework:** K dispozici od verze 2,0.
