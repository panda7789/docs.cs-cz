---
title: MailAddressParser – třída (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.MailAddressParser
- System.Net.Mail.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ff83f6946539fa262ccde980052627f98c75601d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051347"
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
