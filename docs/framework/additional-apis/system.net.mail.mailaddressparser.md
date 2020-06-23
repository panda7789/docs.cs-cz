---
title: MailAddressParser – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990333"
---
# <a name="mailaddressparser-class"></a>MailAddressParser – třída

Analyzuje e-mailové adresy popsané v dokumentu RFC 2822. Tuto třídu nelze zdědit.

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> Tato třída je interní a není určena pro použití přímo v kódu.
>
> Společnost Microsoft v žádné situaci nepodporuje použití této třídy v produkční aplikaci.

## <a name="parseaddress-method"></a>Metoda ParseAddress

Analyzuje jednu e-mailovou adresu ze zadaného řetězce.

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a>Parametry

`data` <xref:System.String>

Řetězec, který obsahuje e-mailovou adresu, která má být analyzována.

### <a name="return-value"></a>Vrácená hodnota

<xref:System.Net.Mail.MailAddress>

Platná e-mailová adresa

### <a name="exceptions"></a>Výjimky

<xref:System.FormatException?displayProperty=nameWithType>

E-mailová adresa je neplatná.

## <a name="requirements"></a>Požadavky

**Obor názvů:**<xref:System.Net>

**Sestavení:** Systém (v System.dll)
